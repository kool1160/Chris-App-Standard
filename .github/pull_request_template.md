## Active gate

`<ID — name>`

## Scope delivered

- 
- 

## Explicitly not changed

- 
- 

## Evidence

- Lint/format: `<command + result>`
- Type/static checks: `<command + result>`
- Unit tests: `<command + result>`
- Integration/E2E: `<command + result or N/A with reason>`
- Build/package: `<command + result>`
- UI/device/package evidence: `<result or N/A with reason>`

## Risk / rollback

`<one short statement>`

## Scope-drift check

- [ ] Every changed file is required by the active gate or a documented gate repair.
- [ ] No backlog/future feature entered this PR.
- [ ] No new service/dependency/architecture boundary was introduced without authority.
- [ ] No production deployment, billing, destructive action, or secret exposure occurred.

## Handoff

`AWAITING_REVIEW`

Head: `<full SHA>`