---
name: tier0-readme
description: Tier 0 raw intake and addendum guidance for dictated notes, rough project seeds, and recurring vision updates.
metadata:
  version: "0.2"
  agentic_rails_source_version: "0.2"
  owner: "Your Name"
  repo: "your-repo"
---
# Tier 0 - Raw Intake and Addenda

Tier 0 is the raw source layer for the five-tier context system. It holds messy human intent before that intent has been synthesized into maintained design, milestone, goal, or implementation-plan context.

Use this folder for durable intake such as:

- initial dictated project seed documents
- voice-note transcripts from AI conversations
- supplemental design addenda
- scope changes, milestone splits, deleted milestones, or reordered goals
- notes that explain why Tier 4 implementation plans need to be regenerated or revised

Do not treat Tier 0 as authoritative after synthesis. Once an intake file changes project direction, promote the accepted decision into the maintained context files:

- Tier 1: `../design.md`
- Tier 2: `../milestones.md`
- Tier 3: `../goals*.md`
- Tier 4: `../implementation-plans/*.md`

## Naming Guidance

Prefer filenames that sort by date and describe the source:

- `YYYY-MM-DD_initial_project_seed.md`
- `YYYY-MM-DD_addendum_<short-topic>.md`
- `YYYY-MM-DD_scope_revision_<short-topic>.md`
- `YYYY-MM-DD_goal_reorder_<short-topic>.md`

Keep names short, stable, and specific enough for an agent to cite from a goal or implementation plan.

## Intake Template

```md
# <Date> - <Short Topic>

## Source

- Captured from: <voice notes, AI chat, meeting, personal notes, etc.>
- Related project area: <milestone, goal, subsystem, or unknown>

## Raw Notes

Paste or summarize the raw dictated material here.

## Important Signals

- New decision:
- Changed assumption:
- New risk:
- Open question:
- Possible milestone or goal impact:

## Integration Notes

- Update `../design.md`:
- Update `../milestones.md`:
- Update `../goals*.md`:
- Update `../implementation-plans/`:
```

## Agent Rules

- Read Tier 0 only when the task involves intake synthesis, project enrichment, scope revision, or rationale recovery.
- Preserve uncertainty instead of turning rough notes into fake certainty.
- Ask or record questions when Tier 0 contradicts maintained context.
- After synthesis, link the Tier 0 source only where the raw source remains useful for traceability.
- Do not store secrets, credentials, or private information here unless the project has explicitly defined a safe handling policy.
