---

# **LLM Prompt Playbook - Advanced Blog Ops**

---

## **Content Brief Generator**

**Goal:** Create a production-ready brief before drafting.
**Template:**

```
Create a content brief for:
- Topic: [topic]
- Audience: [persona]
- Funnel stage: [TOFU/MOFU/BOFU]
- Goal: [traffic/leads/education]

Include:
- search intent
- target keyword + 5 supporting keywords
- angle and differentiation
- outline (H1/H2/H3)
- evidence needed (stats/case studies)
- CTA recommendation

Return:
1) Brief summary
2) Structured brief table
3) "Do not include" list to avoid scope creep
```

**Notes:**

* Helps maintain consistency across multiple writers.

---

## **Topic Cluster Planner**

**Goal:** Build internal-linkable content clusters around a pillar page.
**Template:**

```
Design a topic cluster for:
- Pillar topic: [topic]
- Audience: [persona]
- Region/language: [region]

Return:
1) Pillar page title and thesis.
2) 8-12 cluster article ideas grouped by intent.
3) Internal linking map:
   - pillar -> cluster links
   - cluster -> pillar links
   - sibling links where relevant
4) Publishing priority (high/medium/low) with reason.
```

**Notes:**

* Useful for SEO programs, not just one-off posts.

---

## **E-E-A-T Compliance Pass**

**Goal:** Improve trust signals in draft content.
**Template:**

```
Review this draft for E-E-A-T:
[draft]

Assess:
- Experience signals
- Expertise signals
- Authoritativeness signals
- Trustworthiness signals

For each dimension:
1) Current score (1-5)
2) Missing elements
3) Concrete edits to improve score

Return:
- Annotated improvement plan
- Revised intro and conclusion with stronger trust cues
```

**Notes:**

* Keep claims tied to verifiable sources.

---

## **SERP Differentiation and Refresh Prompt**

**Goal:** Prevent generic content and improve ranking competitiveness.
**Template:**

```
Given:
- Existing draft: [draft]
- Top competitor summaries: [summaries]

Tasks:
1) Identify overlap with competitors.
2) Identify missing unique value in our draft.
3) Propose 5 differentiation upgrades:
   - original framework/checklist
   - practical examples
   - decision table
   - counterintuitive insight
   - updated data angle
4) Rewrite the outline to include those upgrades.
```

**Notes:**

* Use in refresh cycles for aging content.

---
