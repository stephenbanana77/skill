# Agent Skill Library

A small, opinionated skill library for building better software and AI products with Codex-style agents.

These skills are designed for one purpose: make an agent think like a strong engineer before it writes code. They emphasize scope, tradeoffs, evaluation, safety, and production readiness instead of quick demos.

## Skills

### `engineering-thinking`

Staff Engineer style software design before implementation.

Use it when you want an agent to:

- clarify requirements and non-goals
- identify system boundaries
- design architecture and APIs
- reason about data, risks, migrations, and validation
- avoid over-engineering small changes
- record important technical decisions

Best prompts:

```text
Use engineering-thinking to design this feature before coding.
```

```text
Use engineering-thinking to review this architecture and identify the risky decisions.
```

### `ai-product-engineer`

Principal AI Engineer style product and system design for AI features.

Use it when you want an agent to:

- decide whether AI is actually needed
- choose the lowest viable AI complexity
- design LLM, RAG, tool-use, or agent architecture
- define evaluation metrics and release gates
- control latency and cost
- handle prompt injection, privacy, and tool permissions

Best prompts:

```text
Use ai-product-engineer to decide how this AI feature should work.
```

```text
Use ai-product-engineer to review this RAG/agent design for production risks.
```

## Design Principles

- Prefer simple deterministic software before AI.
- Prefer a single bounded LLM call before RAG.
- Prefer fixed tool workflows before autonomous agents.
- Treat evaluation as part of the product.
- Match design depth to risk: tiny changes should not become ceremony.
- Make important engineering decisions explicit and reviewable.

## Repository Structure

```text
skills/
├── engineering-thinking/
│   ├── SKILL.md
│   └── references/
│       ├── decision_records.md
│       ├── engineering_checklist.md
│       ├── examples.md
│       └── patterns.md
└── ai-product-engineer/
    ├── SKILL.md
    └── references/
        ├── ai_system_design.md
        ├── cost_performance.md
        ├── evaluation_framework.md
        ├── examples.md
        └── safety_and_permissions.md
```

## Install

Clone the repository:

```bash
git clone https://github.com/stephenbanana77/skill.git
```

Copy the skills into your Codex skills directory:

```bash
cp -R skill/skills/* "$CODEX_HOME/skills/"
```

On Windows PowerShell:

```powershell
Copy-Item -Recurse -Force .\skill\skills\* "$env:CODEX_HOME\skills\"
```

If `CODEX_HOME` is not set, use your local Codex skills directory.

## Example Workflow

For a normal software feature:

```text
Use engineering-thinking to plan a multi-tenant invitation system.
```

For an AI product feature:

```text
Use ai-product-engineer to design an AI knowledge base assistant with citations and cost controls.
```

For a combined workflow:

```text
First use ai-product-engineer to decide whether the feature needs AI.
Then use engineering-thinking to design the system implementation.
```

## Why This Exists

Most AI coding workflows fail for boring reasons:

- vague requirements
- unclear boundaries
- accidental complexity
- missing tests
- unmeasured AI quality
- expensive or unsafe AI architecture

This library turns those concerns into reusable agent behavior.
