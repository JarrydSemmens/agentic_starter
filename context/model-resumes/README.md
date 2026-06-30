---
name: model-resumes-readme
description: Guidance for Model Resumes, a cross-task artifact recording empirical, workflow-specific performance of each model, rebuilt (never appended) from completion reviews.
metadata:
  version: "2.0"
  agentic_rails_source_version: "2.0"
  owner: "Your Name"
  repo: "your-repo"
---
# Model Resumes

A **Model Resume** is a central, cross-task artifact that lives outside the tier hierarchy. There is one resume per model (Sonnet, Haiku, Opus, GPT, Qwen, ...).

The framing is deliberate: **picking a model for work is hiring for a team.** A resume tells you what a worker is good at and their track record. Each resume holds empirical, *your-workflow-specific* data — not vendor benchmarks. It is the inverse of a standard ML "model card" (top-down, generic); Model Resumes are bottom-up ground truth from your own completion logs.

## What a resume records

- Complexity ranges the model is good at / bad at.
- Effort thresholds where it starts to struggle.
- Token efficiency, speed, and observed error patterns.

## Rebuild, never append

Resumes are **rebuilt from scratch, never appended.** Appending would over-weight the most recent job (recency bias).

- **Batched updates:** collect a set of completion reviews over a few days, then run the rebuild over the corpus and regenerate all resumes.
- **Compaction (cost control):** a full rebuild over a large corpus is expensive. Two strategies:
  - *Golden-set / stratified sampling:* a cheap first pass scores all logs to pick the juiciest ones (failures, surprising successes, edge cases), then deep-evaluate only those.
  - *Incremental merge:* evaluate in batches of ~20, then merge the partial resumes into the final resumes.
- The governing trade-off is **cost vs. freshness** — how stale a resume may get before a rebuild is due (an open parameter for each project).

## Source data

Resumes are rebuilt from the `completion-review.md` files produced under [../implementation-plans/](../implementation-plans/), specifically their "Signals for Model Resumes" and "Why Unexpected" sections. The rebuild logic is **right-rail tooling** in `agentic_rails_tooling`; this folder holds only the resulting artifacts.

## Files

- [MODEL_RESUME_TEMPLATE.md](MODEL_RESUME_TEMPLATE.md) - copy this to create a resume for a model.
