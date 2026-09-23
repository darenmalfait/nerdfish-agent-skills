# Composition Early Returns

Structured rules for composition + early returns and factory entry points.
Complements Vercel's `composition-patterns` skill.

## Structure

- `rules/` - Individual rule files (one per rule)
  - `_sections.md` - Section metadata (titles, impacts, descriptions)
  - `_template.md` - Template for creating new rules
  - `area-description.md` - Individual rule files
- `metadata.json` - Document metadata (version, organization, abstract)
- **`AGENTS.md`** - Compiled output
- **`SKILL.md`** - Agent skill entry point

## Rules

### Conditional UI (HIGH)

- `rendering-composition-early-return.md` - Layout + early returns; ternary over
  `&&`; child guards for optional sections

### Entry-point factories (HIGH)

- `patterns-factory-entry-points.md` - Push conditionals to routes/factories

## Creating a New Rule

1. Copy `rules/_template.md` to `rules/area-description.md`
2. Choose the appropriate area prefix (`rendering-` or `patterns-`)
3. Fill in the frontmatter and content
4. Update `_sections.md` and `SKILL.md` quick reference if needed
5. Expand into `AGENTS.md`

## Impact Levels

- `CRITICAL` - Foundational patterns
- `HIGH` - Significant maintainability improvements
- `MEDIUM` - Good practices for cleaner code
