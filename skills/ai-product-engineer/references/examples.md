# AI Product Engineer Examples

## Example: AI Resume Optimizer

AI necessity:

- AI is useful for semantic critique and rewrite suggestions.
- Deterministic checks can handle spelling, length, missing sections, and formatting.
- Use a hybrid design.

Architecture:

- Upload/parser extracts text.
- Deterministic validator checks structure.
- LLM scores and suggests improvements with a structured schema.
- Evaluation uses golden resumes and recruiter-style rubric.

Risks:

- Privacy: resumes contain personal data.
- Hallucination: AI may invent experience.
- UX: suggestions must be editable, not auto-applied blindly.

## Example: AI Knowledge Base Assistant

AI necessity:

- AI is useful for natural-language answers over private docs.
- RAG is needed because knowledge is private and changing.

Architecture:

- Ingest docs with permissions.
- Chunk and embed.
- Retrieve with workspace filters.
- Rerank and answer with citations.
- Refuse when evidence is insufficient.

Evaluation:

- Grounded answer rate.
- Citation correctness.
- No-answer correctness.
- p95 latency and cost per answer.

## Example: AI Agent Automation

Use an agent only if the workflow needs multiple tools and branching decisions.

Design:

- Goal: complete a bounded user-approved task.
- Tools: explicitly listed and permissioned.
- Loop: max steps and timeout.
- Memory: task-local unless user approves persistence.
- Human approval: before external side effects.
- Audit: log tool calls and decisions.
