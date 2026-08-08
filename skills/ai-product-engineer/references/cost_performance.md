# Cost And Performance

Use this reference when choosing models or productionizing AI features.

## Model Choice

Compare options by:

- Accuracy or task success.
- Latency p50/p95.
- Cost per successful task.
- Context length needs.
- Structured-output reliability.
- Privacy and data handling.
- Operational complexity.

Do not choose the largest model unless its quality improvement changes the product outcome enough to justify cost and latency.

## Optimization Levers

- Use smaller models for routing, classification, extraction, and simple transformations.
- Cache deterministic or repeated results.
- Reduce context size with retrieval, summaries, or field selection.
- Batch offline tasks.
- Stream responses when perceived latency matters.
- Use fallbacks for provider errors or rate limits.
- Move expensive work to background jobs when the user does not need immediate output.

## Budget Controls

- Estimate cost per user action.
- Set per-user, per-workspace, or per-job limits.
- Log token usage and provider cost where possible.
- Add alerts for sudden usage spikes.
- Make retries bounded.

## Latency Design

- Identify which path must be interactive.
- Set timeouts.
- Show progress for long tasks.
- Return partial results only when they are useful and clearly labeled.
- Avoid multi-agent loops in synchronous UX unless bounded tightly.
