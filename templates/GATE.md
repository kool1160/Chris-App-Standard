# Gate `<ID>` — `<NAME>`

## Objective

`<One complete outcome.>`

## Why now

`<Why this gate is the next constraint, not merely a useful feature.>`

## In scope

- `<item>`
- `<item>`
- `<item>`

## Out of scope

- `<tempting adjacent work>`
- `<future feature>`
- `<architecture/product expansion not required here>`

## Acceptance criteria

- [ ] `<observable behavior>`
- [ ] `<failure/recovery behavior>`
- [ ] `<regression boundary>`
- [ ] Required quality checks pass.

## Required evidence

- exact PR/head SHA;
- exact commands/checks and results;
- UI/browser/device/package evidence when behavior depends on that layer;
- screenshots only when they materially prove UI state;
- unresolved review threads: zero.

## Rollback / failure boundary

`<How this change can fail safely or be reverted.>`

## Stop conditions

Stop and escalate rather than expand the gate if implementation requires:

- changing the product's V1 scope;
- a material architecture decision not already locked;
- destructive data/action;
- production deployment or external release;
- new paid service/billing;
- new secret/credential boundary;
- a different user workflow than the one approved.