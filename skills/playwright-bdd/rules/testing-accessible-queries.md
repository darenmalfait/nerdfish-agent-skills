---
title: Prefer Accessible Test Queries
impact: HIGH
impactDescription: Query the UI the way a user would
tags: testing, playwright, a11y
---

## Prefer Accessible Test Queries

**Impact: HIGH**

Query the UI the way a user (or assistive tech) would — roles, labels, text —
not implementation details.

### Prefer

- `getByRole` / `findByRole`
- `getByLabel` / `findByLabelText`
- Page-object wrappers around those (`contactPage.form.getNameInput()`)

### Avoid

- `getByTestId` / `findByTestId` as primary selectors
- CSS: `querySelector`, `getByClassName`, `locator('.foo')`-style class chasing
- Storing query results then reusing after navigation (stale scope)
- Preferring `getByText` / `getByPlaceholderText` / `getByTitle` when a role or
  label query exists

**Incorrect:**

```typescript
await page.getByTestId('contact-submit').click()
await page.locator('.btn-primary').click()
await page.getByPlaceholderText('Email').fill('a@b.c')
```

**Correct:**

```typescript
await page.getByRole('button', { name: 'Submit' }).click()
await page.getByLabel('Email address').fill('a@b.c')

// Better: hide selectors in the page object
await contactPage.form.getEmailInput().fill('a@b.c')
await contactPage.form.submit()
```
