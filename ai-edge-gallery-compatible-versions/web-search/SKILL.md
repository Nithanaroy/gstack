---
name: web-search
description: Search the web for information on any topic using DuckDuckGo and Wikipedia.
---

# Web Search

## Instructions

Call the `run_js` tool using `index.html` and a JSON string for `data` with the following fields:
- **query**: Required. The search query. Extract the key topic or entity from the user's question. Use broad terms for better results (e.g., "2026 Olympics" not "who won the 2026 Olympics 100m dash").
- **lang**: Optional. A 2-letter language code (default: "en"). Use standard codes: "en" (English), "es" (Spanish), "zh" (Chinese), "fr" (French), "de" (German), "ja" (Japanese), "ko" (Korean).

**Constraints:**
- Provide a concise summary (1-3 sentences) based on the search results. Always end with a complete sentence.
- Your response MUST be in the SAME language as the user's original prompt.
- If the exact answer isn't found, briefly state this, then share the most relevant information that was found.
- For time-sensitive queries, include the year in the search (e.g., "Olympics 2026"). Default to the current year if omitted.
