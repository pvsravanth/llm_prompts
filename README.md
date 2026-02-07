# llm_prompts
A repo of useful prompts:

- Trading playbook with technical-analysis master prompt (`Trading.md`)
- Coding/development prompt templates (`Python_Coding.md`)
- FastAPI production skeleton generator (`FastAPI_Prompt.md`)
- Chain-of-density summary prompts (`Chain_of_Density.md`)
- Retrieval-augmented generation prompts (`RAG_Prompts.md`)
- Advanced RAG prompts for query rewriting, reranking, and contradiction handling (`RAG_Advanced.md`)
- Image-to-text captioning and extraction prompts (`Image_to_Text.md`)
- Blog writing templates for SEO-friendly drafting and polishing (`Blog_Writing.md`)
- Advanced blog operations prompts: briefs, clusters, E-E-A-T, refresh strategy (`Blog_Advanced.md`)
- Prompt evaluation prompts: rubric scoring, A/B testing, failure taxonomy, regression suites (`Prompt_Evaluation.md`)
- Safety and guardrail prompts: refusal strategy, PII redaction, injection resistance (`Safety_Guardrails.md`)
- Structured output reliability prompts for strict JSON and validation-repair loops (`Structured_Output.md`)
- Tool-calling prompts for planning, argument extraction, orchestration, and synthesis (`Tool_Calling.md`)
- Debugging prompts: root-cause analysis, MRE creation, test-first bug fixing (`Debugging_Prompts.md`)
- SQL and data prompts: SQL generation, optimization, data quality audits, narrative provenance (`SQL_Data_Prompts.md`)
- Meeting and productivity prompts: action extraction, decision logs, follow-up drafts (`Meeting_Productivity.md`)
- Agent workflow prompts: planner-executor-critic loops and blocked-state escalation (`Agent_Workflows.md`)

Prompty templates (`.prompty`):

- Grounded RAG answer template with strict JSON output contract (`prompty/rag_grounded_answer.prompty`)
- Code review template with severity-ranked findings and remediation (`prompty/code_review_guardrails.prompty`)
- SEO content brief template with typed inputs and structured outline output (`prompty/seo_content_brief.prompty`)
- Tool orchestration planner with dependency and fallback modeling (`prompty/tool_orchestrator.prompty`)

## Starter Map

Start here based on your task:

- Writing Python/code quickly: `Python_Coding.md`
- Building a production FastAPI starter: `FastAPI_Prompt.md`
- Debugging failures and shipping safer fixes: `Debugging_Prompts.md`
- Designing/evaluating prompts before production: `Prompt_Evaluation.md`
- Running ready-to-use `.prompty` templates: `prompty/*.prompty`
- Enforcing JSON/schema-safe outputs: `Structured_Output.md`
- Building tool-using agents: `Tool_Calling.md`
- Running complex tasks with execution loops: `Agent_Workflows.md`
- Building grounded RAG answers: `RAG_Prompts.md`
- Improving retrieval quality and contradiction handling: `RAG_Advanced.md`
- Extracting structured text from images/PDFs: `Image_to_Text.md`
- Writing SEO blogs end-to-end: `Blog_Writing.md`
- Planning content briefs/clusters and refreshes: `Blog_Advanced.md`
- Generating trading analysis and trade plans: `Trading.md`
- Working with SQL/data quality/reporting: `SQL_Data_Prompts.md`
- Converting meetings into action/decision outputs: `Meeting_Productivity.md`
- Compressing long docs into dense summaries: `Chain_of_Density.md`
