---
name: sprints-readme
description: Guidance for Tier 3 sprint documents, the time-bounded execution batches that deliver a milestone by scheduling stories pulled from the backlog.
metadata:
  version: "2.0"
  agentic_rails_source_version: "2.0"
  owner: "Your Name"
  repo: "your-repo"
---
ARCHIVED — the sprint tier was retired by the six-tier reform (2 July 2026); see the six-tier addendum. Kept for migration reference only.

# Tier 3 - Sprints

A **Sprint** is a time-bounded chunk of work toward a milestone, with a clear deliverable outcome. A milestone may require several sprints. A sprint holds roughly a dozen stories pulled from the [backlog](../backlog/).

## How sprints are produced

Sprint planning is where the hard thinking happens: stories are gathered, scored (complexity / effort / risk), mitigated, and where necessary fragmented into phases. It runs at two granularities:

- **Per-milestone:** for a fresh milestone, plan a whole milestone's worth of sprints at once. Search the backlog for everything related to the milestone, gather the stories, compute cumulative effort/complexity/risk, and assemble one or more sprints ordered by interdependency.
- **Per-sprint (ad-hoc):** re-run on an existing sprint any time. If stories have blown out and no longer fit, spawn a secondary sprint and shunt the overflow into it, leaving each sprint with a clear, concise deliverable.

You never have to hold the whole plan in your head, and you never plan far-future sprints that would only be re-planned later.

## Files

- [SPRINT_TEMPLATE.md](SPRINT_TEMPLATE.md) - copy this for each new sprint.
- [sprint-1.md](sprint-1.md) - starter example sprint.

## Rules

- Each sprint belongs to exactly one milestone and links back to it under [../milestones/](../milestones/).
- Stories are pulled from [../backlog/](../backlog/); record which backlog stories a sprint scheduled.
- Order stories within a sprint by interdependency.
- A story ready to execute gets a Tier 5 implementation plan under [../implementation-plans/](../implementation-plans/).
- Keep each sprint's deliverable concise and singular.
