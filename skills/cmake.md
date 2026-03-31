---
name: cmake
description: Modern CMake project setup, targets, presets, and best practices for C++17/20/23 projects
---

Set up a modern CMake project with proper target-based design.

## New Project

```cmake
cmake_minimum_required(VERSION 3.25)
project($ARGUMENTS VERSION 0.1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_library(${PROJECT_NAME} STATIC)

target_sources(${PROJECT_NAME}
  PRIVATE
    src/foo.cpp
  PUBLIC
    FILE_SET HEADERS
    BASE_DIRS include
    FILES include/${PROJECT_NAME}/foo.hpp
)

target_compile_options(${PROJECT_NAME} PRIVATE
  $<$<CXX_COMPILER_ID:MSVC>:/W4 /WX>
  $<$<NOT:$<CXX_COMPILER_ID:MSVC>>:-Wall -Wextra -Wpedantic -Werror>
)
```

## FetchContent Dependency

```cmake
include(FetchContent)
FetchContent_Declare(
  fmt
  GIT_REPOSITORY https://github.com/fmtlib/fmt.git
  GIT_TAG        10.2.1
)
FetchContent_MakeAvailable(fmt)

target_link_libraries(${PROJECT_NAME} PRIVATE fmt::fmt)
```

## CMakePresets.json

```json
{
  "version": 6,
  "configurePresets": [
    {
      "name": "debug",
      "generator": "Ninja",
      "binaryDir": "${sourceDir}/build/debug",
      "cacheVariables": {
        "CMAKE_BUILD_TYPE": "Debug",
        "CMAKE_CXX_COMPILER": "clang++"
      }
    },
    {
      "name": "release",
      "inherits": "debug",
      "binaryDir": "${sourceDir}/build/release",
      "cacheVariables": { "CMAKE_BUILD_TYPE": "Release" }
    }
  ]
}
```

## Tips

- Never use `include_directories()` — use `target_include_directories()` instead
- Prefer `target_link_libraries()` with `PRIVATE`/`PUBLIC`/`INTERFACE`
- Use `CMAKE_EXPORT_COMPILE_COMMANDS` for clangd/clang-tidy integration
