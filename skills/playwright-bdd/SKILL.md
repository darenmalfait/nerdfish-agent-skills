---
name: nerdfish-playwright-bdd
description: >
  Playwright BDD structure (User Story → Given → When) and accessible query
  preferences (role/label over testId/CSS). Use when writing or reviewing
  Playwright specs, page objects, fixtures, or e2e test plans.
license: MIT
metadata:
  author: nerdfish
  version: '1.0.0'
---

# Playwright BDD

Specs tell a story. Selectors go in page objects. Query the UI the way a user
(or assistive tech) would.

## When to Apply

Reference these guidelines when:

- Writing new Playwright specs
- Reviewing e2e tests
- Designing page objects / fixtures

## Rule Categories by Priority

| Priority | Category | Impact | Prefix     |
| -------- | -------- | ------ | ---------- |
| 1        | Testing  | HIGH   | `testing-` |

## Quick Reference

### 1. Testing (HIGH)

- `testing-bdd-structure` - User Story → Given → When nesting
- `testing-accessible-queries` - Prefer role/label over testId/CSS

## How to Use

Read individual rule files for detailed explanations and code examples:

```
rules/testing-bdd-structure.md
rules/testing-accessible-queries.md
```

## Full Compiled Document

For the complete guide with all rules expanded: `AGENTS.md`
