---

# **LLM Prompt Playbook - Advanced RAG**

---

## **Query Rewrite for Better Retrieval**

**Goal:** Expand user queries into retrieval-friendly intents.
**Template:**

```
Given the user query:
[query]

Generate:
1) A concise canonical query.
2) 3-5 retrieval rewrites targeting:
   - synonyms
   - acronym expansions
   - time-scoped variants
   - entity-disambiguated variants
3) Must-have filters (date, region, product, source type).

Return JSON:
{
  "canonical_query": "",
  "rewrites": [],
  "filters": {}
}
```

**Notes:**

* Improves first-pass recall without changing user intent.

---

## **Reranking Prompt with Scoring**

**Goal:** Re-rank retrieved chunks by direct answer utility.
**Template:**

```
Question:
[question]

Retrieved chunks (id + text):
[chunks]

Score each chunk (0-5) on:
- relevance
- specificity
- recency
- authority

Return:
1) Ranked list with total score.
2) Top chunks selected for answering.
3) Chunks excluded and why.
```

**Notes:**

* Useful when retrieval returns noisy or duplicated context.

---

## **Cross-Document Contradiction Resolver**

**Goal:** Surface and handle conflicting evidence across sources.
**Template:**

```
Given these source passages:
[doc IDs + text]

Tasks:
1) Extract claim statements from each source.
2) Identify direct contradictions.
3) Mark each claim as {supported | contradicted | uncertain}.
4) Prioritize by source authority and timestamp.

Return:
- contradiction matrix
- reconciled answer
- unresolved conflicts with source IDs
```

**Notes:**

* Prevents silent merging of incompatible claims.

---

## **Confidence-Calibrated Final Answer**

**Goal:** Answer with explicit confidence grounded in evidence coverage.
**Template:**

```
Use the selected context to answer:
[question]

Before answering:
- Check whether all key sub-questions are covered.
- Assign confidence score 0-1 based on:
  - coverage
  - source quality
  - consistency across sources

Return:
1) Answer with citations.
2) Confidence score and short rationale.
3) Missing evidence needed to improve confidence.
```

**Notes:**

* Adds useful uncertainty signaling for downstream systems.

---
