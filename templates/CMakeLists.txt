cmake_minimum_required(VERSION 3.25)
project(myproject VERSION 0.1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# ── Options ────────────────────────────────────────────────────────────────
option(ENABLE_ASAN  "Enable AddressSanitizer"          OFF)
option(ENABLE_UBSAN "Enable UndefinedBehaviorSanitizer" OFF)
option(BUILD_TESTS  "Build tests"                       ON)

# ── Main target ────────────────────────────────────────────────────────────
add_library(${PROJECT_NAME} STATIC
  src/foo.cpp
)

target_include_directories(${PROJECT_NAME}
  PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
)

target_compile_options(${PROJECT_NAME} PRIVATE
  $<$<CXX_COMPILER_ID:MSVC>:/W4>
  $<$<NOT:$<CXX_COMPILER_ID:MSVC>>:-Wall -Wextra -Wpedantic>
)

# ── Sanitizers ─────────────────────────────────────────────────────────────
set(san_flags "")
if(ENABLE_ASAN)
  list(APPEND san_flags -fsanitize=address -fno-omit-frame-pointer)
endif()
if(ENABLE_UBSAN)
  list(APPEND san_flags -fsanitize=undefined)
endif()
if(san_flags)
  target_compile_options(${PROJECT_NAME} PRIVATE ${san_flags})
  target_link_options(${PROJECT_NAME} PRIVATE ${san_flags})
endif()

# ── Tests ──────────────────────────────────────────────────────────────────
if(BUILD_TESTS)
  enable_testing()
  add_subdirectory(tests)
endif()
