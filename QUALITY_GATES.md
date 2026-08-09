# Quality Gates — App Standard

These are the default minimums. A project may be stricter.

## 1. Scope

- The diff maps directly to the active gate.
- No unrelated feature, refactor, dependency, service, or future-roadmap work entered the PR.
- `CURRENT.md` still describes the work accurately.

## 2. Product behavior

- The primary user can complete the intended gate workflow.
- Success, loading, empty, cancellation, failure, retry/recovery, and permission-denied states are handled where relevant.
- User-facing labels and actions reflect what the system actually does.
- Destructive/external actions require an explicit user/control boundary.

## 3. Data and state

- Authoritative state has one clear owner.
- Persistence is versioned/migratable when durable user data exists.
- Stale/late async results cannot silently overwrite newer state.
- Failed operations do not claim success or leave ambiguous partial state.

## 4. Security and privacy

- Secrets remain server/main-process/secure-store side as appropriate.
- Input crossing trust boundaries is validated.
- Privileged APIs are narrow and explicit.
- No real private/customer/employer data in public fixtures, tests, screenshots, logs, or prompts.

## 5. UX and accessibility

- Supported screen sizes are usable without clipped critical controls.
- Keyboard/focus/accessible names/roles/states are correct for interactive UI when applicable.
- Error messages tell the user what happened and the next useful action.
- Advanced complexity is progressively disclosed rather than dumped on the user.

## 6. Verification

At minimum, run the project's declared:

- format/lint checks;
- type/static checks when applicable;
- unit tests;
- integration tests for changed boundaries;
- build/package check;
- browser/device/packaged E2E for user-critical behavior when applicable.

The PR must list exact commands and results.

## 7. Review

The Review-Control Chat checks the exact pushed head and complete diff. Green CI is necessary when required, but not sufficient. Review includes scope, product behavior, regression risk, trust boundaries, and acceptance criteria.

## Definition of done

A gate is done only when the intended user/system outcome is proven, required evidence is green, blocking findings are resolved, and the accepted exact head contains no hidden scope expansion.