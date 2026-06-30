---
name: completion-review-template
description: Session-end completion review (postmortem) template. Records estimates vs. actuals, model used, narrative, and root causes of surprises for one story.
metadata:
  version: "2.0"
  agentic_rails_source_version: "2.0"
  owner: "Your Name"
  repo: "your-repo"
---

# Completion Review (Postmortem)

A session-end review for one story, distinct from `implementation-log.md` (which records what was *done*). Produce it by walking the git diff and the conversation history. Keep it consistent and machine-ingestible so it can later feed the Oracle dashboard and Model Resume rebuilds.

> Until Oracle infrastructure exists, this file is the interim on-disk staging record. Do not build the dashboard prematurely.

## Status

- Story / Plan: `<link to plan.md>`
- Date completed: `<YYYY-MM-DD>`
- Reviewer / session: `<agent, model, IDE, or human>`

## Estimates vs. Actuals

> Same units as the Estimates block in `plan.md`. Do not estimate one unit and measure another.

| Metric | Estimate | Actual | Delta | Unit |
| --- | --- | --- | --- | --- |
| Time | `<est>` | `<actual>` | `<+/->` | `<minutes / hours / sessions>` |
| Files | `<est>` | `<actual>` | `<+/->` | `<files touched>` |
| Effort | `<est>` | `<actual>` | `<+/->` | `<LOC / chunks / subsystems>` |
| Complexity | `<est>` | `<actual>` | `<+/->` | `<reasoning-budget units>` |
| Risk | `<est>` | `<actual>` | `<+/->` | `<uncapped headline>` |
| Tokens | `<est>` | `<actual>` | `<+/->` | `<tokens>` |

## Model

- Model used: `<model>`
- Reasoning level: `<level>`
- Phases executed: `<count, if fragmented>`

## Narrative Review

How it went, what it struggled with, and what was unexpected (good or bad). Keep it factual and grounded in the diff and the session history.

## Why Unexpected (root causes)

> The crucial section. Distinguish root causes, because different causes need different fixes.

| Surprise | Root cause | Fix target |
| --- | --- | --- |
| `<e.g. took twice as long>` | `<subsystem X had hidden dependencies>` | Tune the **effort estimator** |
| `<e.g. took twice as long>` | `<model kept hallucinating>` | Change **model tier** / improve context |

## Signals for Model Resumes

> Distilled, your-workflow-specific observations about the model on this kind of work. Feeds the batched, rebuild-not-append resume process.

- Complexity range handled well / badly: `<observation>`
- Effort threshold where it struggled: `<observation>`
- Token efficiency / speed: `<observation>`
- Observed error pattern: `<observation>`
