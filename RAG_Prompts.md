
---

# **📘 LLM Prompt Playbook – Retrieval-Augmented Generation**

---

## **Grounded Answer with Citations**

**Goal:** Answer strictly from provided context, citing sources and surfacing uncertainty.
**Template:**

```
You are a RAG system. Use ONLY the provided context to answer.

Context:
[paste passages with identifiers, e.g., [doc1], [doc2]]

Task:
1) Restate the user question in one line.
2) Extract relevant snippets (quote minimally) and map them to their doc IDs.
3) Answer in 2–4 sentences, citing sources inline like [doc1].
4) Add a “Gaps/Uncertainty” bullet if the context is insufficient.

Rules:
- No outside knowledge. If unsure, say “Not in context”.
- Do not merge conflicting facts; call out conflicts explicitly.
- Keep citations close to the claims they support.
```

**Notes:**

* If multiple passages overlap, prefer the most recent or most explicit.
* For numerical answers, compute from the provided values and show the math briefly.

---

## **Context Selection & Coverage Check**

**Goal:** Validate that retrieved chunks are enough and identify what’s missing.
**Template:**

```
Given the query:
[user query]

And retrieved chunks (ID + text):
[chunk list]

Do:
1) List key sub-questions implicit in the query.
2) For each sub-question, mark coverage as {Fully covered | Partially | Missing} and cite the chunk IDs that help.
3) Recommend additional retrieval intents/keywords for missing pieces.
4) If coverage is partial or missing, return a safe fallback answer: “Insufficient context to answer fully.”
```

**Notes:**

* Helps debug RAG recall vs. generation issues.
* Keep recommendations short and actionable.

---

## **Structured RAG Output (Tables/JSON)**

**Goal:** Return grounded, structured answers with provenance for each field.
**Template:**

```
Using only the context below, fill the JSON schema. Include the source doc ID for every field.

Context:
[docs with IDs]

Schema:
{
  "entity": {"value": "", "source": ""},
  "metric": {"value": "", "source": ""},
  "date": {"value": "", "source": ""},
  "notes": {"value": "", "source": ""}
}

Rules:
- If a field is missing, set value to null and source to "not found".
- No hallucinations; copy phrasing when in doubt.
```

**Notes:**

* Works well for compliance or audit trails where provenance is mandatory.

---
