# Decision Records

Use a decision record when a change is hard to reverse, crosses module boundaries, affects public contracts, changes data shape, or creates new operational behavior.

Keep it short. The goal is to preserve reasoning, not ceremony.

## Template

```markdown
## Decision

Choose [option] for [problem].

## Context

- Goal:
- Constraints:
- Existing pattern:
- Non-goals:

## Options

| Option | Pros | Cons | Reversibility |
|---|---|---|---|

## Chosen Approach

- Why this option:
- What we are deliberately not solving:
- What would make us revisit:

## Consequences

- Code impact:
- Data impact:
- Operational impact:
- Test impact:
```

## Reversibility

- One-way door: migrations, public API contracts, security model, data ownership, vendor lock-in.
- Two-way door: internal module layout, UI composition, local naming, small helper abstractions.

Spend more time on one-way doors. Keep two-way doors moving.

## Decision Quality Checks

- The decision names a real tradeoff.
- Alternatives include the boring/simple option.
- The chosen path fits current evidence, not imagined scale.
- The validation plan would catch the main failure mode.
