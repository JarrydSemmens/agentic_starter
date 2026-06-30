---
name: sprint-template
description: Tier 3 sprint template. A sprint is a time-bounded execution batch that schedules stories pulled from the backlog toward a milestone deliverable.
metadata:
  version: "2.0"
  agentic_rails_source_version: "2.0"
  owner: "Your Name"
  repo: "your-repo"
---
# Sprint N: *Name*

> **Tier 3 - Sprint.** A time-bounded chunk of work toward a milestone with a clear deliverable.
>
> **Milestone:** [Milestone N](../milestones/milestone-1.md)
> **Backlog source:** [../backlog/](../backlog/)

---

## Sprint Goal

One concise sentence describing what this sprint delivers. If you cannot state it in one sentence, the sprint is doing too much — split it and shunt the overflow into a secondary sprint.

## Status

`Not Started | In Progress | Blocked | Complete`

## Time Box

- Planned start / end or duration: *e.g. one week, or "until the deliverable is met"*

---

## Stories (scheduled from the backlog)

> Roughly a dozen stories, ordered by interdependency. Each story is pulled from the backlog and scored before execution. A story ready to run gets a Tier 5 implementation plan.

| # | Story | Backlog ref | Complexity | Effort | Risk | Plan | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | *Story name* | [backlog-1.md#story-id](../backlog/backlog-1.md) | — | — | — | *link when ready* | Not Started |
| 2 | *Story name* | [backlog-1.md#story-id](../backlog/backlog-1.md) | — | — | — | *link when ready* | Not Started |

Scores: Complexity (reasoning demand), Effort (volume), Risk (uncapped headline). See [agenticworkflow.md](../agenticworkflow.md#scoring-model-complexity-effort-risk).

---

## Interdependency Order

Explain the sequencing constraints between the stories above (what must be done before what, and why).

1. *Story A before Story B because ...*
2. *...*

---

## Mitigation

> Risk is mitigated at planning time, not at execution. Record any stories that were fragmented into phases or wrapped in extra gates.

- *Story X scored high risk → fragmented into N phases in its implementation plan; gates: unit tests + smoke test between phases.*

---

## Overflow

If stories blow out during the sprint, list what was shunted into a secondary sprint here, and link it.

- Shunted to: [sprint-N.md](sprint-1.md) — *reason*

---

## Notes

- Update the parent milestone's Sprint Index when this sprint's status changes.
- Keep the deliverable singular and clear; resist scope creep mid-sprint.
