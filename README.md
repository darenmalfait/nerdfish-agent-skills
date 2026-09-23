# Nerdfish Agent Skills

A collection of skills for AI coding agents. Skills are packaged instructions
and scripts that extend agent capabilities.

Skills follow the [Agent Skills](https://agentskills.io/) format.

**Model:** skills originally from [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills),
renamed to `nerdfish-*` where generic; Vercel-specific skills keep `vercel-*` / `deploy-to-vercel`. Nerdfish overlays add non-duplicated rules.

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

### Core (vendored from Vercel, renamed)

| Dir | Skill `name` |
| --- | ------------ |
| `vercel-optimize` | `vercel-optimize` |
| `react-best-practices` | `nerdfish-react-best-practices` |
| `web-design-guidelines` | `web-design-guidelines` |
| `writing-guidelines` | `writing-guidelines` |
| `react-native-skills` | `nerdfish-react-native-skills` |
| `react-view-transitions` | `nerdfish-react-view-transitions` |
| `composition-patterns` | `nerdfish-composition-patterns` |
| `deploy-to-vercel` | `deploy-to-vercel` |
| `vercel-cli-with-tokens` | `vercel-cli-with-tokens` |

### Nerdfish (overlay only)

| Dir | Skill `name` |
| --- | ------------ |
| `code-quality` | `nerdfish-code-quality` |
| `bdd-testing` | `nerdfish-bdd-testing` |
| `pr-discipline` | `nerdfish-pr-discipline` |
| `monorepo-architecture` | `nerdfish-monorepo-architecture` |
| `specification-website` | `specification-website` |

Composition / early-return / ternary-vs-`&&` live in
`composition-patterns` + `react-best-practices` — not duplicated in overlays.

## Installation

```bash
npx skills add darenmalfait/nerdfish-agent-skills
```

Single skill:

```bash
npx skills add darenmalfait/nerdfish-agent-skills --skill monorepo-architecture
```

Listed on [skills.sh](https://skills.sh) after discovery releases publish (see
`.github/workflows/agent-skills-discovery.yml`).

## Discovery index

On every push to `main` that touches `skills/**`, CI builds the Agent Skills
discovery index and publishes a GitHub Release with artifacts.

Locally:

```bash
npm ci --ignore-scripts
node scripts/build-discovery-index.mjs https://example.com/skills
```

## Upstream

Upstream content stays in the renamed core skills. Overlay skills only add rules
that are not already covered there.

## License

MIT
