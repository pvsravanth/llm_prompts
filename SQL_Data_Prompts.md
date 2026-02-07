---

# **LLM Prompt Playbook - SQL and Data**

---

## **SQL Generation with Assumptions**

**Goal:** Generate correct SQL with explicit assumptions and safety checks.
**Template:**

```
Generate SQL for this analytics question:
[question]

Schema:
[tables, columns, keys]

Requirements:
- SQL dialect: [Postgres/MySQL/BigQuery/etc.]
- Time range: [range]
- Grain: [daily/weekly/user-level/etc.]

Return:
1) SQL query
2) Assumptions made
3) Validation checks (row-count sanity, null checks)
4) Possible edge cases
```

**Notes:**

* Ask for missing schema details instead of guessing field names.

---

## **SQL Query Optimization Pass**

**Goal:** Improve runtime and cost without changing query meaning.
**Template:**

```
Optimize this SQL query:
[query]

Schema + indexes/partitions:
[details]

Tasks:
- Identify bottlenecks.
- Rewrite for better performance.
- Suggest index/partition improvements.
- Explain trade-offs.

Return:
1) Optimized SQL
2) Before vs after reasoning
3) EXPLAIN-plan checkpoints to verify improvement
```

**Notes:**

* Keep result semantics identical unless asked otherwise.

---

## **Data Quality Audit Prompt**

**Goal:** Assess dataset trustworthiness before modeling/reporting.
**Template:**

```
Audit this dataset:
[table description]

Check:
- completeness (missingness by column)
- uniqueness (primary key violations)
- validity (type/range/format)
- consistency (cross-field rules)
- timeliness (data freshness)

Return:
1) Audit report with severity levels
2) SQL checks for each issue
3) Remediation plan ordered by impact
```

**Notes:**

* Useful before dashboards or ML training.

---

## **Narrative with SQL Provenance**

**Goal:** Produce an executive summary tied directly to query outputs.
**Template:**

```
Given query outputs:
[tables/results]

Write:
- 5-bullet executive summary
- 3 actionable recommendations

Rules:
- Every claim must cite supporting metric/result ID.
- No causal claims unless explicitly supported.
- Separate observations from recommendations.

Return:
1) Summary
2) Recommendation list
3) Claim-to-metric mapping table
```

**Notes:**

* Prevents unsupported narratives in reporting.

---
