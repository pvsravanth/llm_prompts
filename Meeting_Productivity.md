---

# **LLM Prompt Playbook - Meeting and Productivity**

---

## **Transcript to Action Items**

**Goal:** Turn meeting notes/transcript into accountable tasks.
**Template:**

```
Convert this meeting transcript into action items:
[transcript]

For each action item, extract:
- owner
- task
- due date
- priority (high/medium/low)
- dependencies

Rules:
- If owner or due date missing, mark as "TBD".
- Merge duplicates.
- Keep wording short and executable.

Return:
1) Action-item table
2) Unassigned items list
3) Risks/blockers mentioned
```

**Notes:**

* Best used with full transcript instead of summaries.

---

## **Decision Log Extractor**

**Goal:** Capture decisions with context and rationale.
**Template:**

```
From these notes, extract decisions:
[notes]

For each decision:
- decision statement
- options considered
- rationale
- decision owner
- decision date
- revisit trigger/date

Return:
1) Decision log table
2) Open decisions not finalized
```

**Notes:**

* Helps avoid repeated debates in recurring meetings.

---

## **Follow-Up Email Draft**

**Goal:** Draft concise follow-up communication after meetings.
**Template:**

```
Write a follow-up email based on:
- Meeting topic: [topic]
- Participants: [list]
- Key outcomes: [list]
- Action items: [list]

Constraints:
- Tone: [formal/friendly]
- Length: <= [N] words
- Include clear next checkpoint date

Return:
1) Email subject (3 options)
2) Email body
```

**Notes:**

* Keep commitments explicit and date-bound.

---

## **Weekly Status Digest**

**Goal:** Build a compact status report from scattered updates.
**Template:**

```
Create a weekly status digest from:
[updates]

Structure:
- Wins
- In-progress work
- Risks/blockers
- Metrics
- Next week priorities

Rules:
- Keep to <= 250 words.
- Use bullets only.
- Include asks/decisions needed from leadership.
```

**Notes:**

* Useful for team leads and project managers.

---
