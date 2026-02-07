---

# **LLM Prompt Playbook - Prompt Evaluation**

---

## **Prompt Quality Rubric (Scored)**

**Goal:** Evaluate prompt quality with a repeatable scoring model.
**Template:**

```
Evaluate this prompt:
[prompt text]

Score each category from 1-5:
1) Objective clarity
2) Input completeness
3) Output specificity
4) Constraint quality (scope, style, safety)
5) Verifiability (can output be checked?)
6) Robustness to ambiguity

Return:
- Table: category, score, rationale (1 sentence each)
- Total score out of 30
- Top 3 weaknesses
- Revised prompt that fixes those weaknesses
```

**Notes:**

* Use this before productionizing any prompt.
* Keep rationales short and concrete.

---

## **A/B Prompt Comparison**

**Goal:** Pick the better of two prompts for a fixed task.
**Template:**

```
Task:
[task definition]

Prompt A:
[prompt A]

Prompt B:
[prompt B]

Evaluation method:
- Run both prompts against the same input(s): [test set]
- Compare on:
  - correctness
  - completeness
  - format compliance
  - hallucination risk
  - token efficiency

Return:
1) Side-by-side score table.
2) Winner by criterion.
3) Final winner with reason.
4) Hybrid prompt that combines best parts.
```

**Notes:**

* Use at least 3 representative test inputs for stable results.

---

## **Failure Taxonomy and Fix Plan**

**Goal:** Convert prompt failures into targeted improvements.
**Template:**

```
Given:
- Prompt: [prompt]
- Failures observed: [examples]

Classify each failure as one of:
- missing constraint
- ambiguous instruction
- weak grounding
- schema mismatch
- reasoning gap
- safety gap

For each failure:
1) Root cause
2) Minimal prompt edit
3) Expected behavior change
4) Validation test

Return a patched prompt and a short regression test list.
```

**Notes:**

* Prefer small edits over full rewrites when possible.

---

## **Prompt Regression Test Suite**

**Goal:** Keep prompt behavior stable across revisions.
**Template:**

```
Create a regression suite for this prompt:
[prompt]

Include:
- 5 normal cases
- 3 edge cases
- 3 adversarial/ambiguous cases

For each case:
- input
- expected output properties
- hard constraints (must include / must not include)
- pass/fail check

Return:
1) Test matrix.
2) Criteria for release readiness.
```

**Notes:**

* Define properties, not exact wording, unless output must be deterministic.

---
