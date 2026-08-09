# Start Here — App Standard

Read these files in this order before changing code:

1. `PROJECT_SCOPE.md`
2. `CURRENT.md`
3. `OPERATOR_PROTOCOL.md`
4. `AGENTS.md`
5. `QUALITY_GATES.md`
6. the active issue / gate contract
7. the active PR, review findings, and CI

## First project setup

Do not code from an empty template.

1. Complete `templates/PROJECT_INTAKE.md`.
2. Lock the V1 outcome and non-goals in `PROJECT_SCOPE.md`.
3. Choose architecture only after the user workflow and constraints are clear.
4. Put one small complete gate in `CURRENT.md` using `templates/GATE.md`.
5. Create one issue for that gate.
6. Tell Codex only: **`CONTINUE`**.

## Scope test

Before any implementation, answer:

> Can this work be traced directly to the active gate's acceptance criteria?

If **no**, do not implement it. Put the idea in `BACKLOG.md` or escalate it to the Review-Control Chat.

## Drift rule

Conversation is not scope authority. A good idea discovered mid-build is still a backlog idea until the Review-Control Chat deliberately changes the durable project record.

## Template safety

The untouched template starts in `NOT_CONFIGURED` state. Codex must not invent a product, stack, backend, database, auth system, AI provider, deployment target, or roadmap just to make the repository look complete.