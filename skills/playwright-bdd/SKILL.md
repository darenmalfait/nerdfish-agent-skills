---
name: playwright-bdd
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

- Writing new Playwright specs
- Reviewing e2e tests
- Designing page objects / fixtures

## Quick Reference

| Rule                      | File                                   |
| ------------------------- | -------------------------------------- |
| BDD structure             | `rules/testing-bdd-structure.md`       |
| Accessible test queries   | `rules/testing-accessible-queries.md`  |

## How to Use

Read the rule files under `rules/` for incorrect/correct examples.
