# Skills Reference

## cmake

Sets up a modern CMake project with proper target-based design, presets, and dependency management via FetchContent or Conan.

**Triggers on:** "new cmake project", "add dependency", "cmake preset", "FetchContent"

**Example prompts:**
- `set up a new C++23 CMake project`
- `add fmt as a FetchContent dependency`
- `create CMakePresets.json for debug and release`

---

## sanitizers

Adds AddressSanitizer, UBSan, and ThreadSanitizer support to a CMake project with proper flags and options.

**Triggers on:** "sanitizer", "asan", "ubsan", "memory error", "undefined behavior"

**Example prompts:**
- `enable AddressSanitizer in this CMake project`
- `set up sanitizer options with CMake`

---

## concepts

Defines, applies, and composes C++20 Concepts and constraints.

**Triggers on:** "concept", "constraint", "requires clause", "template constraint"

**Example prompts:**
- `write a concept for a numeric type`
- `constrain this template with concepts`
- `compose two concepts`

---

## ranges

Applies C++20 Ranges and views for composable, lazy sequence transformations.

**Triggers on:** "ranges", "views", "filter transform", "lazy sequence"

**Example prompts:**
- `filter and transform this vector with ranges`
- `collect range view into a vector`
- `sort with a projection`

---

## coroutines *(coming soon)*

C++20 coroutines: generators, async tasks, and coroutine handles.

## modules *(coming soon)*

C++20 module units, interface files, and CMake integration.

## formatting *(coming soon)*

`std::format` and fmtlib: format strings, custom formatters, compile-time checks.
