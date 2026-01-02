
---

# **📘 LLM Prompt Playbook – Chain-of-Density Summaries**

---

## **Condensed-then-Dense Summary**

**Goal:** Produce a concise summary that keeps adding specifics without growing the token budget.
**Template:**

```
Summarise the following content using a chain-of-density approach.

Steps:
1) Draft a terse synopsis in ≤3 bullets (≤12 words each). No numbers or names yet.
2) Iteration A: Add the most critical proper nouns, dates, and figures while keeping bullet count and length the same.
3) Iteration B: Replace generic phrases with concrete details (who, what, where, when). Keep length stable.
4) Final: Output a single paragraph (3–4 sentences) that is denser than the bullets but still readable.

Rules:
- Do not invent facts.
- If a detail is missing, say “detail not provided”.
- Prefer absolute numbers over adjectives; include percentages if present.
```

**Notes:**

* Works best when source text is ≥3 paragraphs.
* If input is already short, skip iterations and go straight to the final dense paragraph.
* Maintain consistency across iterations (do not drop previously added critical facts).

---

## **Iterative Compression with Limits**

**Goal:** Hit a strict token/word limit while preserving coverage of key entities and events.
**Template:**

```
Summarise the text in ≤[word_limit] words using iterative compression.

Process:
1) Extract a fact list: {actors, actions, outcomes, metrics, timelines}.
2) Rank facts by impact on the main claim (High/Med/Low).
3) Draft a summary using only High + Med facts; stay under the word limit.
4) If over limit, remove lowest-impact adjectives first; if still over, remove lowest-ranked facts.

Return:
- Final summary (≤[word_limit] words).
- Bullet list of omitted facts (if any) with reasons.
```

**Notes:**

* Use explicit counts and dates where given.
* Keep causal links intact (“because”, “therefore”, “driven by”).

---
