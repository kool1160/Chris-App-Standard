# Project Scope — App Standard

> This file is product truth. Keep it short enough to reread before every gate.

## Product

**Name:** `<PROJECT_NAME>`  
**Primary user:** `<WHO>`  
**Problem:** `<REAL PROBLEM>`  
**V1 outcome:** `<WHAT THE USER CAN SUCCESSFULLY DO>`

## Success proof

V1 is successful when:

- `<MEASURABLE USER OUTCOME>`
- `<RELIABILITY / QUALITY OUTCOME>`
- `<REAL-WORLD ACCEPTANCE OUTCOME>`

## In scope

- `<V1 capability>`
- `<V1 capability>`
- `<V1 capability>`

## Out of scope / non-goals

- `<Explicit non-goal>`
- `<Explicit non-goal>`
- `<Future idea that must not leak into V1>`

## Product boundaries

- Build the smallest complete workflow that solves the stated problem.
- Do not add auth, accounts, cloud sync, database, AI, payments, analytics, collaboration, notifications, background jobs, or native wrappers unless the product actually requires them.
- AI is an implementation option, not a default product requirement.
- External side effects such as sending, publishing, charging, deleting, or changing production require an explicit controlled gate.
- Prefer understandable user flow over exposing internal system complexity.

## Scope-change rule

Only the Review-Control Chat may change this file after an owner product decision. Codex may identify a scope conflict but must not resolve it by expanding the product.

A new idea goes to `BACKLOG.md` unless it is explicitly promoted into this file and then into `CURRENT.md`.