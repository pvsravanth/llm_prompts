---

# **LLM Prompt Playbook - Tool Calling**

---

## **Tool Selection Planner**

**Goal:** Choose the right tool(s) and sequence with clear rationale.
**Template:**

```
You can use these tools:
[tool list with capability summaries]

Task:
[user task]

Plan:
1) Determine if tools are needed or answer can be direct.
2) If tools are needed, choose minimal set.
3) Order calls by dependency and cost.
4) Define success checks per call.

Return:
- selected_tools
- call_order
- expected_output_per_call
- failure_fallback
```

**Notes:**

* Prevents unnecessary tool calls and cost spikes.

---

## **Argument Extraction for Tool Calls**

**Goal:** Build valid, complete call arguments from user language.
**Template:**

```
Tool schema:
[parameters, types, required fields]

User request:
[request]

Extract:
- required args
- optional args when clearly implied
- defaults used

Rules:
- Do not invent values not supported by user input.
- Put uncertain values into "clarifications_needed".

Return JSON:
{
  "arguments": {...},
  "defaults_used": {...},
  "clarifications_needed": []
}
```

**Notes:**

* Works well before function-calling in production agents.

---

## **Multi-Tool Orchestration with Dependencies**

**Goal:** Coordinate multiple tools without losing state or provenance.
**Template:**

```
Orchestrate this task with tools:
[task + tools]

Execution rules:
- Parallelize independent calls.
- Run dependent calls sequentially.
- After each call, store:
  - tool_name
  - input
  - output summary
  - confidence
- If a call fails, retry once with corrected args.
- If still failing, use fallback plan.

Return:
1) Execution log
2) Final result
3) Source mapping from result claims to tool outputs
```

**Notes:**

* Keeps final answers auditable and debuggable.

---

## **Tool Result Synthesis**

**Goal:** Merge tool outputs into one coherent user answer.
**Template:**

```
Inputs:
- Tool outputs with identifiers
- User question

Synthesis rules:
- Resolve contradictions explicitly.
- Prioritize most recent and most authoritative source.
- Keep each claim linked to a tool output ID.
- If unresolved conflict remains, state uncertainty.

Return:
1) Direct answer
2) Supporting evidence list
3) Open gaps and next best tool call (if needed)
```

**Notes:**

* Prevents overconfident summaries across inconsistent tool data.

---
