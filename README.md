# Nerdfish Agent Skills

A collection of skills for AI coding agents. Skills are packaged instructions
and scripts that extend agent capabilities.

Skills follow the [Agent Skills](https://agentskills.io/) format.

**Model:** full [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills)
clone + nerdfish overlays only (no forks that duplicate upstream).

## Skill package layout (rule-based skills)

```
skills/{skill-name}/
  SKILL.md
  AGENTS.md
  README.md
  metadata.json
  rules/
    _sections.md
    _template.md
    {prefix}-{name}.md
```

Thin skills (`web-design-guidelines`, `writing-guidelines`,
`specification-website`) are `SKILL.md`-only — same as upstream.

## Available Skills

### From Vercel (vendored)

| Dir | Skill `name` |
| --- | ------------ |
| `vercel-optimize` | `vercel-optimize` |
| `react-best-practices` | `vercel-react-best-practices` |
| `web-design-guidelines` | `web-design-guidelines` |
| `writing-guidelines` | `writing-guidelines` |
| `react-native-skills` | `vercel-react-native-skills` |
| `react-view-transitions` | `vercel-react-view-transitions` |
| `composition-patterns` | `vercel-composition-patterns` |
| `deploy-to-vercel` | `deploy-to-vercel` |
| `vercel-cli-with-tokens` | `vercel-cli-with-tokens` |

### Nerdfish (overlay only)

| Dir | Skill `name` |
| --- | ------------ |
| `code-quality` | `nerdfish-code-quality` |
| `playwright-bdd` | `nerdfish-playwright-bdd` |
| `pr-discipline` | `nerdfish-pr-discipline` |
| `monorepo-architecture` | `nerdfish-monorepo-architecture` |
| `specification-website` | `specification-website` |

Composition / early-return / ternary-vs-`&&` live in upstream
`composition-patterns` + `react-best-practices` — not duplicated here.

## Installation

```bash
npx skills add darenmalfait/nerdfish-agent-skills
```

Single skill:

```bash
npx skills add darenmalfait/nerdfish-agent-skills --skill monorepo-architecture
```

## Discovery index

```bash
npm ci --ignore-scripts
node scripts/build-discovery-index.mjs https://example.com/skills
```

## Upstream

Do not silently fork vendored Vercel skill dirs. Overlay = new skill name + only
rules that are not already upstream.

## License

MIT
