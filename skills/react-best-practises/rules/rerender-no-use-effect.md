---
title: No Bare useEffect
impact: HIGH
impactDescription: Enforced by ESLint @nerdfish/conventions/no-use-effect
tags: rerender, quality, use-effect, conventions, eslint
---

## No Bare useEffect

**Repo extension** (nerdfish) — stricter than examples elsewhere in this skill
that still show bare `useEffect`.

`@nerdfish/conventions/no-use-effect` bans direct `useEffect`. Syncing with
props/state → derived values. User work → event handlers. Data fetching →
router/framework. The rare mount-only side effect goes through `useMountEffect`
(re-exported from `@repo/lib/hooks/use-mount-effect`).

**Incorrect:**

```typescript
useEffect(() => {
	setDerived(compute(props.value))
}, [props.value])

useEffect(() => {
	const subscription = api.subscribe(id)
	return () => subscription.unsubscribe()
}, [])
```

**Correct:**

```typescript
const derived = compute(props.value)

import { useMountEffect } from '@repo/lib/hooks/use-mount-effect'

useMountEffect(() => {
	const subscription = api.subscribe(id)
	return () => subscription.unsubscribe()
})
```

Empty-deps `useEffect(..., [])` specifically should become `useMountEffect` so
mount-only intent is searchable.

When adapting other examples in this skill that call bare `useEffect`, prefer
derived state / handlers / `useMountEffect` instead.

Full local rule: `agents/rules/quality-no-use-effect.md`. Reference:
`@nerdfish/config/eslint/conventions` → `no-use-effect`,
`packages/lib/hooks/use-mount-effect.tsx`.
