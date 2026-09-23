# Composition Patterns

Composition + early returns for conditional UI, and factory entry points that
keep domain modules branch-free.

## 1. Component Composition

**Impact: HIGH**

Preference order for conditional UI:

1. **Composition + early returns** (best when possible)
2. Explicit ternary (`cond ? <A /> : null`) — never `&&` for render guards
3. `&&` — avoid; falsy values (`0`, `NaN`) can render

Use **composition + early returns** instead of layering conditional JSX in one
return. Applies to mutually exclusive states (loading, empty, data), required
params, and optional sections that would otherwise be inline ternaries.

Do not stop at “ternary instead of `&&`” when a child with an early return (or a
layout + mutually exclusive returns) keeps the parent flat — that is the
preferred shape.

### Mutually exclusive states

Compose a shared layout; each state gets its own early return.

**Incorrect (nested conditional JSX):**

```tsx
export function ShoppingList() {
	const { data, isPending } = useQuery(/* ... */)

	return (
		<Card>
			{isPending ? (
				<Skeleton />
			) : !data ? (
				<EmptyScreen />
			) : (
				<>
					{data.assignee ? <UserInfo {...data.assignee} /> : null}
					{data.content.map((item) => (
						<ShoppingItem key={item.id} {...item} />
					))}
				</>
			)}
		</Card>
	)
}
```

**Correct (layout + early returns):**

```tsx
function Layout({ children, title }: { children: ReactNode; title?: string }) {
	return (
		<Card>
			<CardHeading>{title ?? 'Welcome'}</CardHeading>
			<CardContent>{children}</CardContent>
		</Card>
	)
}

export function ShoppingList() {
	const { data, isPending } = useQuery(/* ... */)

	if (isPending) {
		return (
			<Layout>
				<Skeleton />
			</Layout>
		)
	}

	if (!data) {
		return (
			<Layout>
				<EmptyScreen />
			</Layout>
		)
	}

	return (
		<Layout title={data.title}>
			<AssigneeInfo assignee={data.assignee} />
			{data.content.map((item) => (
				<ShoppingItem key={item.id} {...item} />
			))}
		</Layout>
	)
}
```

### Optional sections — child with early return

Prefer a child component that guards visibility over an inline ternary in the
parent. Keeps the parent flat; the child can use Hooks safely (after the guard).

**Incorrect (inline ternary in parent):**

```tsx
function Panel({ isVisible }: { isVisible: boolean }) {
	return <Card>{isVisible ? <div>Visible content</div> : null}</Card>
}
```

**Correct (composed child):**

```tsx
function Panel({ isVisible }: { isVisible: boolean }) {
	return (
		<Card>
			<VisibleContent isVisible={isVisible} />
		</Card>
	)
}

function VisibleContent({ isVisible }: { isVisible: boolean }) {
	if (!isVisible) {
		return null
	}

	return <div>Visible content</div>
}
```

### Required params via composition

Guard missing/invalid params in the page or parent; render a child that requires
the narrowed type.

```tsx
function UserDetailsPage() {
	const { userId } = useParams()

	if (!userId) {
		return <MissingUserId />
	}

	return <UserDetails userId={userId} />
}

function UserDetails({ userId }: { userId: string }) {
	const { data, isPending } = useUserDetailsQuery({ userId })
	// ...
}
```

### Hooks

Run all Hooks at the top level, then early-return. Never call Hooks inside
conditions, ternaries, or after a guard that skips them.

## 2. Factory Entry Points

**Impact: HIGH**

If statements belong at the entry point, not scattered throughout services.

**Incorrect (conditionals scattered in service):**

```typescript
class ContentService {
	async get(slug: string, kind: string, locale?: string) {
		if (kind === 'blog') {
			/* ... */
		} else if (kind === 'wiki') {
			/* ... */
		}
	}
}
```

**Correct (entry point chooses specialized module):**

```typescript
import { blog } from '~/features/blog/api'
import { wiki } from '~/features/wiki/api'
```

Push conditionals up to routes/factories. Keep domain modules single-purpose.
Watch for if-statement accumulation during review.
