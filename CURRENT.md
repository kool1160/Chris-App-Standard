# Current — App Standard

**Status:** `NOT_CONFIGURED`

This is the first file the Review-Control Chat and Codex use to answer: **What exactly are we doing right now?**

## Active gate

**Gate:** `<GATE_ID — SHORT NAME>`  
**Issue:** `<#>`  
**PR:** `none`  
**State:** `READY_TO_IMPLEMENT | AWAITING_REVIEW | REPAIR | BLOCKED | COMPLETE | HELD`

## Objective

`<One sentence describing the user-visible or system outcome this gate must deliver.>`

## IN SCOPE

- `<bounded item>`
- `<bounded item>`
- `<bounded item>`

## OUT OF SCOPE

- `<explicit temptation / future feature>`
- `<explicit temptation / future feature>`
- `<anything not needed for this gate>`

## Acceptance evidence

- [ ] Required deterministic checks pass.
- [ ] Gate-specific acceptance criteria pass.
- [ ] User-facing behavior is proven at the correct layer.
- [ ] No unresolved blocking review finding remains.
- [ ] No out-of-scope behavior entered the PR.

## Review state

**Reviewed head:** `none`  
**CI:** `none`  
**Blocking finding:** `none`

## Next valid action

`COMPLETE PROJECT INTAKE BEFORE IMPLEMENTATION`

## Hard rule

There is exactly **one active gate**. New work does not become active because it was mentioned in chat, discovered by Codex, or seems convenient while editing nearby code.