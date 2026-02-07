---

# **LLM Prompt Playbook - Structured Output Reliability**

---

## **Strict JSON Schema Output**

**Goal:** Enforce machine-readable JSON with no extra text.
**Template:**

```
Return output as strict JSON only.
Do not include markdown, prose, or trailing commentary.

Task:
[task]

Schema:
[JSON schema or fixed JSON shape]

Rules:
- Include all required fields.
- Use null for unknown values.
- Keep enums exact.
- Dates must be ISO-8601 (YYYY-MM-DD when date-only).
- If validation would fail, return:
  {"error":"SCHEMA_VALIDATION_FAILED","details":[...]}
```

**Notes:**

* Works best with short field descriptions in the schema.

---

## **Validate-and-Repair Loop**

**Goal:** Repair structured outputs until schema-compliant.
**Template:**

```
Generate JSON for:
[task]

Schema:
[schema]

Process:
1) Draft JSON.
2) Self-validate against schema.
3) If invalid, list violations and repair.
4) Repeat up to 2 repair passes.
5) If still invalid, return explicit error object.

Return:
- final_json
- validation_report (pass/fail + violations)
```

**Notes:**

* Reduces downstream parser failures.

---

## **Deterministic Table Extraction**

**Goal:** Convert unstructured text to stable tabular output.
**Template:**

```
Extract records from the text into a table.

Text:
[text]

Columns:
[ordered column list]

Rules:
- Preserve column order exactly.
- One row per record.
- Do not infer missing values; use null.
- Keep numeric precision and currency symbols if present.

Return both:
1) CSV
2) JSON array of objects
```

**Notes:**

* Helpful when consuming LLM output in ETL pipelines.

---

## **Function Argument Normalizer**

**Goal:** Produce valid function-call arguments from messy user input.
**Template:**

```
Function name: [name]
Parameter schema:
[schema]

User input:
[text]

Task:
- Map user intent to function arguments.
- Normalize units and date/time formats.
- If required parameter missing, set to null and add missing_fields.

Return JSON:
{
  "function": "[name]",
  "arguments": {...},
  "missing_fields": [],
  "assumptions": []
}
```

**Notes:**

* Makes tool-calling more robust under ambiguous phrasing.

---
