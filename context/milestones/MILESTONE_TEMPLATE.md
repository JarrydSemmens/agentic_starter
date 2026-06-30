---
name: milestone-template
description: Tier 2 milestone template. A milestone is a macro-feature or major delivery phase that indexes a grouped collection of sprints.
metadata:
  version: "2.0"
  agentic_rails_source_version: "2.0"
  owner: "Your Name"
  repo: "your-repo"
---
# Milestone N: *Name*

> **Tier 2 - Milestone.** A macro-feature or major delivery phase. This document indexes the sprints that deliver it.
>
> Related: [design.md (Milestones Index)](../design.md#milestones-index), [../sprints/](../sprints/), [../backlog/](../backlog/)

---

## Intent

One sentence describing the macro-feature or major phase this milestone delivers. The deliverable is the milestone as a whole, not any single sprint.

## Why it matters

- Reason 1
- Reason 2

## Impact

- What completing this milestone unlocks
- What it enables downstream

## Status

`Not Started | In Progress | Blocked | Complete` — `<X>/<Y>` sprints complete.

---

## Sprint Index

> The grouped collection of sprints that deliver this milestone, ordered by interdependency. A milestone may yield several sprints, sometimes planned all at once (per-milestone planning) or added later (per-sprint planning). Each sprint has a clear, concise deliverable.

| Sprint | Document | Deliverable | Status |
| --- | --- | --- | --- |
| Sprint 1 | [../sprints/sprint-1.md](../sprints/sprint-1.md) | *What this sprint delivers* | Not Started |

---

## Backlog Source

The stories that feed this milestone's sprints are pulled from the [backlog](../backlog/). During per-milestone planning, search the backlog for everything related to this milestone, gather the relevant stories, compute cumulative effort/complexity/risk, and assemble the sprints above ordered by interdependency.

- Relevant backlog themes: *list the search themes used to drain the backlog for this milestone*
- Known interdependencies: *e.g. "secrets sprint cannot start until the container sprint exists"*

---

## Notes

- Keep this index in sync with [../sprints/](../sprints/) and the [Milestones Index](../design.md#milestones-index) in Design.
- If a story turns out to be milestone-sized, reclassify it into its own milestone rather than forcing it into a sprint here.
