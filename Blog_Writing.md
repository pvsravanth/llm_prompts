
---

# **📘 LLM Prompt Playbook – Blog Writing**

---

## **Long-Form Blog Draft (SEO-Friendly)**

**Goal:** Produce a complete blog post with clear structure, SEO signals, and voice control.
**Template:**

```
Write a blog post about [topic] for [audience persona].

Constraints:
- Length: [word_count] words ±10%.
- Voice/Tone: [e.g., friendly, authoritative, witty]; avoid filler phrases.
- POV: [first/second/third].
- Reading level: [e.g., Grade 8/12].
- Target keywords: [list]; primary keyword: [primary_keyword]. Include primary keyword in H1 and early in intro; use naturally elsewhere.
- Formatting: H1 title, H2/H3 sections, short paragraphs (≤3 sentences), bullets where helpful.
- Include: intro hook, thesis, 3–5 key sections, practical examples, one short case/example, takeaway summary, CTA.
- Links: Add 2–3 external links to reputable sources (no placeholders); 1 internal link placeholder `[internal_link_here]`.
- Media cues: Suggest 2–3 image ideas (alt text included).

Return:
1) Title (H1) with primary keyword.
2) Meta description (≤155 chars) using primary keyword.
3) Outline (H2/H3 list).
4) Full post with markdown headings; include bullets/tables if useful.
5) CTA paragraph.
6) SEO checklist with counts: primary keyword occurrences, secondary keyword coverage, link count.
```

**Notes:**

* Keep claims specific; add simple numbers/dates when available.
* Avoid cliché openers (“In today’s world…”).
* If data is uncertain, mark it; do not invent statistics.
* Keep sentences active and concise.

---

## **Idea → Outline → Draft (Iterative)**

**Goal:** Generate a draft through checkpoints to catch issues early.
**Template:**

```
Phase 1 – Idea + Angle:
- Topic: [topic]
- Audience: [persona]
- Desired outcome: [educate/convert/entertain]
- Constraints: [word count, tone, style]
Return 3 angle options with 1–2 line pitches. Pick 1 best angle and say why.

Phase 2 – Outline:
- Produce an outline with H1/H2/H3, bullet subpoints, and where examples/stats go.
- Add keyword placement notes (primary/secondary).
- Include CTA placement.
Return outline only. Wait for approval signal "Proceed to draft".

Phase 3 – Draft:
- Write the full post per the approved outline.
- Keep paragraphs short; use bullets/tables where clarity improves.
- Add inline “(source: link)” for any external fact.
```

**Notes:**

* Use this when collaboration/approval cycles are needed.
* If approval is not given, propose a revised outline instead of drafting.

---

## **Fact Check & Polish Pass**

**Goal:** Guardrail the draft against hallucinations and tighten SEO/readability.
**Template:**

```
Given the draft:
[draft text]

Tasks:
1) Fact scan: list statements that need sources or look speculative.
2) Rewrite any speculative line to neutral language unless a source exists.
3) Check keyword usage: primary keyword [primary_keyword]; secondary [list]. Report counts and if missing.
4) Readability pass: shorten long sentences, remove filler, keep active voice.
5) Consistency: tone, POV, tense; fix any drift.
6) Return the polished draft with marked changes.
```

**Notes:**

* If stats lack sources, either add a plausible reputable source placeholder or rephrase as directional (e.g., “many”, “most”).
* Keep meta description unchanged unless it exceeds 155 chars.

---

## **Repurposing / Condensation**

**Goal:** Create derivative assets from the blog.
**Template:**

```
Repurpose the blog into:
- 3 social posts (platform: [X/LinkedIn], 220–260 chars; include 1–2 hashtags max).
- 1 email teaser (60–80 words) with subject line options (3 variants).
- 1 TL;DR bullet list (5 bullets max) for the top of the post.
Maintain original tone; no new claims; keep any numbers consistent.
```

**Notes:**

* Avoid clickbait; keep promises aligned with the blog content.

---
