# AI System Design

Use this reference when designing AI application architecture.

## AI Necessity

Prefer non-AI when:

- The task is deterministic.
- The data is structured and queryable.
- Rules are clear and stable.
- Users need exactness more than interpretation.
- Cost, latency, or privacy risk outweighs value.

Use AI when:

- The task requires language understanding, summarization, generation, classification, semantic matching, reasoning over messy inputs, or flexible transformation.
- The product value depends on personalization, explanation, synthesis, or natural-language interaction.

## Complexity Ladder

Start at the lowest level that solves the problem:

| Level | Pattern | Use When | Avoid When |
|---|---|---|---|
| 0 | Rules/search/SQL/templates | Logic is deterministic or data is structured | User needs interpretation or generation |
| 1 | Single LLM call | One bounded transformation or classification is enough | Needs private/current knowledge |
| 2 | LLM + selected app context | Context is small and structured | Context is large or permissioned |
| 3 | RAG | Needs private/changing knowledge with grounding | Structured query is enough |
| 4 | Tool use | AI must inspect or draft through tools | Side effects are risky or unnecessary |
| 5 | Agent loop | Multi-step plan with changing state is required | A fixed workflow works |
| 6 | Fine-tune/custom model | Repeated task, stable dataset, eval proves value | Prompting/retrieval is enough |

## Architecture Layers

- UX layer: input constraints, previews, confidence, citations, correction flow.
- API layer: auth, validation, request shaping, response contracts.
- Orchestration layer: prompt assembly, tool routing, retrieval, model calls, retries.
- Model layer: model provider, routing, fallback, structured output.
- Data layer: source documents, embeddings, permissions, logs, eval datasets.
- Evaluation layer: offline tests, online metrics, human review, regression tracking.

## Prompt Design

- Define role, task, context, constraints, output schema, and refusal behavior.
- Keep user data and system instructions separate.
- Sanitize or isolate untrusted retrieved content.
- Prefer structured outputs when downstream code depends on the result.
- Include examples only when they materially improve consistency.

## RAG Design

Use RAG when the model needs current, private, or domain-specific knowledge.

Design:

- Data sources and freshness.
- Chunking strategy.
- Embedding model.
- Vector store or search backend.
- Retrieval filters and permission checks.
- Reranking.
- Citation/grounding behavior.
- No-answer behavior when evidence is insufficient.

Avoid RAG when the answer can be computed directly from structured data.

## Agent Design

Use agents only when the task requires multi-step planning, tool use, or interaction with changing external state.

Define:

- Goal and success condition.
- Tool list and permissions.
- Planning loop and max steps.
- Memory scope.
- Human approval points.
- Failure and timeout behavior.
- Audit trail.

Avoid agents for simple question answering, one-shot extraction, or deterministic workflows.

## AI UX

- Constrain inputs where possible.
- Show progress for slow or multi-step operations.
- Distinguish generated content, retrieved evidence, and deterministic calculations.
- Let users inspect, edit, accept, reject, or retry.
- Provide safe failure states instead of silent wrong answers.
