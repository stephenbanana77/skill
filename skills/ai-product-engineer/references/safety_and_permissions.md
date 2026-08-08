# AI Safety And Permissions

Use this reference when an AI feature handles private data, untrusted content, tool use, external actions, or generated recommendations that affect users.

## Threat Model

Check:

- Untrusted user input.
- Untrusted retrieved documents.
- Prompt injection in web pages, files, emails, tickets, or documents.
- Cross-user or cross-tenant data leakage.
- Tool calls that send messages, spend money, delete data, change settings, or publish content.
- Model outputs that users may over-trust.

## Prompt Injection Defenses

- Keep system instructions separate from user and retrieved content.
- Treat retrieved text as data, not instructions.
- Strip, quote, or sandbox untrusted content when possible.
- Require citations or evidence for factual claims.
- Refuse or ask for confirmation when instructions conflict with user intent or system policy.

## Tool Permission Design

Classify tools:

- Read-only: search, fetch, summarize, inspect.
- Draft-only: prepare email, create proposal, generate patch.
- Reversible write: create issue, update draft, add comment.
- Irreversible or high-impact: send, delete, purchase, deploy, change permissions.

Rules:

- Prefer draft-only before write actions.
- Require human approval for irreversible or external side effects.
- Give agents the narrowest tool set needed.
- Log tool calls and final decisions.
- Set max steps, timeouts, and stop conditions for any agent loop.

## Privacy And Data Handling

- Minimize data sent to model providers.
- Avoid logging raw secrets, credentials, private documents, or personal data.
- Respect tenant/user boundaries during retrieval.
- Define retention for prompts, outputs, embeddings, and logs.
- Provide deletion or re-indexing strategy when source data changes.

## User Trust

- Show uncertainty when evidence is weak.
- Make AI suggestions editable.
- Do not auto-apply risky recommendations.
- Provide citations or source snippets when decisions depend on retrieved content.
- Offer a fallback path when AI is unavailable.
