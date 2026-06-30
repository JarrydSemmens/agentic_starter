---
name: tier0-readme
description: Tier 0 transcription guidance for raw dictation, rough project seeds, and recurring vision updates before any structure is imposed.
metadata:
  version: "2.0"
  agentic_rails_source_version: "2.0"
  owner: "Your Name"
  repo: "your-repo"
---
# Tier 0 - Transcription

Tier 0 is the raw source layer for the seven-tier context system. It holds a brain-dump of the rough shape of a project — messy human intent before any structure is imposed and before that intent has been synthesized into maintained design, milestone, sprint, story, or implementation-plan context. A transcription is typically the output of one to several hours of just talking.

Use this folder for durable transcription such as:

- initial dictated project seed documents (the rough shape of the whole project)
- voice-note transcripts from AI conversations
- supplemental design addenda
- scope changes, milestone splits, deleted milestones, or reordered work
- notes that explain why Tier 5 implementation plans need to be regenerated or revised

Do not treat Tier 0 as authoritative after synthesis. Once a transcription changes project direction, promote the accepted decision into the maintained context files:

- Tier 1: `../design.md` (including its Milestones Index)
- Tier 2: `../milestones/`
- Tier 3: `../sprints/`
- Tier 4: `../backlog/`
- Tier 5: `../implementation-plans/`

## Naming Guidance

Prefer filenames that sort by date and describe the source:

- `YYYY-MM-DD_initial_project_seed.md`
- `YYYY-MM-DD_addendum_<short-topic>.md`
- `YYYY-MM-DD_scope_revision_<short-topic>.md`
- `YYYY-MM-DD_milestone_reorder_<short-topic>.md`

Keep names short, stable, and specific enough for an agent to cite from a story or implementation plan.

## Intake Template

```md
# <Date> - <Short Topic>

## Source

- Captured from: <voice notes, AI chat, meeting, personal notes, etc.>
- Related project area: <milestone, sprint, story, subsystem, or unknown>

## Raw Notes

Paste or summarize the raw dictated material here.

## Important Signals

- New decision:
- Changed assumption:
- New risk:
- Open question:
- Possible milestone or story impact:

## Integration Notes

- Update `../design.md` (and its Milestones Index):
- Update `../milestones/`:
- Update `../sprints/`:
- Update `../backlog/`:
- Update `../implementation-plans/`:
```

## Agent Rules

- Read Tier 0 only when the task involves transcription synthesis, project enrichment, scope revision, or rationale recovery.
- Preserve uncertainty instead of turning rough notes into fake certainty.
- Ask or record questions when Tier 0 contradicts maintained context.
- After synthesis, link the Tier 0 source only where the raw source remains useful for traceability.
- Do not store secrets, credentials, or private information here unless the project has explicitly defined a safe handling policy.
