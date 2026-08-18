# Chris App Standard

Reusable operating standard for interactive applications.

Use this repository as the starting point for apps that need real user workflows, state, data, APIs, optional AI, responsive UI, or later wrapper/native packaging. If the product is primarily a desktop engineering/system tool, start from `Chris-Software-Standard`. If it is primarily a public website, start from `Chris-Web-Standard`.

## The rule

**Keep the product simple in front and disciplined underneath.**

A new project starts with the problem, user, V1 outcome, scope, non-goals, and proof of success. It does not start by inventing architecture.

## Default platform

Chris's standard application platform is **Vercel + Supabase**.

- **Vercel** is the default hosting, preview, and deployment surface.
- **Supabase** is the default backend/data platform for database, auth, storage, realtime, and server-side data services the app actually needs.

Do not re-decide the platform on every app. A different platform requires a concrete product/technical reason and explicit owner approval. See `PLATFORM_STANDARD.md`.

## Run it in 60 seconds

1. Complete `templates/PROJECT_INTAKE.md` with the owner.
2. Lock the result into `PROJECT_SCOPE.md` and one active gate in `CURRENT.md`.
3. Start the planning/review chat with `templates/REVIEW_CONTROL_CHAT.md`.
4. Start Codex with `templates/CODEX_CHAT.md`.
5. Review-Control says **`CONTINUE`**.
6. Codex works one bounded pass and stops **`AWAITING_REVIEW`**.
7. Review-Control audits the exact head using `AUDIT_PROCESS.md`. Repair needed? It records the finding and says **`CONTINUE`** again. Pass? It performs routine advancement inside the already-approved plan and says **`CONTINUE`** for the next gate.
8. The owner is pulled back in only for real product decisions, exceptions, controlled/high-risk actions, or an explicitly requested Claude audit circuit breaker.

## Operating loop

```text
Owner vision / product decision
          ↓
Review-Control Chat locks one active gate
          ↓
       CONTINUE
          ↓
Codex implements or repairs one bounded pass
          ↓
    AWAITING_REVIEW
          ↓
Review-Control exact-head audit
     ↙                 ↘
CONTINUE            OWNER_DECISION / BLOCKED
```

The owner should not have to carry technical prompts between chats. GitHub holds scope, findings, evidence, and current state.

## Audit rule

Audit is **deterministic checks first, Review-Control exact-head review second**. Claude / Anthropic is not a required audit, routine fallback, or automatic tie-breaker. Only the owner may explicitly invoke a one-off Claude audit to break a stalled or repeatedly stacking review/repair loop. Claude's report is advisory evidence; it does not merge, advance, redefine scope, or override deterministic failures. See `AUDIT_PROCESS.md`.

## Core guardrails

- One repository, one active gate, one implementation PR.
- `CURRENT.md` stays short and always shows **IN SCOPE**, **OUT OF SCOPE**, acceptance evidence, and the next valid action.
- New ideas go to `BACKLOG.md`; they do not become current work by conversation drift.
- Codex does not choose new scope, merge, advance, or keep working after `AWAITING_REVIEW`.
- The Review-Control Chat independently reviews the exact pushed head. It may perform routine merge/next-gate advancement only when the work is already inside the locked plan and every required check passes.
- Product direction, material architecture changes, destructive actions, production deployment, billing, paid services, secrets, external side effects, and unresolved ambiguity escalate to the owner.
- Evidence beats confidence. Green CI alone is not proof of product correctness.
- Prefer the smallest complete vertical slice over broad scaffolding.
- Vercel/Supabase integration must preserve secret boundaries, environment separation, migrations, authorization/RLS, and production-data safety.

## Start here

1. Read `START_HERE.md`.
2. Complete `templates/PROJECT_INTAKE.md`.
3. Replace the placeholders in `PROJECT_SCOPE.md`.
4. Put exactly one bounded gate in `CURRENT.md`.
5. Use `OPERATOR_PROTOCOL.md` for the two-chat loop.
6. Use `AUDIT_PROCESS.md` and `QUALITY_GATES.md` as the acceptance bar.

## Standard files

- `START_HERE.md` — required reading order and first setup
- `PROJECT_SCOPE.md` — durable product boundary
- `CURRENT.md` — one active gate, kept directly in front of every agent
- `OPERATOR_PROTOCOL.md` — Review-Control Chat ↔ Codex workflow and owner-triggered Claude circuit breaker
- `AUDIT_PROCESS.md` — exact-head acceptance audit; Claude only by explicit owner request
- `PLATFORM_STANDARD.md` — Vercel + Supabase default platform and guardrails
- `AGENTS.md` — authority and fail-closed rules
- `QUALITY_GATES.md` — app-specific definition of acceptable work
- `BACKLOG.md` — idea parking lot; not implementation authority
- `templates/PROJECT_INTAKE.md` — fast product setup
- `templates/GATE.md` — bounded milestone/gate template
- `templates/REVIEW_CONTROL_CHAT.md` — ready-to-use planning/review chat role
- `templates/CODEX_CHAT.md` — ready-to-use implementation chat role
- `.github/pull_request_template.md` — scope/evidence handoff
- `sxf/project.sxf.example.yaml` — safe non-executing SXF 0.1 example for future factory integration

## Status

**V1 operating foundation is ready to use.** Vercel + Supabase is the default application platform. Project-specific product architecture inside that platform is selected from real requirements rather than speculative complexity.