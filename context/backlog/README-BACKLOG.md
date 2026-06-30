---
name: backlog-readme
description: Guidance for the Tier 4 story backlog, the evergreen, prioritized pool of discrete work units that sprint planning drains into sprints.
metadata:
  version: "2.0"
  agentic_rails_source_version: "2.0"
  owner: "Your Name"
  repo: "your-repo"
---
# Tier 4 - Story Backlog

A **Story** is one discrete work unit: a bug fix, a feature, or a refactor. The backlog is the pool of stories, built once from Design + Milestones and then refined continuously. Sprint planning pulls stories from here into sprints.

## Backlog rules

- **30-story cap per file.** Each backlog file holds a maximum of 30 stories; overflow spawns a new backlog file (`backlog-1.md`, `backlog-2.md`, ...).
- **Priority sorting front-to-back.** Most urgent, important, concrete, and doable stories go in the **front** files; wishful, experimental, least-concrete, least-urgent stories sink to the **back**.
- **Evergreen and messy by design.** The backlog is not meant to be perfectly organized end to end. It can represent six months to several years of work. Do not try to maintain perfect foresight.
- **Reclassify mis-sized stories.** A story that, once scored, reveals itself to be epic-sized is actually a **Milestone**. Promote it into a milestone (see [../milestones/](../milestones/)) and the [Milestones Index](../design.md#milestones-index) rather than forcing it through as a story.
- **Supplement freely.** Add stories as understanding improves.

## Scoring

Stories are scored on three orthogonal metrics before model assignment: **Complexity** (reasoning demand), **Effort** (volume), and **Risk** (uncapped headline + sub-scores). Scoring is performed by right-rail tooling and recorded when a story is scheduled into a sprint or planned. See [agenticworkflow.md](../agenticworkflow.md#scoring-model-complexity-effort-risk).

## Files

- [BACKLOG_TEMPLATE.md](BACKLOG_TEMPLATE.md) - copy this to start a new backlog file.
- [backlog-1.md](backlog-1.md) - the front (highest-priority) backlog file.

## Flow

1. Build the backlog once from Design + Milestones.
2. Sort it front-to-back by priority.
3. Sprint planning searches the backlog by milestone theme, gathers stories, scores them, and schedules them into [../sprints/](../sprints/).
4. A scheduled story ready to run gets a Tier 5 implementation plan under [../implementation-plans/](../implementation-plans/).
