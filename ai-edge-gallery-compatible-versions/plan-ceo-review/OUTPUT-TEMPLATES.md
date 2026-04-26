# Output Templates

## "NOT in scope" Section

List work considered and explicitly deferred, with one-line rationale each.

```
## NOT in scope

- [item]: [why deferred]
- [item]: [why deferred]
```

---

## "What already exists" Section

List existing code/flows that partially solve sub-problems.

```
## What already exists

- [existing code/flow]: [reused / unnecessarily rebuilt]
```

---

## "Dream state delta" Section

Where this plan leaves us relative to the 12-month ideal.

```
## Dream State Delta

Current state:  [describe]
After this plan: [describe]
12-month ideal:  [describe]
Gap remaining:   [describe what's still needed]
```

---

## Error & Rescue Registry

From Section 2. Complete table of every method that can fail.

```
METHOD/CODEPATH     | WHAT CAN GO WRONG     | EXCEPTION CLASS
--------------------|----------------------|------------------
[method]            | [failure]            | [class]

EXCEPTION CLASS     | RESCUED? | RESCUE ACTION        | USER SEES
--------------------|----------|---------------------|------------------
[class]             | Y/N      | [action]            | [what user sees]
```

---

## Failure Modes Registry

```
CODEPATH | FAILURE MODE   | RESCUED? | TEST? | USER SEES?     | LOGGED?
---------|----------------|----------|-------|----------------|--------
```

Any row with RESCUED=N, TEST=N, USER SEES=Silent -> **CRITICAL GAP**.

---

## Completion Summary

```
+====================================================================+
|            CEO PLAN REVIEW — COMPLETION SUMMARY                     |
+====================================================================+
| Mode selected        | EXPANSION / SELECTIVE / HOLD / REDUCTION     |
| Step 0               | [mode + key decisions]                      |
| Section 1  (Arch)    | ___ issues found                            |
| Section 2  (Errors)  | ___ error paths mapped, ___ GAPS            |
| Section 3  (Security)| ___ issues found, ___ High severity         |
| Section 4  (Data/UX) | ___ edge cases mapped, ___ unhandled        |
| Section 5  (Quality) | ___ issues found                            |
| Section 6  (Tests)   | diagram produced, ___ gaps                  |
| Section 7  (Perf)    | ___ issues found                            |
| Section 8  (Observ)  | ___ gaps found                              |
| Section 9  (Deploy)  | ___ risks flagged                           |
| Section 10 (Future)  | Reversibility: _/5, debt items: ___         |
| Section 11 (Design)  | ___ issues / SKIPPED (no UI scope)          |
+--------------------------------------------------------------------+
| NOT in scope         | written (___ items)                          |
| What already exists  | written                                     |
| Dream state delta    | written                                     |
| Error/rescue registry| ___ methods, ___ CRITICAL GAPS              |
| Failure modes        | ___ total, ___ CRITICAL GAPS                |
| Scope proposals      | ___ proposed, ___ accepted (EXP + SEL)      |
| Unresolved decisions | ___ (listed below)                          |
+====================================================================+
```

---

## Scope Expansion Decisions (EXPANSION and SELECTIVE only)

```
## Scope Decisions

| # | Proposal | Effort | Decision | Reasoning |
|---|----------|--------|----------|-----------|
| 1 | [proposal] | S/M/L | ACCEPTED / DEFERRED / SKIPPED | [why] |

## Accepted Scope
- [items added to scope]

## Deferred
- [items sent to later work]

## Skipped
- [items rejected]
```

---

## Unresolved Decisions

```
## Unresolved Decisions

These decisions were left open and may bite you later:

1. [Issue #N]: [description]
2. [Issue #N]: [description]
```
