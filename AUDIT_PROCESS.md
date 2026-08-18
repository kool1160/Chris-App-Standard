# Audit Process — App Standard

## Audit authority

**The Review-Control Chat is the default acceptance auditor. Codex is the builder and may not approve its own work.**

Claude / Anthropic is **not** a required audit, routine fallback, automatic tie-breaker, or milestone gate. Do not invoke Claude merely because a PR exists, a gate is important, or a second model would be nice to have.

The owner may explicitly invoke a one-off **Claude audit** as a circuit breaker when the normal Review-Control ↔ Codex repair loop is stalled, repeatedly stacking findings/repairs, or otherwise no longer earning confidence. That exception exists only when the owner directly requests it for the current work.

## Audit order

Audit the exact pushed PR head in this order.

### 1. Scope audit

Compare the full diff against `PROJECT_SCOPE.md` and `CURRENT.md`.

Fail the audit if the PR contains:

- future-gate work;
- unrelated cleanup/refactors;
- speculative infrastructure;
- unapproved service/dependency changes;
- behavior listed under OUT OF SCOPE.

New useful ideas belong in `BACKLOG.md`, not the current PR.

### 2. Deterministic audit

Run and inspect the project's declared checks as applicable:

- format/lint;
- type/static checks;
- unit tests;
- integration tests;
- build;
- migration/schema validation;
- dependency/security/secret checks;
- repository policy/guard checks.

A builder saying tests passed is not enough. The auditor verifies exact-head evidence.

### 3. Platform and trust-boundary audit

For the default Vercel + Supabase stack, inspect changed risk surfaces when applicable:

- Supabase migrations and schema changes;
- RLS / authorization behavior;
- client versus privileged/server key boundaries;
- environment-variable handling;
- preview/test versus production data separation;
- server/API validation;
- Vercel preview/build behavior;
- production deployment boundary.

No service-role or privileged secret may reach browser/client code.

### 4. Product / user-flow audit

For changed user-facing behavior, prove the real workflow at the right layer:

- primary path;
- loading/empty/failure/retry/recovery states;
- responsive behavior on supported sizes;
- keyboard/focus/accessibility where relevant;
- browser/device E2E for critical flows;
- explicit confirmation for destructive/external actions.

Screenshots or packaged/browser evidence are required when the risk cannot be proven by unit tests.

### 5. Exact-head review

Review the complete diff and acceptance criteria against the exact SHA. Check regression risk, data/security boundaries, UX truth, and whether the gate outcome is actually proven.

## Owner-triggered Claude audit circuit breaker

Claude is available only by explicit owner instruction such as `CLAUDE AUDIT` or an unmistakable equivalent directed at the current gate/PR.

When invoked:

1. Audit the same exact pushed head and the same locked scope; do not widen the task.
2. Give Claude the repository truth, active acceptance criteria, complete diff, deterministic evidence, existing review findings, and unresolved threads needed to inspect the problem independently.
3. Treat Claude's output as an **independent finding report**, not acceptance authority.
4. Reproduce or otherwise substantiate actionable findings where practical and record blocking findings on GitHub.
5. Claude may not merge, advance, redefine scope, waive deterministic failures, or grant production/destructive authority.
6. After the one-off audit is incorporated, return to the normal Review-Control ↔ Codex exact-head loop.

Review-Control may tell the owner that an external second-look could be useful, but it may **not invoke or require Claude on its own**.

## Verdicts

Return exactly one:

```text
PASS
Head: <full SHA>
Evidence: <short summary>
Next: routine merge / next approved gate
```

```text
REPAIR
Head: <full SHA>
Finding: <specific blocking defect>
Next: CONTINUE
```

```text
BLOCKED
Head: <full SHA>
Reason: <missing decision/evidence/external prerequisite>
```

A changed head invalidates the prior audit. Re-audit the new exact head.

## Principle

**Deterministic evidence first. Review-Control is the default independent auditor. Claude is an owner-triggered circuit breaker only, never a required audit.**