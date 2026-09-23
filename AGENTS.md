# AGENTS.md

Guidance for AI coding agents working in this repository.

## Repository Overview

A collection of skills for AI coding agents. Skills are packaged instructions
that extend agent capabilities. Format follows
[Agent Skills](https://agentskills.io/).

Inspired by [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills).

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

# {Skill Title}

{Brief description}

## When to Apply

- Trigger scenarios

## How to Use

Read rule files under `rules/` as needed. Prefer progressive disclosure —
keep SKILL.md under 500 lines.
```

### Conventions

- Skill directory: `kebab-case`
- Rule files: `{prefix}-{name}.md` with YAML frontmatter (`title`, `impact`,
  `tags`)
- Prefer incorrect/correct code examples over prose
- Keep skills portable — no repo-specific paths unless the skill is about a
  shared pattern that generalizes cleanly

## Installation (consumers)

Private repo — clone or add with a token:

```bash
npx skills add darenmalfait/nerdfish-agent-skills --skill composition-patterns
```

Or copy a skill into a project:

```bash
cp -r skills/composition-patterns /path/to/project/.cursor/skills/
# or ~/.claude/skills/
```
