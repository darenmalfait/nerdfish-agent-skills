# Nerdfish Agent Skills

A collection of skills for AI coding agents. Skills are packaged instructions
and scripts that extend agent capabilities.

Skills follow the [Agent Skills](https://agentskills.io/) format.

Includes the full set from
[vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills), plus
nerdfish-authored skills that use the **same package layout**.

## Skill package layout (rule-based skills)

Matches upstream Vercel multi-rule skills:

```
skills/{skill-name}/
  SKILL.md              # Agent entry (name: vercel-* | nerdfish-*)
  AGENTS.md             # Full compiled guide
  README.md             # Human-oriented structure docs
  metadata.json         # version, organization, abstract, references
  rules/
    _sections.md        # Section order + impact
    _template.md        # New-rule template
    {prefix}-{name}.md  # Individual rules
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

### Nerdfish

| Dir | Skill `name` |
| --- | ------------ |
| `react-best-practises` | `nerdfish-react-best-practises` |
| `composition-early-returns` | `nerdfish-composition-early-returns` |
| `code-quality` | `nerdfish-code-quality` |
| `playwright-bdd` | `nerdfish-playwright-bdd` |
| `pr-discipline` | `nerdfish-pr-discipline` |
| `monorepo-architecture` | `nerdfish-monorepo-architecture` |
| `specification-website` | `specification-website` |

## Installation

Private repo — credentials must be able to read it:

```bash
npx skills add darenmalfait/nerdfish-agent-skills
```

Single skill:

```bash
npx skills add darenmalfait/nerdfish-agent-skills --skill composition-early-returns
```

## Discovery index

```bash
npm ci --ignore-scripts
node scripts/build-discovery-index.mjs https://example.com/skills
```

## Upstream

Vercel skills are copied from
[vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) (MIT).
Nerdfish divergences get their own skill dirs/names — do not silently fork
vendored directories.

## License

MIT
