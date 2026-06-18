---
version: 0.1
agentic_rails_source_version: 0.1
owner: "Your Name"
repo: "your-repo"
description: Tier 1 design specification template defining project architecture, principles, constraints, and the five-tier context hierarchy.
---
# Project Name - Design Specification

## Purpose of This File

This repository is an intentionally empty starter for future projects. Replace the placeholders in this file when you fork or copy the template into a real codebase.

This file is Tier 1: the maintained design specification. It should synthesize relevant Tier 0 intake into stable project direction.

## Context Hierarchy

| Tier | Document | Purpose |
| --- | --- | --- |
| 0 - Raw Intake and Addenda | [tier0/](tier0/) | Dictated notes, rough source material, and supplemental design changes |
| 1 - Design | `design.md` | Project architecture, principles, and constraints |
| 2 - Milestones | [milestones.md](milestones.md) | Roadmap structure and milestone summaries |
| 3 - Goals | `goals*.md` | Specific deliverables and acceptance criteria |
| 4 - Implementation Plans and Handovers | `implementation-plans/*.md` | Task-specific implementation plans and phase handovers |
| Support | [laws.md](laws.md) | Constitutional code quality and security laws — loaded first by all agents |
| Support | [agenticworkflow.md](agenticworkflow.md) | Workflow for AI agent collaboration |
| Support | [AgentThinking.md](AgentThinking.md) | Optional temporary scratchpad for long tasks |
| Support | [wiki/home.md](wiki/home.md) | Operational reference notes and cheat sheets |

---

## Executive Summary

Describe the project this repository will become:

- what it is
- who it is for
- what problem it solves
- why this architecture is appropriate

### Core Principles

- **Principle 1:** Replace with a guiding architectural principle.
- **Principle 2:** Replace with a second principle.
- **Principle 3:** Replace with a third principle.
- **Principle 4:** Add more only when they are truly decision-driving.

---

## System Architecture

### How the Pieces Fit Together

Describe the major components of the system, how they interact, and what boundaries matter.

**External services and dependencies:**

- `Service or dependency` - purpose
- `Service or dependency` - purpose

### Repository Structure

Update this tree as the project takes shape.

```text
project-root/
|-- context/
|   |-- tier0/
|   |-- design.md
|   |-- milestones.md
|   |-- goals1.md
|   |-- agenticworkflow.md
|   |-- AgentThinking.md
|   |-- implementation-plans/
|   `-- wiki/
|-- source/
|-- tests/
|-- scripts/
`-- README.md
```

---

## Processing Pipelines

> Delete this section if the project has no defined pipelines. Add it back when the system's data flows are known.

Describe the main data flows or user journeys only after the project has enough shape to justify them.

### Pipeline 1

1. Step 1
2. Step 2
3. Step 3

### Pipeline 2

1. Step 1
2. Step 2
3. Step 3

---

## Configuration

Document configuration only once the real stack is known.

### Primary Configuration

Describe the main project configuration surface.

### Secondary or App-Level Configuration

Describe any machine-level or environment-level settings.

### Secrets and Credentials

Document the real secret-management approach here and in the wiki once chosen.

---

## Application Layers

List only the layers the project actually uses.

### Layer 1

Purpose and architecture summary.

### Layer 2

Purpose and architecture summary.

---

## Security and Privacy

- Define how data is stored and protected.
- Define the expected secret-management strategy.
- Define any privacy or compliance constraints.

---

## Observability

### Logging

Describe logging approach.

### Debugging

Describe debugging tools or diagnostic outputs.

### Health Checks

Describe any health checks or operational diagnostics.

---

## Testing Policy

Define what kinds of tests are expected and when they are required.

---

## Performance

If performance is not yet a concern, say so explicitly and revisit it later.

---

## Context Maintenance

Use Tier 0 intake to revise this design when the project vision changes. Do not leave important decisions stranded in raw notes, chats, or addenda. Promote durable decisions into this file, milestones, goals, or implementation plans as appropriate.

When an older design statement is superseded, update it directly and preserve only the rationale needed for future agents to understand the decision.

---

## Navigation

### Specification Hierarchy

- [tier0/README.md](tier0/README.md) - Tier 0 raw intake and addenda
- [design.md](design.md) - Tier 1 design overview
- [milestones.md](milestones.md) - Tier 2 roadmap summary
- `goals*.md` - Tier 3 goals and deliverables
- `implementation-plans/*.md` - Tier 4 execution plans and handovers

### Reference Documents

- [agenticworkflow.md](agenticworkflow.md) - AI collaboration workflow
- [AgentThinking.md](AgentThinking.md) - optional temporary agent scratchpad

### Wiki

- [wiki/home.md](wiki/home.md) - wiki navigation hub
