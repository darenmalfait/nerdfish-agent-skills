# AGENTS.md

Guidance for AI coding agents working in this repository.

## Repository Overview

A collection of skills for AI coding agents. Core skills are adapted from
[vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) and
renamed to `nerdfish-*`, plus nerdfish-authored overlays.

Format: [Agent Skills](https://agentskills.io/).

## Creating a New Skill

### Directory Structure

```
skills/
  {skill-name}/           # kebab-case
    SKILL.md              # Required
    AGENTS.md             # Optional: full compiled guide
    rules/                # Optional: progressive-disclosure rule files
    scripts/              # Optional
    references/           # Optional
```

### Naming

- **Skill directory**: `kebab-case`
- **SKILL.md `name:`**: `nerdfish-*` prefix
- Prefer incorrect/correct code examples over long prose
- Keep skills portable — no single-repo paths unless generalized as examples
- Core content from upstream keeps the same directory layout; do not fork a
  second copy of the same rules. Overlays (`code-quality`,
  `monorepo-architecture`, …) only add non-duplicated rules.

### SKILL.md Format

```markdown
---
name: {skill-name}
description: >
  What the skill does and when to use it. Include trigger phrases.
license: MIT
metadata:
  author: nerdfish
  version: '1.0.0'
---
```

Keep `SKILL.md` under 500 lines; put detail in `rules/` / `references/`.

## Installation (consumers)

```bash
npx skills add darenmalfait/nerdfish-agent-skills --skill {skill-name}
```

## Syncing Vercel upstream

```bash
git clone --depth 1 https://github.com/vercel-labs/agent-skills.git /tmp/vas
# copy skills you want to refresh into skills/{name}
# keep nerdfish-only skills untouched
```
