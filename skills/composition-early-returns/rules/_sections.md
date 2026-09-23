# Sections

This file defines all sections, their ordering, impact levels, and descriptions.
The section ID (in parentheses) is the filename prefix used to group rules.

---

## 1. Conditional UI (rendering)

**Impact:** HIGH  
**Description:** Prefer composition + early returns over nested conditional
JSX. Ternary over `&&` for render guards. Optional sections as child components
with early returns.

## 2. Entry-point factories (patterns)

**Impact:** HIGH  
**Description:** Push kind/type/product conditionals to routes and factories so
domain modules stay single-purpose and branch-free.
