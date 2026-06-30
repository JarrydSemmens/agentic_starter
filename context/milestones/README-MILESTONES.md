---
name: milestones-readme
description: Guidance for the Tier 2 milestone documents, each of which indexes a grouped collection of sprints toward a macro-feature or major delivery phase.
metadata:
  version: "2.0"
  agentic_rails_source_version: "2.0"
  owner: "Your Name"
  repo: "your-repo"
---
# Tier 2 - Milestones

A **Milestone** is a macro-feature or major delivery phase (for example "Dockerize the app", "Port the game to a new platform", or "Get the repo ready to move on"). Each milestone document is an **index of a grouped collection of sprints**. There are multiple milestone documents; one file per milestone.

The high-level **Milestones Index** (the table of contents pointing at these files) lives inside [design.md](../design.md), because a milestones table is the same tier as Design. The files in this folder are the milestones themselves, each pointing down at its sprints.

## How milestones are produced

1. After the rough Design exists, fragment it into milestones **conversationally** with the human. Propose a breakdown, then negotiate the count and shape until it fits the human's capacity and priorities.
2. Milestones are grouped around large-scale deliverables. The deliverable is the milestone, not necessarily a single sprint.
3. A milestone may require several sprints. Sprint planning drains the relevant backlog stories into one or more sprints, ordered by interdependency.

## Files

- [MILESTONE_TEMPLATE.md](MILESTONE_TEMPLATE.md) - copy this for each new milestone.
- [milestone-1.md](milestone-1.md) - starter example milestone.

## Rules

- One file per milestone. Keep milestones thematic, not granular.
- Each milestone indexes its sprints under [../sprints/](../sprints/).
- Keep the Milestones Index in [design.md](../design.md) in sync with the files here.
- When a backlog story scores as epic-sized, reclassify it upward into a new milestone here and in the Design index.
- The system is progressive: complete a milestone and move on rather than perpetually re-opening old milestones.
