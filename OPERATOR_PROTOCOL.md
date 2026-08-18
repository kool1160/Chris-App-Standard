# Operator Protocol — App Standard

## Purpose

Make project operation simple enough that the owner does not become a human message bus.

> **Review-Control Chat decides and reviews. GitHub remembers. Codex implements one bounded pass.**

One repo. One active gate. One implementation PR.

## The two working chats

### 1. Review-Control Chat

Owns:

- product/scope discussion;
- durable decisions;
- `PROJECT_SCOPE.md` and `CURRENT.md` authority;
- exact-head review;
- detailed review findings on GitHub;
- routine merge and activation of the next already-approved gate;
- owner escalation when a real product decision is required.

It does **not** do normal implementation work.

### 2. Codex Implementation Chat

Owns:

- implementation of the one active gate;
- repair of blocking review findings on the same PR;
- tests and deterministic evidence;
- updating the same implementation branch/PR;
- stopping when the bounded pass is complete.

It does **not** choose new scope, merge, advance, deploy, or approve its own work.

## The simple loop

### Review-Control Chat output

Normal successful output is:

```text
CONTINUE
Gate: <id/name>
PR: none | #__
Reason: <one sentence>
```

`CONTINUE` means Codex should read GitHub and perform the next valid bounded pass. The owner should not need to copy technical instructions.

If a real decision is required:

```text
OWNER_DECISION
Question: <one short product/architecture/risk decision>
Why it matters: <one sentence>
```

If work cannot validly proceed:

```text
BLOCKED
Reason: <one sentence>
```

### Codex output

Codex always stops with:

```text
AWAITING_REVIEW
Gate: <id/name>
PR: #__
Head: <full SHA>
CI: green | failing | running
Work: <one sentence>
Blocker: none | <one sentence>
```

or:

```text
BLOCKED
Gate: <id/name>
Reason: <one sentence>
```

## What Codex does when told `CONTINUE`

Read repository truth first, then follow this order:

1. If `CURRENT.md` is `NOT_CONFIGURED` or `HELD`, stop.
2. If the active PR has unresolved blocking findings, repair only those findings on the same PR.
3. If required CI is failing, repair only the failure within the active gate.
4. If the PR is green and no blocker remains, refresh exact-head evidence and stop at `AWAITING_REVIEW`.
5. If no implementation PR exists, implement the smallest complete slice allowed by `CURRENT.md`, open one focused draft PR, and stop at `AWAITING_REVIEW`.
6. If the needed work conflicts with `PROJECT_SCOPE.md`, requires a missing decision, or exceeds the gate, record the blocker and stop.

`CONTINUE` never means “keep finding useful things to do.”

## What the Review-Control Chat does after `AWAITING_REVIEW`

1. Read `PROJECT_SCOPE.md`, `CURRENT.md`, the active gate, PR, full diff, exact head, review threads, and required checks fresh.
2. Independently verify acceptance. Do not accept the builder's summary as proof.
3. If repair is needed, put the specific blocking finding on GitHub and return `CONTINUE`. Codex repairs the same PR.
4. If the exact head is accepted and the work is routine, merge with exact-head protection, record evidence in `CURRENT.md`, activate exactly one next gate that is already approved, then return `CONTINUE`.
5. If the project/gate is complete, return `COMPLETE`.
6. If advancement would require a new product decision, material architecture change, destructive action, production deployment, billing/paid service, secret handling change, external side effect, or meaningful scope change, return `OWNER_DECISION` instead of guessing.

## Owner-triggered Claude audit circuit breaker

Claude is **not** part of the normal two-chat loop. It is never required for a PR, gate, milestone, merge, or tie-break.

Only the owner may trigger it, with an explicit instruction such as:

```text
CLAUDE AUDIT
```

or an unmistakable equivalent such as “Claude audit this PR right now.”

This is intended as a circuit breaker when the normal Review-Control ↔ Codex loop has become unproductive—for example, repeated repair passes keep stacking findings, the same defect is not being resolved, or the owner wants an independent second look before spending more time on the loop. There is no automatic threshold and Review-Control may not invoke Claude on its own.

When triggered:

1. Freeze the scope at the current gate and exact PR head being audited.
2. Give Claude the relevant GitHub truth, complete diff, deterministic evidence, review findings, and unresolved threads.
3. Ask for an independent audit/finding report, not implementation authority.
4. Treat Claude findings as advisory until reproduced or otherwise substantiated where practical.
5. Record actionable blocking findings on GitHub.
6. Claude does not merge, advance, redefine scope, waive failing evidence, or grant production/destructive authority.
7. Resume the normal Review-Control ↔ Codex loop after the one-off audit is incorporated.

The owner can use this whenever the normal loop is pissing them off or no longer earning confidence; the template must never force it when the owner did not ask for it.

## Scope-drift firewall

- New idea discovered during implementation → `BACKLOG.md`.
- Nice-to-have cleanup outside the active acceptance criteria → backlog.
- “While we're here” refactor not required by the gate → backlog.
- Future infrastructure with no current consumer → backlog.
- New dependency or service that materially changes architecture → owner/control decision.
- A blocker may justify a narrow repair. It does not authorize a redesign.

## Routine merge authority

This standard deliberately removes a separate routine “Advance” ceremony. The Review-Control Chat may merge an accepted exact head and activate the next **already-approved** gate when all guardrails pass.

The owner remains the authority for exceptions and material decisions. Projects with higher-risk release requirements may override this standard and require explicit owner advancement.