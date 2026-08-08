# Engineering Thinking Examples

## Example: Build A SaaS Feature

Request: "Add team invitations."

Engineering thinking:

- Requirement: admins invite users by email; invited users join a workspace.
- Boundaries: frontend invite form, backend invite API, email provider, invitation table, auth callback.
- Risks: duplicate invites, expired tokens, workspace ownership, email failure, invite enumeration.
- Implementation: model, API, service, UI, tests, config.
- Validation: API tests for accept/expire/duplicate; UI test for invite flow.

## Example: Refactor A Module

Request: "Clean up the analytics service."

Engineering thinking:

- Identify pain: hard to test, mixed IO and calculation, slow queries.
- Preserve contracts first.
- Extract pure calculations from IO.
- Add tests around existing behavior before changing internals.
- Avoid rewriting unrelated analytics surfaces.
