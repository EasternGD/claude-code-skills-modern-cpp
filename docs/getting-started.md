# Getting Started

## Prerequisites

- CMake >= 3.25
- A C++23-capable compiler:
  - Clang >= 16
  - GCC >= 13
  - MSVC 19.34+ (Visual Studio 2022 17.4+)
- Claude Code >= 1.0

## Installation

Clone this repo and copy the skills you need into your project's `.claude/skills/` directory:

```bash
git clone https://github.com/yourname/claude-code-skills-modern-cpp
cp claude-code-skills-modern-cpp/skills/cmake.md your-project/.claude/skills/
```

Or install globally so all your projects can use them:

```bash
cp claude-code-skills-modern-cpp/skills/*.md ~/.claude/skills/
```

## Quick Start

Once installed, invoke a skill directly in Claude Code:

```
/cmake
/sanitizers
/concepts
```

Or reference it inline:

```
set up a new CMake project using the cmake skill
```

## Project Layout

```
your-project/
├── .claude/
│   └── skills/
│       ├── cmake.md
│       ├── concepts.md
│       └── sanitizers.md
├── CMakeLists.txt
├── include/
├── src/
└── tests/
```

See [preview.png](preview.png) for a screenshot of Claude Code using these skills.
