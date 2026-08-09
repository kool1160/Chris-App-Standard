# Audit Process — App Standard

## Audit authority

**The Review-Control Chat is the acceptance auditor. Codex is the builder and may not approve its own work.**

Claude / Anthropic is **not** part of the standard audit, review, fallback, or tie-break process. Do not route a project to Claude for an audit. If additional model review is ever desired, use an explicitly approved OpenAI review path; deterministic evidence remains primary.

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

**Deterministic evidence first. Independent Review-Control judgment second. No Claude audit.**