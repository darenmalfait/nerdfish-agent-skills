---
name: pr-discipline
description: >
  Git and PR discipline for agents: never push, open PRs, or commit unless the
  user explicitly asks. Prefer small draft stacked PRs with conventional commit
  titles. Use when branching, committing, stacking, or opening pull requests.
license: MIT
metadata:
  author: nerdfish
  version: '1.0.0'
---

# PR Discipline

Agents stop at local work unless the user asks otherwise. Prefer small, draft,
stackable PRs.

## When to Apply

- Any git push / PR / commit decision
- Splitting large work into reviewable layers
- Writing PR titles and bodies

## Quick Reference

| Rule                    | File                              |
| ----------------------- | --------------------------------- |
| Never push/PR/commit    | `rules/git-pr-discipline.md`      |
| Small draft stacked PRs | `rules/quality-pr-creation.md`    |

## How to Use

Read the rule files under `rules/`. Treat `git-pr-discipline` as always-on
unless the consuming project overrides it.
