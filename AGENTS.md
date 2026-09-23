# AGENTS.md

Guidance for AI coding agents working in this repository.

## Repository Overview

A collection of skills for AI coding agents. Includes the full
[vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) set
(vendored) plus nerdfish-authored skills.

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
- **SKILL.md**: always this exact filename
- Prefer incorrect/correct code examples over long prose
- Keep skills portable — no single-repo paths unless generalized as examples

### Do not silently fork Vercel skills

Vendored Vercel directories (`react-best-practices`, `composition-patterns`, etc.)
should stay close to upstream. Nerdfish divergences get their **own** skill
name (`react-best-practises`, `composition-early-returns`).

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
