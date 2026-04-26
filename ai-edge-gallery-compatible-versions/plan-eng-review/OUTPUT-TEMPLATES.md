# Output Templates

## "NOT in scope" Section

Every plan review MUST produce this section. List work that was considered and explicitly deferred, with a one-line rationale for each item.

```
## NOT in scope

- [item]: [why deferred]
- [item]: [why deferred]
```

---

## "What already exists" Section

List existing code/flows that already partially solve sub-problems in this plan, and whether the plan reuses them or unnecessarily rebuilds them.

```
## What already exists

- [existing code/flow]: [reused / unnecessarily rebuilt]
- [existing code/flow]: [reused / unnecessarily rebuilt]
```

---

## Failure Modes Registry

For each new codepath identified in the review, list one realistic way it could fail in production.

```
CODEPATH         | FAILURE MODE    | TEST? | ERROR HANDLING? | USER SEES?
-----------------|-----------------|-------|-----------------|------------
[codepath]       | [timeout/nil/   | Y/N   | Y/N             | Clear error /
                 |  race/stale]    |       |                 | Silent failure
```

Any row with TEST=N AND ERROR HANDLING=N AND USER SEES=Silent -> **CRITICAL GAP**.

---

## Completion Summary

Fill in and display at the end of the review:

```
ENGINEERING PLAN REVIEW — COMPLETION SUMMARY
=============================================
Step 0: Scope Challenge — [scope accepted / scope reduced]
Architecture Review:  ___ issues found
Code Quality Review:  ___ issues found
Test Review:          diagram produced, ___ gaps identified
Performance Review:   ___ issues found
---------------------------------------------
NOT in scope:         written (___ items)
What already exists:  written
Failure modes:        ___ total, ___ CRITICAL GAPS
Unresolved decisions: ___
=============================================
```

---

## Unresolved Decisions

If the user does not respond to a question or interrupts to move on, list unresolved decisions here. Never silently default to an option.

```
## Unresolved Decisions

These decisions were left open and may bite you later:

1. [Issue #N]: [brief description of what wasn't decided]
2. [Issue #N]: [brief description]
```
