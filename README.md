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

Project planning and AI-agent context live in [context/](context/). Start with:

- [context/laws.md](context/laws.md)
- [context/design.md](context/design.md) (Tier 1 design, includes the Milestones Index)
- [context/milestones/](context/milestones/) (Tier 2 milestone docs)
- [context/sprints/](context/sprints/) (Tier 3 sprints)
- [context/backlog/](context/backlog/) (Tier 4 stories)
- [context/implementation-plans/IMPLEMENTATION_PLAN_TEMPLATE/](context/implementation-plans/IMPLEMENTATION_PLAN_TEMPLATE/) (Tier 5 plans, Tier 6 phases)

For the durable overview of the Agentic Rails system, keep and maintain [AGENTIC_RAILS_README.MD](AGENTIC_RAILS_README.MD).

## Repository Layout

```text
project-root/
|-- AGENTS.md
|-- AGENTIC_RAILS_README.MD
|-- README.md
`-- context/
    |-- laws.md
    |-- agenticworkflow.md
    |-- design.md
    |-- tier0/
    |-- milestones/
    |-- sprints/
    |-- backlog/
    |-- implementation-plans/
    |-- model-resumes/
    `-- wiki/
```

## Notes

- Replace this README with project-specific information as the project matures.
- Keep `AGENTIC_RAILS_README.MD` in derived projects so the framework context is not lost when this README changes.
