---
name: readme
description: Minimal project README template for repositories created from the Agentic Rails context starter.
metadata:
  version: "2.0"
  agentic_rails_source_version: "2.0"
  owner: "Your Name"
  repo: "your-repo"
---
# Project Name

Short description of the project.

## Overview

Replace this section with the project-specific purpose, audience, and current status.

## Getting Started

Add setup, build, test, and run instructions once the project stack is known.

## Project Context

This repository was created from `agentic_rails_context_starter`, the context-template side of the Agentic Rails system.

This README is the single entry point for the repository. Use the links below as a convenient nexus into the broader context layers — not every file, just the doorways into each part of the system.

### Start here

- [AGENTS.md](AGENTS.md) - mandatory agent startup workflow and working rules
- [AGENTIC_RAILS_README.MD](AGENTIC_RAILS_README.MD) - durable overview of the Agentic Rails system
- [context/laws.md](context/laws.md) - constitutional code-quality and security laws (loaded first)
- [context/agenticworkflow.md](context/agenticworkflow.md) - the seven-tier workflow standard
- [context/design.md](context/design.md) - Tier 1 design specification and Milestones Index

### Context layers

- [context/dictations-tier-0/](context/dictations-tier-0/) - Tier 0 raw dictation and transcription
- [context/design.md](context/design.md) - Tier 1 design (includes the Milestones Index)
- [context/milestones/](context/milestones/) - Tier 2 milestone documents
- [context/sprints/](context/sprints/) - Tier 3 sprints
- [context/backlog/](context/backlog/) - Tier 4 stories
- [context/implementation-plans/](context/implementation-plans/) - Tier 5 plans and Tier 6 phases
- [context/wiki/home.md](context/wiki/home.md) - operational reference notes and cheat sheets

## Repository Layout

```text
project-root/
|-- AGENTS.md
|-- AGENTIC_RAILS_README.MD
|-- CLAUDE.md
|-- README.md
`-- context/
    |-- laws.md
    |-- agenticworkflow.md
    |-- design.md
    |-- agent-thinking.md
    |-- dictations-tier-0/
    |-- milestones/
    |-- sprints/
    |-- backlog/
    |-- implementation-plans/
    `-- wiki/
```

## Notes

- Replace this README with project-specific information as the project matures.
- Keep `AGENTIC_RAILS_README.MD` in derived projects so the framework context is not lost when this README changes.
