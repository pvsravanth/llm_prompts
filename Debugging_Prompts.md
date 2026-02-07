---

# **LLM Prompt Playbook - Debugging**

---

## **Root Cause Analysis from Error Logs**

**Goal:** Identify likely root causes with evidence, not guesses.
**Template:**

```
Analyze this failure:

Context:
[system/app context]

Error logs:
[logs]

Recent changes:
[commits/config/deploy changes]

Return:
1) Top 3 root-cause hypotheses ranked by likelihood.
2) Evidence for and against each.
3) Fastest validation step for each hypothesis.
4) Recommended next action.
```

**Notes:**

* Require evidence for every hypothesis to reduce random fixes.

---

## **Minimal Reproducible Example Generator**

**Goal:** Distill a bug into the smallest reproducible case.
**Template:**

```
Given this bug report:
[report]

Create a minimal reproducible example (MRE).

Requirements:
- Keep only code necessary to trigger the bug.
- Include exact input data and environment assumptions.
- Provide expected vs actual behavior.
- Add run commands.

Return:
1) MRE code
2) Repro steps
3) Why each retained component is necessary
```

**Notes:**

* Great for faster issue triage and bug handoff.

---

## **Test-First Bug Fix**

**Goal:** Fix bug with a failing test first, then patch.
**Template:**

```
Task: fix this bug with test-first workflow.

Bug:
[description]

Code:
[snippet/repo context]

Process:
1) Write a failing test that reproduces bug.
2) Explain why test fails.
3) Implement minimal fix.
4) Show updated test now passing.
5) Check for regressions nearby.

Return:
- test code
- patch
- brief rationale
```

**Notes:**

* Keeps fixes focused and prevents silent behavior drift.

---

## **Regression Guard Checklist**

**Goal:** Ensure a fix does not break adjacent behavior.
**Template:**

```
For this patch:
[patch]

Create a regression guard checklist covering:
- input boundary cases
- null/empty handling
- concurrency/state risks
- performance implications
- backward compatibility
- logging/observability

Return:
1) Checklist with pass/fail status.
2) Missing tests to add.
3) Residual risk summary.
```

**Notes:**

* Use before merge for critical code paths.

---
