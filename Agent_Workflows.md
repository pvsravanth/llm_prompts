---

# **LLM Prompt Playbook - Agent Workflows**

---

## **Planner -> Executor -> Critic Loop**

**Goal:** Run multi-step tasks with explicit quality control before final output.
**Template:**

```
You are an execution agent. Use a 3-phase loop:

Phase 1 - Planner:
- Restate the objective in one sentence.
- Break work into 3-7 steps with dependencies.
- Mark each step as {must-have | nice-to-have}.
- Define "done" criteria for each must-have step.

Phase 2 - Executor:
- Execute steps in order.
- After each step, output:
  - step_id
  - result
  - evidence (command/file/source)
  - blockers (if any)

Phase 3 - Critic:
- Check results against done criteria.
- List defects or missing evidence.
- If defects exist, fix and re-run Critic once.

Return:
1) Final deliverable.
2) Completed checklist mapped to done criteria.
3) Residual risks.
```

**Notes:**

* Good default for coding, analysis, and operations tasks.
* Keeps a clear audit trail for each step.

---

## **Task Decomposition with Stop Criteria**

**Goal:** Prevent infinite loops and over-execution.
**Template:**

```
Decompose this task:
[task]

Rules:
- Create atomic steps that can be verified.
- Set explicit stop criteria:
  - max_steps: [N]
  - max_retries_per_step: [N]
  - max_time_minutes: [N]
- Define handoff triggers to ask for user input.

For each step, return:
- objective
- inputs
- action
- expected output
- validation check
- fallback if validation fails
```

**Notes:**

* Use when requirements are broad or ambiguous.
* Helps contain cost and latency.

---

## **Blocked-State Escalation Prompt**

**Goal:** Escalate only when blocked, with concrete options.
**Template:**

```
If blocked, do not stop silently. Return:

1) Blocker summary (one line).
2) What was attempted (max 3 bullets).
3) Why the blocker is real (evidence).
4) Three options:
   - Option A: lowest risk
   - Option B: fastest path
   - Option C: highest quality
5) Recommended option with trade-off.
6) Exact input needed from user to continue.

If not blocked, continue execution without escalation.
```

**Notes:**

* Keeps momentum and removes vague "cannot proceed" responses.

---
