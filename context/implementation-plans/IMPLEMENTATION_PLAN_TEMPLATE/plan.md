---
name: implementation-plan-template
description: Tier 4 implementation plan template for scoping a concrete task, listing source context, affected areas, steps, verification, and risks.
metadata:
  version: "0.3"
  agentic_rails_source_version: "0.3"
  owner: "Your Name"
  repo: "your-repo"
---

# Implementation Plan Template

Use this folder as the starting point for a Tier 4 implementation plan in this repository. Copy `plan.md` and `implementation-log.md` to a task-specific folder and replace all placeholders.

Tier 4 context means the work is ready to execute against the repository. The plan should be grounded in maintained design, milestone, and goal context, and it should cite Tier 0 intake only when raw notes or addenda materially shaped the task.

## Naming Guidance

Choose a folder name that matches the task type:

- `GOAL_<milestone>_<goal>_<short-slug>/`
- `FEATURE_<short-slug>/`
- `BUG_<short-slug>/`

If the work is phased or needs explicit ownership transfer, use the relevant handover guidance in [agenticworkflow.md](../../agenticworkflow.md) or an installed handover skill.

---

## Metadata

- Task Type: `GOAL | FEATURE | BUG`
- Task Name: `<short task title>`
- Status: `Draft | Ready | In Progress | Blocked | Complete | Superseded`
- Owner: `<name or team>`
- Last Updated: `<YYYY-MM-DD>`

## Linked Context

- Tier 0 Source: `<link only if intake or addenda materially shaped this plan>`
- Design: [design.md](../../design.md)
- Workflow: [agenticworkflow.md](../../agenticworkflow.md)
- Milestone: `<link if applicable>`
- Goal: `<link if applicable>`
- Handover: `<link if continuing phased work>`
- External Tooling: `<shared rule, skill, workflow-skill, or specialist agent if required>`
- Optional Provenance Artifacts: `<complaining.md, thinking.md, evidence.md, or handover path only if created by an explicit skill or workflow>`

## Objective

State the concrete outcome this implementation plan must produce.

## Problem Summary

Describe the issue, feature gap, or goal being addressed. Keep this section factual and specific to the repository.

## Scope

- In scope: `<what this task will change>`
- In scope: `<second scope item>`
- Out of scope: `<what this plan explicitly does not cover>`

## Current State

Summarize the relevant existing structure, behavior, or placeholder content already present in the repository.

## Assumptions and Constraints

- `<important assumption>`
- `<technical or workflow constraint>`
- `<dependency, approval, or sequencing constraint>`

## Files and Areas Likely Affected

- `<path>` - `<why it matters>`
- `<path>` - `<why it matters>`
- `<path>` - `<why it matters>`

## Implementation Steps

1. `<first concrete change>`
2. `<second concrete change>`
3. `<third concrete change>`
4. `<fourth concrete change>`

## Verification Plan

### Automated Checks

- `<test command or lint command>`
- `<build command>`

### Manual Checks

1. `<manual verification step>`
2. `<manual verification step>`
3. `<manual verification step>`

## Risks and Open Questions

- Risk: `<known risk and why it matters>`
- Question: `<decision still needed>`
- Dependency: `<external dependency or prerequisite>`

## Completion Checklist

- [ ] Implementation matches the linked design and goal context
- [ ] Any relevant Tier 0 source has been synthesized into maintained docs
- [ ] Scope stayed within this plan
- [ ] Verification steps were completed or explicitly deferred
- [ ] Relevant status docs were updated
- [ ] `implementation-log.md` was updated
- [ ] Optional provenance artifacts were updated if their skills were used
- [ ] A handover artifact was created if a handover skill or workflow was used

## Notes for the Implementing Agent

- Read only the minimum required context before changing files.
- Prefer repository-specific decisions over generic examples.
- Use installed external skills, workflow-skills, rules, or specialist agents only when this plan or the task explicitly calls for them.
- Replace placeholders with concrete repository paths, commands, and acceptance criteria before implementation starts.
