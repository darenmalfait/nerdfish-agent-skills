# Monorepo Architecture

Structured rules for vertical slices and acyclic package dependencies.

## Structure

- `rules/` - Individual rule files
  - `_sections.md` - Section metadata
  - `_template.md` - Template for creating new rules
- `metadata.json` - Document metadata
- **`AGENTS.md`** - Compiled output
- **`SKILL.md`** - Agent skill entry point

## Rules

### Vertical slices (CRITICAL)

- `architecture-vertical-slices.md` - Domain folders; routes compose blocks

### Acyclic dependencies (CRITICAL)

- `architecture-circular-dependencies.md` - Never import upward

## Creating a New Rule

1. Copy `rules/_template.md` to `rules/architecture-description.md`
2. Fill in frontmatter and content
3. Update `_sections.md`, `SKILL.md`, and `AGENTS.md`
