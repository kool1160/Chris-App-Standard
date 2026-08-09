# Agent Instructions — App Standard

## Authority order

Follow these sources in order:

1. Explicit owner instruction for the current decision
2. `PROJECT_SCOPE.md`
3. `CURRENT.md`
4. `OPERATOR_PROTOCOL.md`
5. `AUDIT_PROCESS.md`
6. `PLATFORM_STANDARD.md`
7. `AGENTS.md`
8. active gate / issue
9. active PR, exact head, review threads, and CI
10. `QUALITY_GATES.md`
11. `BACKLOG.md`
12. historical notes

A lower source cannot silently override a higher one. Conflict means `BLOCKED`.

## Permanent rules

- One active gate. One implementation PR. No parallel future work.
- Codex implements or repairs only what `CURRENT.md` allows.
- Codex never changes product scope to make implementation easier.
- Codex never merges, advances, deploys, publishes, charges, deletes production data, changes billing, exposes secrets, or performs another external side effect unless the current gate explicitly authorizes it and the authority boundary permits it.
- New ideas and unrelated cleanup go to `BACKLOG.md`.
- Do not create speculative infrastructure, abstractions, services, data stores, auth systems, or frameworks without a current requirement.
- Do not silently add a dependency when the platform can already solve the problem cleanly.
- Keep secrets out of source, fixtures, logs, prompts, screenshots, and CI.
- Block instead of guessing about missing requirements, destructive actions, user data, production state, architecture conflicts, or external services.
- Tests prove behavior at the layer where the risk exists. A unit test does not prove a packaged/native/browser integration.
- Builder confidence is not review evidence.
- **Claude / Anthropic is not used for standard audit, review, fallback, or tie-breaking.** Follow `AUDIT_PROCESS.md`.

## App platform rules

- Default platform is **Vercel + Supabase**.
- Do not substitute another hosting/backend platform without explicit owner approval and a concrete reason.
- Never expose Supabase service-role or privileged secrets to client/browser code.
- Use explicit authorization and appropriate RLS where applicable.
- Database changes use durable migrations.
- Preview/test work must not silently modify production data.
- Production deployment is a controlled action.

## App-specific product rules

- Optimize for the primary user workflow, not the number of features.
- The UI must expose understandable actions, truthful state, loading, empty, success, and failure behavior.
- Responsive behavior and accessibility are product requirements when the supported surface requires them.
- Keep privileged/server operations behind narrow validated boundaries; never expose secrets or unrestricted system access to the client.
- AI output must not bypass deterministic validation, required confirmation, permissions, or product truth.
- External actions such as send, publish, purchase, delete, or release must be explicit and recoverable where practical.

## Codex stop condition

Once the bounded implementation/repair pass is pushed with evidence, stop at `AWAITING_REVIEW`. Do not inspect the backlog for more work.