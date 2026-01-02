

# **📘 LLM Prompt Playbook – Image to Text (PDF & Structured Layout)**

---

## **Page-to-Text with Layout Preservation**

**Goal:** Extract page images (PDF scans, slides, docs) into structured text while preserving hierarchy, tables, code, and diagrams.
**Template:**

```
You are converting page images to structured text. Follow strict fidelity rules.

Inputs:
- Page image(s) with page number. If multiple, process in order.

Output format (in order):
1) Page metadata:
   - page_number
   - orientation (portrait/landscape/unknown)
   - quality: {clear | mild blur | severe blur | partial crop | glare}
2) Heading hierarchy:
   - List headings with levels (H1/H2/H3), exact text, and order of appearance.
3) Body blocks:
   - Ordered paragraphs/lists. Preserve bullets/numbering. Do not merge paragraphs.
4) Tables:
   - For each table: title/caption if present; row x column counts; header rows; merged cells noted.
   - Recreate as Markdown table AND as JSON with rows of cells. Keep cell text verbatim, including units/footnotes.
   - If numeric columns, keep signs, decimals, currency symbols.
5) Figures/graphs/charts:
   - Describe chart type, axes labels/units, legends, and any visible numbers.
   - Transcribe text in the chart (titles, labels, annotations). If data points are readable, list them.
6) Flowcharts/diagrams:
   - Convert to mermaid `flowchart TD` with nodes and labeled edges based on visible text. If unclear, describe in prose and mark nodes as "unclear".
7) Code blocks:
   - Transcribe exactly with indentation in fenced code blocks. Infer language only if explicitly shown; else use ```text```.
8) Captions/footnotes/callouts:
   - Capture verbatim and link to the referenced table/figure if obvious.
9) Unreadable/uncertain:
   - List any unreadable areas and why (blur, cut off). Use "unknown" rather than guessing.

Guardrails:
- No hallucinations. Do not add data not visible. If a value is cut off, mark as "truncated".
- Maintain page order; do not reorder elements.
- Preserve casing, symbols, and formatting (e.g., ALL CAPS headings stay uppercase).
- If the page has no content for a section (e.g., no tables), state "None".

Self-check (perform before finalizing):
- Verify table row/column counts match the recreated table.
- Check numbered lists are sequential; note if numbering is broken in source.
- Confirm all visible headings appear in output and in correct order.
- Ensure every figure/chart has axes/legend info if present; if missing in source, say "not shown".
- Re-scan for any text in images (labels, axis text, small print) and add if missed.
```

**Notes:**

* Works for scanned PDFs, slide decks, receipts, forms, and handwritten mixes.
* For multipage PDFs, repeat the output format per page and keep a running page_number.

---

## **High-Fidelity Table Reconstruction**

**Goal:** Recreate tables with exact content, structure, and units; avoid silent normalization.
**Template:**

```
Recreate every table on the page with fidelity.

For each table:
- Report: title/caption (or "untitled"), row_count, column_count, header_rows, merged_cells (list coordinates or "none").
- Output 1: Markdown table preserving column order and header rows.
- Output 2: JSON:
  {
    "title": "",
    "rows": [
      [{"text": "cell text", "rowspan": 1, "colspan": 1}],
      ...
    ]
  }

Rules:
- Keep original symbols (%, $, €, ±), thousand separators, superscripts if shown (use ^ in text).
- If a cell spans rows/cols, note exact spans. If spans unclear, set "rowspan": null or "colspan": null and flag "uncertain": true.
- Do not round or reformat numbers. Preserve leading zeros.
- If a column has mixed types (text + numbers), keep as-is and do not coerce.
- If any cell is unreadable, set text: "unreadable", add reason in a "notes" array for the table.

QA check per table:
- Confirm header rows are included.
- Count rows/columns after spans; ensure counts match source.
- Re-read tiny footnotes inside cells and include them inline.
```

**Notes:**

* Use this as a sub-prompt when tables are dense or critical.

---

## **Diagram / Flow / Code Extraction**

**Goal:** Capture diagrams, flows, and code blocks with structure and provenance.
**Template:**

```
For diagrams and flowcharts:
- Identify nodes (box text) and connectors (arrows). If direction unclear, assume left-to-right and mark "direction_unconfirmed".
- Output mermaid `flowchart TD` plus a node/edge list:
  nodes: [{"id": "A", "text": "..."}], edges: [{"from": "A", "to": "B", "label": "via API"}]
- Note swimlanes or groupings if visible.

For graphs/charts:
- Specify chart type (bar/line/pie/etc.).
- Transcribe: title, subtitle, axis labels + units, legend entries, any visible data labels.
- If numeric values are visible, list them with their category; if approximated, mark "approx".
- State what is missing if axes or legends are absent.

For code:
- Copy exactly into fenced code blocks. Preserve indentation, spacing, and comments.
- If language is stated, use it in the fence. If not, use ```text.
- If line numbers are visible, include them as inline comments (e.g., "# line 12").

Guardrails:
- No inferred arrows, nodes, or code not clearly visible.
- If part of a diagram is cut off, describe what is missing instead of guessing.
```

**Notes:**

* Useful for technical PDFs where architecture diagrams and snippets appear alongside text.
