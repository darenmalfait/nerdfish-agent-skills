# Code Quality

Structured rules for clarity, comments, and review rigor.

## Structure

- `rules/` - Individual rule files (one per rule)
  - `_sections.md` - Section metadata
  - `_template.md` - Template for creating new rules
  - `area-description.md` - Individual rule files
- `metadata.json` - Document metadata
- **`AGENTS.md`** - Compiled output
- **`SKILL.md`** - Agent skill entry point

## Rules

### Code Quality (HIGH)

- `quality-simplicity.md` - Clarity over cleverness
- `quality-code-comments.md` - Comments explain why, not what
- `quality-thorough-code-review.md` - Address all nits before merge

## Creating a New Rule

1. Copy `rules/_template.md` to `rules/quality-description.md`
2. Fill in frontmatter and content
3. Update `_sections.md`, `SKILL.md`, and `AGENTS.md`
