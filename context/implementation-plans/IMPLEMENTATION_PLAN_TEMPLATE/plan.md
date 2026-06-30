---
name: implementation-plan-template
description: Tier 5 implementation plan template for one story, with estimates, complexity/effort/risk scoring, optional phase mitigation, source context, steps, verification, and risks.
metadata:
  version: "2.0"
  agentic_rails_source_version: "2.0"
  owner: "Your Name"
  repo: "your-repo"
---

# Implementation Plan Template

Use this folder as the starting point for a Tier 5 implementation plan in this repository. Copy `plan.md`, `implementation-log.md`, and `completion-review.md` to a story-specific folder and replace all placeholders.

Tier 5 context means one story is ready to execute against the repository. The plan should be grounded in maintained design, milestone, sprint, and story context, and it should cite Tier 0 transcription only when raw notes or addenda materially shaped the work. By the time execution starts, the work should already be scored, normalized, and (if risk demanded it) fragmented into phases.

## Naming Guidance

Choose a folder name that matches the work type:

- `STORY_<sprint>_<story>_<short-slug>/`
- `FEATURE_<short-slug>/`
- `BUG_<short-slug>/`

If the work is phased or needs explicit ownership transfer, use the relevant handover guidance in [agenticworkflow.md](../../agenticworkflow.md) or an installed handover skill.

---

## Estimates

> Populated during planning, before execution. Estimates and actuals must use the **same units** (do not estimate "file count" but measure "lines changed"). Actuals are recorded in `completion-review.md` at session end and compared back here.

| Metric | Estimate | Unit |
| --- | --- | --- |
| Time | `<value>` | `<minutes / hours / sessions>` |
| Files | `<value>` | `<files touched>` |
| Effort | `<value>` | `<LOC / chunks / subsystems>` |
| Complexity | `<value>` | `<reasoning-budget units>` |
| Risk | `<value>` | `<uncapped headline>` |
| Tokens | `<value>` | `<tokens>` |

## Scoring

> Three orthogonal metrics drive model routing and mitigation. Scoring is performed by right-rail tooling; record the results here. See [agenticworkflow.md](../../agenticworkflow.md#scoring-model-complexity-effort-risk).

- **Complexity** (reasoning demand): `<score>` — `<steps, files, decision points, dependencies against the per-model budget>`
- **Effort** (volume): `<score>` — `<file count, LOC, discrete chunks, subsystems touched>`
- **Risk** (uncapped headline, computed before mitigation): `<headline>`
  - Technical: `<sub-score>`
  - Architectural: `<sub-score>`
  - Dependency: `<sub-score>`
  - Other: `<sub-score>`
- **Routing intent:** `<which model tier + reasoning level this implies, and why>`

## Mitigation

> Mitigation happens at planning time, not execution. If risk is intolerably high, this story is **not** executed as-is.

- Fragmented into phases: `Yes | No` (if yes, see Phase Breakdown below)
- Gates inserted: `<unit tests, smoke tests, evaluations, provenance checks, and where they sit>`
- Irreducible risk accepted: `<what, and how it is wrapped in validation>`

## Metadata

- Work Type: `STORY | FEATURE | BUG`
- Story / Title: `<short title>`
- Status: `Draft | Ready | In Progress | Blocked | Complete | Superseded`
- Owner: `<name or team>`
- Last Updated: `<YYYY-MM-DD>`

## Linked Context

- Tier 0 Source: `<link only if transcription materially shaped this plan>`
- Design: [design.md](../../design.md)
- Workflow: [agenticworkflow.md](../../agenticworkflow.md)
- Milestone: `<link to ../../milestones/*.md if applicable>`
- Sprint: `<link to ../../sprints/*.md if applicable>`
- Story (backlog): `<link to ../../backlog/*.md story if applicable>`
- Handover: `<link if continuing phased work>`
- External Tooling: `<shared rule, skill, workflow-skill, or specialist agent if required>`
- Optional Provenance Artifacts: `<complaining.md, thinking.md, evidence.md, or handover path only if created by an explicit skill or workflow>`

## Objective

State the concrete outcome this implementation plan must produce for the one story it covers.

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

## Phase Breakdown (Tier 6, optional)

> Use only when risk or size demanded fragmentation. Each phase is an independently executable, risk-bounded slice carrying a tolerable risk score (e.g. several phases each at ~3 instead of one story at 10). Delete this section if the story runs in a single pass.

| Phase | Deliverable | Risk after split | Gate before next phase |
| --- | --- | --- | --- |
| Phase 1 | `<safe slice>` | `<score>` | `<test / smoke / eval / provenance check>` |
| Phase 2 | `<safe slice>` | `<score>` | `<gate>` |

## Risks and Open Questions

- Risk: `<known risk and why it matters>`
- Question: `<decision still needed>`
- Dependency: `<external dependency or prerequisite>`

## Completion Checklist

- [ ] Implementation matches the linked design, milestone, sprint, and story context
- [ ] Any relevant Tier 0 source has been synthesized into maintained docs
- [ ] Scope stayed within this plan
- [ ] Verification steps were completed or explicitly deferred
- [ ] Phase gates passed when the story was fragmented
- [ ] Relevant status docs (milestone, sprint, backlog) were updated
- [ ] `implementation-log.md` was updated
- [ ] `completion-review.md` was produced (estimates vs. actuals, model used, why-unexpected)
- [ ] Optional provenance artifacts were updated if their skills were used
- [ ] A handover artifact was created if a handover skill or workflow was used

## Notes for the Implementing Agent

- Read only the minimum required context before changing files.
- Prefer repository-specific decisions over generic examples.
- Use installed external skills, workflow-skills, rules, or specialist agents only when this plan or the task explicitly calls for them.
- Replace placeholders with concrete repository paths, commands, and acceptance criteria before implementation starts.
- At session end, fill in `completion-review.md` with actuals measured in the same units as the Estimates block above.
