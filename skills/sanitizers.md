---
name: sanitizers
description: Enable and use AddressSanitizer, UBSan, and ThreadSanitizer in CMake builds
---

Add sanitizer support to a CMake project.

## CMake Integration

```cmake
option(ENABLE_ASAN  "Enable AddressSanitizer"  OFF)
option(ENABLE_UBSAN "Enable UndefinedBehaviorSanitizer" OFF)
option(ENABLE_TSAN  "Enable ThreadSanitizer"   OFF)

function(target_enable_sanitizers target)
  set(san_flags "")
  if(ENABLE_ASAN)
    list(APPEND san_flags -fsanitize=address -fno-omit-frame-pointer)
  endif()
  if(ENABLE_UBSAN)
    list(APPEND san_flags -fsanitize=undefined)
  endif()
  if(ENABLE_TSAN)
    list(APPEND san_flags -fsanitize=thread)
  endif()
  if(san_flags)
    target_compile_options(${target} PRIVATE ${san_flags})
    target_link_options(${target} PRIVATE ${san_flags})
  endif()
endfunction()
```

## Usage

```bash
cmake -B build -DENABLE_ASAN=ON -DENABLE_UBSAN=ON
cmake --build build
./build/my_app
```

## ASAN_OPTIONS

```bash
export ASAN_OPTIONS=detect_leaks=1:abort_on_error=1:print_stats=1
export UBSAN_OPTIONS=print_stacktrace=1:halt_on_error=1
```

## Notes

- ASAN and TSAN are mutually exclusive — do not combine
- Use `Debug` build type with `-O1` for readable stack traces
- On macOS, use `DYLD_INSERT_LIBRARIES` if preloading is needed
