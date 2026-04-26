# Review Sections — Detailed Evaluation Criteria

## Section 1: Architecture Review

Evaluate and diagram:
- **Overall system design** and component boundaries. Draw the dependency graph.
- **Data flow** — all four paths. For every new data flow:
  - Happy path (data flows correctly)
  - Nil path (input is nil/missing)
  - Empty path (input is present but empty/zero-length)
  - Error path (upstream call fails)
- **State machines.** For every new stateful object: include impossible/invalid transitions and what prevents them.
- **Coupling concerns.** Which components are now coupled that weren't before?
- **Scaling characteristics.** What breaks first under 10x load? Under 100x?
- **Single points of failure.** Map them.
- **Security architecture.** Auth boundaries, data access, API surfaces.
- **Production failure scenarios.** For each new integration point: one realistic failure and whether the plan accounts for it.
- **Rollback posture.** If this ships and breaks, what's the procedure? How long?

**EXPANSION/SELECTIVE additions:**
- What would make this architecture beautiful? Not just correct — elegant.
- What infrastructure would make this feature a platform others can build on?

---

## Section 2: Error & Rescue Map

For every new method, service, or codepath that can fail:

```
METHOD/CODEPATH          | WHAT CAN GO WRONG           | EXCEPTION CLASS
-------------------------|-----------------------------|-----------------
ExampleService#call      | API timeout                 | TimeoutError
                         | API returns 429             | RateLimitError
                         | Malformed JSON              | JSONParseError
                         | DB pool exhausted           | ConnectionPoolExhausted
                         | Record not found            | RecordNotFound

EXCEPTION CLASS          | RESCUED?  | RESCUE ACTION          | USER SEES
-------------------------|-----------|------------------------|------------------
TimeoutError             | Y         | Retry 2x, then raise   | "Service unavailable"
RateLimitError           | Y         | Backoff + retry         | Nothing (transparent)
JSONParseError           | N <- GAP  | —                      | 500 error <- BAD
```

Rules:
- Catch-all error handling is ALWAYS a smell. Name specific exceptions.
- Every rescued error must: retry with backoff, degrade gracefully, or re-raise with context.
- "Swallow and continue" is almost never acceptable.
- For each GAP: specify the rescue action and what the user should see.

---

## Section 3: Security & Threat Model

Evaluate:
- **Attack surface expansion.** New endpoints, params, file paths, background jobs?
- **Input validation.** For every new user input: validated, sanitized, rejected on failure?
- **Authorization.** For every new data access: scoped to the right user/role? Direct object reference vulnerability?
- **Secrets and credentials.** In env vars, not hardcoded? Rotatable?
- **Dependency risk.** New packages? Security track record?
- **Injection vectors.** SQL, command, template, LLM prompt injection.
- **Audit logging.** For sensitive operations: is there an audit trail?

For each finding: threat, likelihood, impact, and whether the plan mitigates it.

---

## Section 4: Data Flow & Interaction Edge Cases

**Data Flow Tracing:** For every new data flow:
```
INPUT -> VALIDATION -> TRANSFORM -> PERSIST -> OUTPUT
  |           |            |           |          |
  v           v            v           v          v
[nil?]    [invalid?]   [exception?] [conflict?] [stale?]
[empty?]  [too long?]  [timeout?]   [dup key?]  [partial?]
```
For each node: what happens on each shadow path? Is it tested?

**Interaction Edge Cases:** For every new user-visible interaction:
```
INTERACTION          | EDGE CASE              | HANDLED? | HOW?
---------------------|------------------------|----------|--------
Form submission      | Double-click submit    | ?        |
                     | Submit with stale state| ?        |
Async operation      | User navigates away    | ?        |
                     | Operation times out    | ?        |
List/table view      | Zero results           | ?        |
                     | 10,000 results         | ?        |
```

---

## Section 5: Code Quality Review

Evaluate:
- Code organization and module structure.
- DRY violations — be aggressive.
- Naming quality.
- Error handling patterns (cross-reference Section 2).
- Over-engineering and under-engineering.
- Cyclomatic complexity — flag methods that branch more than 5 times.

---

## Section 6: Test Review

Map everything new:
```
NEW UX FLOWS:          [list each]
NEW DATA FLOWS:        [list each]
NEW CODEPATHS:         [list each]
NEW ASYNC WORK:        [list each]
NEW INTEGRATIONS:      [list each]
NEW ERROR PATHS:       [list each]
```

For each:
- Test type (Unit / Integration / E2E)?
- Happy path test?
- Failure path test? (which failure?)
- Edge case test? (nil, empty, boundary, concurrent)

Test ambition: What's the "ship at 2am Friday" test? The hostile QA test?

---

## Section 7: Performance Review

- N+1 queries and database access patterns
- Memory usage — max size of new data structures in production
- Caching opportunities
- Slow paths — top 3 slowest new codepaths
- Connection pool pressure

---

## Section 8: Observability & Debuggability

- Logging at entry, exit, and each significant branch
- Metrics — what tells you it's working? What tells you it's broken?
- Tracing for cross-service flows
- Alerting — what new alerts should exist?
- Debuggability — can you reconstruct what happened from logs alone?
- Runbooks for each new failure mode

---

## Section 9: Deployment & Rollout

- Migration safety — backward-compatible? Zero-downtime?
- Feature flags — should any part be behind one?
- Rollout order — migrate first, deploy second?
- Rollback plan — explicit step-by-step
- Deploy-time risk window — old + new code running simultaneously
- Post-deploy verification checklist

---

## Section 10: Long-Term Trajectory

- Technical debt introduced
- Path dependency — does this make future changes harder?
- Knowledge concentration — documentation sufficient?
- Reversibility — rate 1-5
- The 1-year question — would a new engineer understand this?

**EXPANSION/SELECTIVE additions:**
- What comes after this ships? Phase 2? Phase 3?
- Platform potential — does this create capabilities others can leverage?

---

## Section 11: Design & UX Review (skip if no UI scope)

- Information architecture — what does the user see first, second, third?
- Interaction state coverage: LOADING / EMPTY / ERROR / SUCCESS / PARTIAL
- User journey coherence
- Responsive intention — is mobile mentioned or afterthought?
- Accessibility basics — keyboard nav, screen readers, contrast

**EXPANSION/SELECTIVE additions:**
- What would make this UI feel *inevitable*?
- What 30-minute UI touches would make users think "they thought of that"?
