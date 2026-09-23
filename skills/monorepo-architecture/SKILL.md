---
name: nerdfish-monorepo-architecture
description: >
  Monorepo architecture patterns: organize app code by domain (vertical slices)
  and keep an acyclic package dependency graph. Use when structuring features,
  placing code in packages vs app features, reviewing imports, or fixing
  circular dependencies in a pnpm/Turbo monorepo.
license: MIT
metadata:
  author: nerdfish
  version: '1.0.0'
---

# Monorepo Architecture

Organize by domain, not by technical layer. Keep the dependency graph acyclic.

## When to Apply

Reference these guidelines when:

- Deciding where new code lives (package vs feature vs route)
- Reviewing cross-package / cross-feature imports
- Refactoring layered folders into slices
- Hunting circular dependencies

## Rule Categories by Priority

| Priority | Category             | Impact   | Prefix           |
| -------- | -------------------- | -------- | ---------------- |
| 1        | Vertical slices      | CRITICAL | `architecture-`  |
| 2        | Acyclic dependencies | CRITICAL | `architecture-`  |

## Quick Reference

### 1. Vertical slices (CRITICAL)

- `architecture-vertical-slices` - Domain folders under `features/`; routes
  compose blocks; no `*-page` composers in features

### 2. Acyclic dependencies (CRITICAL)

- `architecture-circular-dependencies` - lib → packages → features → app; never
  import upward

## How to Use

```
rules/architecture-vertical-slices.md
rules/architecture-circular-dependencies.md
```

## Full Compiled Document

For the complete guide with all rules expanded: `AGENTS.md`
