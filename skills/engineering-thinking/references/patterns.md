# Engineering Patterns

Use these patterns as defaults. Follow the target repository's existing conventions when they differ.

## Module Boundaries

- Put business rules close to the domain they govern.
- Keep transport code thin: controllers/routes parse input and call services.
- Keep UI components focused on presentation and interaction; move shared logic into hooks/services only when reused.
- Keep persistence details out of UI and high-level orchestration.

## API Design

- Use typed request/response models.
- Keep resource identifiers in paths and filters/options in query parameters.
- Paginate or bound list endpoints.
- Return stable error shapes.
- Treat API contracts as shared product surfaces.

## Data Design

- Model ownership and lifecycle explicitly.
- Add indexes for expected lookup paths, not every column.
- Plan migrations before relying on new fields.
- Avoid ambiguous status fields without a state transition story.

## Refactoring

- Refactor toward a current change, not toward abstract neatness.
- Prefer small moves with tests over large rewrites.
- Preserve behavior first; change behavior deliberately.

## Validation

- Test the behavior closest to the risk.
- Typecheck shared contracts.
- Add regression tests for fixed bugs when practical.
- Document manual verification when automation is too expensive.
