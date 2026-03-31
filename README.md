# Claude Code Skills: Modern C++

A collection of Claude Code skills and templates for Modern C++ (C++17/20/23) development.

## Skills

| Skill | Description |
|-------|-------------|
| `cmake` | CMake project setup, targets, and best practices |
| `sanitizers` | AddressSanitizer, UBSan, ThreadSanitizer usage |
| `concepts` | C++20 Concepts and constraints |
| `ranges` | C++20 Ranges and views |
| `coroutines` | C++20 Coroutines basics |
| `modules` | C++20 Modules setup |
| `formatting` | std::format and fmtlib |

## Usage

Copy the `.md` files under `skills/` into your project's `.claude/skills/` directory, or reference them globally from `~/.claude/skills/`.

## Templates

Under `templates/` you'll find ready-to-use config files:

- `CMakeLists.txt` — modern CMake starter
- `.clang-format` — opinionated clang-format config
- `.clang-tidy` — clang-tidy checks
- `msvc.ini` — MSVC compiler response file defaults

## Requirements

- CMake >= 3.25
- Clang >= 16 or GCC >= 13 or MSVC 19.34+
- Claude Code >= 1.0
