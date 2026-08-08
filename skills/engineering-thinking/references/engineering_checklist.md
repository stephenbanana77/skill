# Engineering Checklist

Use this checklist for design, implementation planning, refactoring, and architecture review.

## Requirement Analysis

- What user or system goal is being served?
- What is explicitly out of scope?
- What inputs, outputs, and side effects exist?
- What data must be persisted, derived, cached, or discarded?
- What future change is likely, and what future change is speculative?

## Boundary Design

- Frontend: UI state, interaction, validation, loading/error states.
- Backend/API: contracts, auth, validation, orchestration, business rules.
- Domain: core concepts, invariants, lifecycle, ownership.
- Data: schema, migrations, query patterns, consistency.
- External systems: LLMs, payments, email, storage, queues, webhooks.
- Infrastructure: config, health, deploy, secrets, observability.

## Architecture

- What components are necessary?
- Which component owns each responsibility?
- What interfaces connect them?
- What can fail independently?
- What should be synchronous vs asynchronous?
- What should be configured vs hardcoded?

## Risk Review

- Security: auth, authorization, injection, secrets, sensitive data.
- Correctness: edge cases, null/empty inputs, concurrency, idempotency.
- Performance: unbounded loops, N+1 queries, large payloads, blocking work.
- Operability: logs, metrics, health checks, retries, rollback.
- Compatibility: migrations, API contracts, old clients, config defaults.
- Testing: unit, integration, e2e, regression, fixtures.

## Implementation Readiness

Ready to implement when:

- The core user/system goal is clear.
- Interfaces and ownership are clear enough.
- High-risk failure modes have mitigations.
- Validation commands or manual checks are known.

If any of these are missing, either ask one focused question or proceed with an explicitly labeled assumption.

## Complexity Triggers

Increase design depth when the change includes:

- Public API or database schema changes.
- Auth, permissions, billing, payments, secrets, or sensitive data.
- Background jobs, queues, retries, or concurrency.
- External providers or new infrastructure.
- Cross-platform behavior.
- A migration path or rollback plan.

Decrease design depth when the change is:

- Local, reversible, and easy to test.
- A small UI copy/layout fix.
- A straightforward bug with a clear reproduction.
- Consistent with an existing nearby pattern.
