# Review Sections — Detailed Evaluation Criteria

## Section 1: Architecture Review

Evaluate:
- **Overall system design** and component boundaries.
- **Dependency graph** and coupling concerns. Which components are now coupled that weren't before? Is that coupling justified?
- **Data flow patterns** and potential bottlenecks. For every new data flow, trace:
  - Happy path (data flows correctly)
  - Nil path (input is nil/missing)
  - Empty path (input is present but empty/zero-length)
  - Error path (upstream call fails)
- **Scaling characteristics.** What breaks first under 10x load? Under 100x?
- **Single points of failure.** Map them.
- **Security architecture.** Auth boundaries, data access patterns, API surfaces. For each new endpoint: who can call it, what do they get, what can they change?
- **Production failure scenarios.** For each new integration point, describe one realistic production failure and whether the plan accounts for it.
- **Distribution architecture.** If this introduces a new artifact, how does it get built, published, and updated?

---

## Section 2: Code Quality Review

Evaluate:
- **Code organization** and module structure. Does new code fit existing patterns?
- **DRY violations** — be aggressive. If the same logic exists elsewhere, flag it.
- **Naming quality.** Are new classes, methods, and variables named for what they do, not how they do it?
- **Error handling patterns** and missing edge cases (call these out explicitly).
- **Technical debt** hotspots.
- **Over-engineering check.** Any new abstraction solving a problem that doesn't exist yet?
- **Under-engineering check.** Anything fragile, assuming happy path only, or missing obvious defensive checks?

---

## Section 3: Test Review

Make a complete diagram of everything new the plan introduces:

```
NEW UX FLOWS:
  [list each new user-visible interaction]

NEW DATA FLOWS:
  [list each new path data takes through the system]

NEW CODEPATHS:
  [list each new branch, condition, or execution path]

NEW BACKGROUND JOBS / ASYNC WORK:
  [list each]

NEW INTEGRATIONS / EXTERNAL CALLS:
  [list each]

NEW ERROR/RESCUE PATHS:
  [list each]
```

For each item:
- What type of test covers it? (Unit / Integration / System / E2E)
- Does a test for it exist in the plan? If not, write the test spec header.
- What is the happy path test?
- What is the failure path test? (Be specific — which failure?)
- What is the edge case test? (nil, empty, boundary values, concurrent access)

**Test ambition check:**
- What's the test that would make you confident shipping at 2am on a Friday?
- What's the test a hostile QA engineer would write to break this?

**Test pyramid check:** Many unit, fewer integration, few E2E? Or inverted?

**Flakiness risk:** Flag any test depending on time, randomness, external services, or ordering.

---

## Section 4: Performance Review

Evaluate:
- **N+1 queries** and database access patterns.
- **Memory usage.** For every new data structure: what's the maximum size in production?
- **Caching opportunities.** For every expensive computation or external call: should it be cached?
- **Slow paths.** Top 3 slowest new codepaths and estimated latency.
- **Connection pool pressure.** New DB connections, HTTP connections?
