# AI Evaluation Framework

AI products must be evaluable before they are trusted.

## Metric Types

- Task quality: accuracy, relevance, completeness, factuality, grounding.
- Safety: hallucination rate, prompt injection resistance, unsafe output rate, privacy leakage.
- UX: acceptance rate, correction rate, regeneration rate, user satisfaction.
- Reliability: timeout rate, error rate, fallback rate.
- Cost/performance: cost per task, latency p50/p95, token usage.

## Evaluation Assets

- Golden examples: representative inputs with expected outputs or rubrics.
- Adversarial examples: prompt injection, malformed inputs, misleading context.
- Regression set: past bugs and edge cases.
- Human review rubric: what good, acceptable, and bad output means.
- Automated checks: schema validation, citation presence, deterministic assertions.

## Evaluation Flywheel

1. Collect representative examples before launch.
2. Define a rubric and release gate.
3. Run offline evaluation before changes.
4. Log production failures and user corrections.
5. Promote real failures into the regression set.
6. Compare model, prompt, retrieval, or tool changes against the same set.

## Release Gates

Define release gates before launch:

- Minimum quality threshold.
- Maximum hallucination or unsupported-claim rate.
- Maximum p95 latency.
- Maximum cost per successful task.
- Required fallback behavior.

## Common Rubric

```markdown
| Criterion | 1 Poor | 3 Acceptable | 5 Excellent |
|---|---|---|---|
| Correctness | Wrong or unsupported | Mostly correct with minor gaps | Correct and well-supported |
| Grounding | No evidence | Some evidence | Clear citations/evidence |
| Usefulness | Not actionable | Partly useful | Directly helps the user decide |
| Safety | Leaks or fabricates | Minor risk | Handles uncertainty safely |
```

## Review Questions

- What examples prove the AI feature works?
- What examples prove it fails safely?
- How will quality regressions be caught?
- What will users see when confidence is low?
- Can the product explain or cite its answer when needed?
- What examples would make us decide not to ship?
- What cheaper or simpler model/workflow is the baseline?
