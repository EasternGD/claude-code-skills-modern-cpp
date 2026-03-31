# Contributing

Contributions welcome. Please follow the guidelines below.

## Adding a New Skill

1. Create `skills/{name}.md` with the following frontmatter:

```markdown
---
name: skill-name
description: One-line description used for skill matching
---
```

2. Structure the content with:
   - A brief intro (1–2 sentences)
   - Code examples with realistic snippets
   - A "Tips" or "Notes" section for gotchas

3. Add an entry to `docs/skills-reference.md`

## Skill Writing Guidelines

- **Be terse.** Claude Code skills are read by an LLM, not a human. Prefer dense, accurate code over prose.
- **Use real examples.** Avoid toy `foo`/`bar` code where a realistic example fits in the same space.
- **Include the include.** Always show which headers are needed.
- **C++23 by default**, but note when a feature requires a specific standard.

## Template Files

Templates under `templates/` should be immediately usable — copy-paste into a project and it should work. Keep them minimal but complete.

## Pull Requests

- One skill or template per PR
- Test any CMake snippets with at least Clang 16 and GCC 13
- No trailing whitespace, Unix line endings
