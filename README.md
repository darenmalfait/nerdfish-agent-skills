# Nerdfish Agent Skills

A collection of skills for AI coding agents. Skills are packaged instructions
and scripts that extend agent capabilities.

Skills follow the [Agent Skills](https://agentskills.io/) format.

Includes the full set from
[vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills), plus
nerdfish-authored skills.

## Available Skills

### From Vercel (vendored)

| Skill | Use when |
| ----- | -------- |
| `vercel-optimize` | Cost/perf/reliability audits on a deployed Vercel project |
| `react-best-practices` | React/Next.js performance (official Vercel rules) |
| `web-design-guidelines` | UI / a11y / UX audit against Web Interface Guidelines |
| `writing-guidelines` | Docs/prose against the Vercel writing handbook |
| `react-native-skills` | React Native / Expo performance and architecture |
| `react-view-transitions` | View Transition API + Next.js `transitionTypes` |
| `composition-patterns` | Compound components, lift state, avoid boolean props |
| `deploy-to-vercel` | Claimable deploy from a conversation |
| `vercel-cli-with-tokens` | Vercel CLI auth/token workflows |

### Nerdfish

| Skill | Use when |
| ----- | -------- |
| `react-best-practises` | Vercel react-best-practices **fork** + nerdfish extensions (composition early-return, no bare `useEffect`) |
| `composition-early-returns` | Nested conditional JSX → layout + early returns; factory entry points |
| `code-quality` | Clarity over cleverness, comments, thorough review |
| `playwright-bdd` | `User Story` → `Given` → `When`; accessible queries |
| `pr-discipline` | Never push/PR/commit unless asked; small draft stacks |
| `monorepo-architecture` | Vertical slices + acyclic package graph |
| `specification-website` | The Website Specification (MCP / Markdown audits) |

## Installation

Private repo — use credentials that can read it:

```bash
npx skills add darenmalfait/nerdfish-agent-skills
```

Single skill:

```bash
npx skills add darenmalfait/nerdfish-agent-skills --skill composition-early-returns
```

Manual:

```bash
cp -r skills/composition-early-returns ~/.cursor/skills/
```

## Which React performance skill?

- Prefer **`react-best-practises`** (nerdfish) when you want the Vercel rules
  plus local extensions.
- Use **`react-best-practices`** (Vercel) for a pure upstream copy.

## Discovery index

```bash
npm ci --ignore-scripts
node scripts/build-discovery-index.mjs https://example.com/skills
```

## Skill Structure

Each skill contains:

- `SKILL.md` — instructions for the agent
- `rules/` — progressive-disclosure rule files (optional)
- `AGENTS.md` — full compiled guide (optional)
- `scripts/` — helper scripts (optional)

## Upstream

Vercel skills are copied from
[vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) (MIT).
Re-sync periodically; do not invent local forks of those directories unless you
intend to diverge (like `react-best-practises`).

## License

MIT
