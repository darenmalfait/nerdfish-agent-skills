# Playwright BDD

Specs tell a story. Selectors go in page objects. Query the UI the way a user
(or assistive tech) would.

## 1. Playwright BDD Structure

**Impact: HIGH**

1. Top-level `describe` starts with `User Story:`
2. Nested blocks start with `Given ` or `When `
3. User stories mention **user** (unless permission/role-specific)
4. `When` actions live in `beforeEach`
5. Assertions only in `test` / `it`
6. No `"and"` in titles — split instead
7. One coherent action per When

**Incorrect:**

```typescript
test.describe('Contact form', () => {
	test('opens and submits', async ({ contactPage }) => {
		await contactPage.goto()
		await contactPage.openForm()
		await contactPage.form.submit()
		await expect(contactPage.getSuccessAlert()).toBeVisible()
	})
})
```

**Correct:**

```typescript
test.describe('User Story: The user wants to submit the contact form', () => {
	test.describe('Given the user is on the contact page', () => {
		test.beforeEach(async ({ contactPage }) => {
			await contactPage.goto()
		})

		test.describe('When the user opens the contact form', () => {
			test.beforeEach(async ({ contactPage }) => {
				await contactPage.openForm()
			})

			test.describe('When the user submits the form', () => {
				test.beforeEach(async ({ contactPage }) => {
					await contactPage.form.submit()
				})

				test('it should show a success alert', async ({ contactPage }) => {
					await expect(contactPage.getSuccessAlert()).toBeVisible()
				})
			})
		})
	})
})
```

Colocate `*.spec.ts` + `*.page.ts` + `*.fixture.ts` + `*.builders.ts`.

## 2. Prefer Accessible Test Queries

**Impact: HIGH**

**Prefer:** `getByRole`, `getByLabel`, page-object wrappers.

**Avoid:** `getByTestId` as primary, CSS class locators, stale scopes after
navigation.

**Incorrect:**

```typescript
await page.getByTestId('contact-submit').click()
await page.locator('.btn-primary').click()
```

**Correct:**

```typescript
await page.getByRole('button', { name: 'Submit' }).click()
await contactPage.form.submit()
```
