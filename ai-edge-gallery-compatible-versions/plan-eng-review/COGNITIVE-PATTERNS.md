# Cognitive Patterns — How Great Eng Managers Think

These are not additional checklist items. They are the instincts that experienced engineering leaders develop over years — the pattern recognition that separates "reviewed the code" from "caught the landmine." Apply them throughout your review.

---

1. **State diagnosis** — Teams exist in four states: falling behind, treading water, repaying debt, innovating. Each demands a different intervention (Larson, An Elegant Puzzle).

2. **Blast radius instinct** — Every decision evaluated through "what's the worst case and how many systems/people does it affect?"

3. **Boring by default** — "Every company gets about three innovation tokens." Everything else should be proven technology (McKinley, Choose Boring Technology).

4. **Incremental over revolutionary** — Strangler fig, not big bang. Canary, not global rollout. Refactor, not rewrite (Fowler).

5. **Systems over heroes** — Design for tired humans at 3am, not your best engineer on their best day.

6. **Reversibility preference** — Feature flags, A/B tests, incremental rollouts. Make the cost of being wrong low.

7. **Failure is information** — Blameless postmortems, error budgets, chaos engineering. Incidents are learning opportunities, not blame events (Allspaw, Google SRE).

8. **Org structure IS architecture** — Conway's Law in practice. Design both intentionally (Skelton/Pais, Team Topologies).

9. **DX is product quality** — Slow CI, bad local dev, painful deploys lead to worse software and higher attrition. Developer experience is a leading indicator.

10. **Essential vs accidental complexity** — Before adding anything: "Is this solving a real problem or one we created?" (Brooks, No Silver Bullet).

11. **Two-week smell test** — If a competent engineer can't ship a small feature in two weeks, you have an onboarding problem disguised as architecture.

12. **Glue work awareness** — Recognize invisible coordination work. Value it, but don't let people get stuck doing only glue (Reilly, The Staff Engineer's Path).

13. **Make the change easy, then make the easy change** — Refactor first, implement second. Never structural + behavioral changes simultaneously (Beck).

14. **Own your code in production** — No wall between dev and ops. "The DevOps movement is ending because there are only engineers who write code and own it in production" (Majors).

15. **Error budgets over uptime targets** — SLO of 99.9% = 0.1% downtime *budget to spend on shipping*. Reliability is resource allocation (Google SRE).

---

## How to Apply

When evaluating architecture, think "boring by default." When reviewing tests, think "systems over heroes." When assessing complexity, ask Brooks's question. When a plan introduces new infrastructure, check whether it's spending an innovation token wisely.
