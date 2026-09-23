# Nerdfish Agent Skills

A collection of skills for AI coding agents. Skills are packaged instructions
that extend agent capabilities.

Skills follow the [Agent Skills](https://agentskills.io/) format.

Inspired by [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills).

## Available Skills

### react-best-practises

React and Next.js performance optimization guidelines. ~47 rules across 8
categories, prioritized by impact. Includes nerdfish extensions (composition
early returns, no bare `useEffect`).

**Use when:** writing/reviewing React or Next.js code, data fetching, bundle
size, or performance work.

### composition-patterns

Composition + early returns for conditional UI, and factory patterns that push
conditionals to entry points.

**Use when:** refactoring nested conditional JSX, boolean prop sprawl, or
services littered with `kind`/`type` switches.

### code-quality

Clarity over cleverness, comment guidelines (why not what), and thorough code
review standards.

**Use when:** reviewing PRs, writing comments, or simplifying clever code.

### playwright-bdd

Playwright BDD structure (`User Story` → `Given` → `When`) and accessible
query preferences (`getByRole` / `getByLabel` over `testId` / CSS).

**Use when:** writing or reviewing Playwright specs and page objects.

### pr-discipline

Never push, open PRs, or commit unless asked. Prefer small draft stacked PRs.

**Use when:** branching, committing, stacking, or opening pull requests.

### web-design-guidelines

Review UI against Vercel Web Interface Guidelines (fetched live from upstream).

**Use when:** "review my UI", accessibility, design/UX audit.

## Installation

Private repo — use a GitHub token / SSH that can read it:

```bash
npx skills add darenmalfait/nerdfish-agent-skills
```

Single skill:

```bash
npx skills add darenmalfait/nerdfish-agent-skills --skill composition-patterns
```

Manual:

```bash
cp -r skills/composition-patterns ~/.cursor/skills/
# or ~/.claude/skills/
```

## Skill Structure

Each skill contains:

- `SKILL.md` — instructions for the agent
- `rules/` — progressive-disclosure rule files (optional)
- `AGENTS.md` — full compiled guide (optional)
- `scripts/` — helper scripts (optional)

## License

MIT
