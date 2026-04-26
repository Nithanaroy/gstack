# Mode Reference — Comparison Table

```
+-----------+-------------+-------------+-------------+------------------+
|           | EXPANSION   | SELECTIVE   | HOLD SCOPE  | REDUCTION        |
+-----------+-------------+-------------+-------------+------------------+
| Scope     | Push UP     | Hold + offer| Maintain    | Push DOWN        |
|           | (opt-in)    |             |             |                  |
| Recommend | Enthusiastic| Neutral     | N/A         | N/A              |
| posture   |             |             |             |                  |
| 10x check | Mandatory   | Surface as  | Optional    | Skip             |
|           |             | cherry-pick |             |                  |
| Platonic  | Yes         | No          | No          | No               |
| ideal     |             |             |             |                  |
| Delight   | Opt-in      | Cherry-pick | Note if seen| Skip             |
| opps      | ceremony    | ceremony    |             |                  |
| Complexity| "Is it big  | "Is it right| "Is it too  | "Is it the bare  |
| question  |  enough?"   |  + what else|  complex?"  |  minimum?"       |
|           |             | is tempting"|             |                  |
| Taste     | Yes         | Yes         | No          | No               |
| calibrate |             |             |             |                  |
| Temporal  | Full        | Full        | Key decis.  | Skip             |
| interrog. | (hr 1-6)    | (hr 1-6)    | only        |                  |
| Observ.   | "Joy to     | "Joy to     | "Can we     | "Can we see if   |
| standard  |  operate"   |  operate"   |  debug it?" |  it's broken?"   |
| Deploy    | Infra as    | Safe deploy | Safe deploy | Simplest deploy  |
| standard  | feature     | + cherry    | + rollback  |                  |
| Error map | Full + chaos| Full + chaos| Full        | Critical paths   |
|           | scenarios   | for accepted|             | only             |
| Design    | "Inevitable"| If UI scope | If UI scope | Skip             |
| (Sec 11)  | UI review   | detected    | detected    |                  |
+-----------+-------------+-------------+-------------+------------------+
```

## When to Use Each Mode

### SCOPE EXPANSION
You are building a cathedral. The plan is good but could be great. Dream big — propose the ambitious version. Every expansion is presented individually for approval. You opt in to each one.

**Best for:** Greenfield features, new products, ambitious initiatives.

### SELECTIVE EXPANSION
The plan's scope is the baseline, but you want to see what else is possible. Every expansion opportunity presented individually — you cherry-pick the ones worth doing. Neutral recommendations.

**Best for:** Feature enhancements, iterations on existing systems.

### HOLD SCOPE
The plan's scope is right. Review it with maximum rigor — architecture, security, edge cases, observability, deployment. Make it bulletproof. No expansions surfaced.

**Best for:** Bug fixes, hotfixes, refactors, well-scoped work.

### SCOPE REDUCTION
The plan is overbuilt or wrong-headed. Propose a minimal version that achieves the core goal, then review that.

**Best for:** Plans touching 15+ files, unclear value propositions, time-constrained work.

## Expansion Framing

FLAT (avoid): "Add real-time notifications. Latency drops from ~30s polling to <500ms push. Effort: ~1 hour."

EXPANSIVE (aim for): "Imagine the moment a workflow finishes — the user sees the result instantly, no tab-switching, no polling, no 'did it actually work?' anxiety. Real-time feedback turns a tool they check into a tool that talks to them. Concrete shape: WebSocket channel + optimistic UI. Effort: ~1 hour. Makes the product feel 10x more alive."

Both are outcome-framed. Only one makes the user feel the cathedral. Lead with the felt experience, close with concrete effort and impact.

**For SELECTIVE EXPANSION:** neutral recommendation does not mean flat prose. Present vivid options, then let the user decide. Evocative, not promotional.
