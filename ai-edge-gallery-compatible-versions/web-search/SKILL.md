---
name: web-search
description: |
  Search the web using DuckDuckGo. Returns summarized results for landscape
  awareness, competitive research, and search-before-building checks.
  Used by other skills when they need to understand what the world thinks
  about a problem space.
---

# Web Search

Search the web for information relevant to the current conversation.

## When to Use

- Landscape awareness: understanding what exists in a problem space
- Search before building: checking if a built-in or standard solution exists
- Competitive research: understanding conventional wisdom
- Fact-checking: verifying claims about markets, technologies, or trends

## How to Use

Call `run_js` with the `scripts/index.html` script. Pass a search query as the input.

**Privacy rule:** When searching on behalf of a user's idea, use **generalized category
terms** — never the user's specific product name, proprietary concept, or stealth idea.

Example: search "task management app landscape 2026" not "SuperTodo AI-powered task killer"

## Interpreting Results

After receiving search results, synthesize using the three-layer framework:

- **Layer 1 (Tried-and-true):** What does everyone already know about this space?
- **Layer 2 (Current discourse):** What are the search results saying right now?
- **Layer 3 (First principles):** Given what you know, is there a reason the conventional approach is wrong?

If Layer 3 reasoning reveals a genuine insight, name it:
"EUREKA: Everyone does X because they assume [assumption]. But [evidence] suggests
that's wrong here. This means [implication]."
