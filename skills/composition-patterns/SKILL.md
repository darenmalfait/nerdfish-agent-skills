---
name: composition-patterns
description: >
  React composition patterns that scale: early returns over nested conditional
  JSX, composed children for optional UI, and factory entry points that keep
  services branch-free. Use when refactoring boolean props, nested ternaries,
  loading/empty/data trees, or kind/type switches in services.
license: MIT
metadata:
  author: nerdfish
  version: '1.0.0'
---

# Composition Patterns

Prefer composition + early returns over nested conditional JSX. Push
conditionals to routes and factories so domain modules stay branch-free.

## When to Apply

- Nested `isPending ? … : !data ? … : …` trees
- Optional sections rendered with inline ternaries in parents
- Services switching on `kind` / `type` / product flags
- Reviewing component architecture for boolean-prop sprawl

## Rule Categories by Priority

| Priority | Category               | Impact | Prefix          |
| -------- | ---------------------- | ------ | --------------- |
| 1        | Conditional UI         | HIGH   | `rendering-`    |
| 2        | Entry-point factories  | HIGH   | `patterns-`     |

## Quick Reference

### 1. Conditional UI (HIGH)

- `rendering-composition-early-return` — layout + early returns; ternary over
  `&&`; child guards for optional sections

### 2. Entry-point factories (HIGH)

- `patterns-factory-entry-points` — push conditionals to routes/factories; keep
  services single-purpose

## How to Use

Read individual rule files:

```
rules/rendering-composition-early-return.md
rules/patterns-factory-entry-points.md
```

## Full Compiled Document

For the complete guide with all rules expanded: `AGENTS.md`
