---
name: agentic-rails-readme
description: Durable framework overview for Agentic Rails, the opinionated IDE-agnostic system for AI-assisted software development.
metadata:
  version: "2.0"
  agentic_rails_source_version: "2.0"
  owner: "Your Name"
  repo: "your-repo"
---

# Agentic Rails

Agentic Rails is an opinionated, IDE-agnostic framework for AI-assisted software development.

The core idea is simple:

> Agents can move fast, but they need rails.

Without rails, agentic coding can become generated code, scattered plans, half-remembered decisions, and fragile handovers. Agentic Rails gives AI agents a structured way to work inside a project so the human can keep control, understand what happened, and continue safely.

```text
Left rail  = context and provenance
Right rail = tools, skills, agents, and workflows
Carriage   = the project being built
Driver     = the human
```

The point is not to make agents autonomous. The point is to make agentic coding legible, inspectable, repeatable, and safe enough for real engineering work.

## Repository Model

Agentic Rails is the framework name for projects that use the context starter and reusable tooling together. It is not a separate repository.

| Layer | Role | Responsibility |
| --- | --- | --- |
| Agentic Rails | Framework name | Names the combined development system, terminology, and adoption model |
| `agentic_rails_context_starter` | Left rail | Template repository for project-local context, plans, implementation logs, and handovers |
| `agentic_rails_tooling` | Right rail | Reusable skills, agents, rules, workflows, and references |
| Target project repositories | Carriage | Actual software projects created from the starter and supported by tooling |

This repository was created from, or is itself, the `agentic_rails_context_starter` template. It should carry the context structure and persistent framework overview, but it should not become the home for generic reusable skills, agents, or workflows. Those belong in `agentic_rails_tooling`.

## The Left Rail: Context And Provenance

The left rail answers:

> Where does project knowledge live?

It is provided by `agentic_rails_context_starter` and gives each project a durable documentation structure:

- seven-tier context hierarchy
- backlog, sprint, and milestone conventions
- documentation conventions
- implementation-plan folders that receive plan, implementation-log, and completion-review documents
- optional skill-generated provenance artifacts
- handover locations when a handover skill or workflow is used
- persistent framework identity files

The starter is a template. A derived project should replace placeholders with project-specific purpose, architecture, milestones, sprints, stories, and execution history.

## The Right Rail: Tooling And Behaviour

The right rail answers:

> How should agents behave while working?

It is provided by `agentic_rails_tooling` and may include reusable:

- skills
- specialist agents
- rules
- workflow skills
- handover behaviours
- planning behaviours
- complaint logging behaviours
- evidence and provenance behaviours

Project-local context remains authoritative. Shared tooling supplements the project, but it does not override the project laws, design, milestones, sprints, stories, or implementation plans.

## Seven-Tier Context System

Agentic Rails uses a seven-tier, backlog-driven, Scrum-aligned context model. Rough design and milestones are set up front; work is then planned close to execution by pulling only what is needed now. The backlog is allowed to be messy.

| Tier | Layer | Location | Purpose | Scrum |
| --- | --- | --- | --- | --- |
| Tier 0 | Transcription | `context/dictations-tier-0/` | Raw dictation — the rough shape of the project before structure is imposed | Pre-planning |
| Tier 1 | Design | `context/design.md` | The whole deliverable and its largest pieces; holds the Milestones Index subsection | Vision / roadmap |
| Tier 2 | Milestone | `context/milestones/` | Macro-features; each doc indexes a grouped collection of sprints | Theme |
| Tier 3 | Sprint | `context/sprints/` | Time-bounded chunks toward a milestone with a clear deliverable | Sprint |
| Tier 4 | Story | `context/backlog/` | Discrete work units (feature, bug, refactor), then scheduled into a sprint | Story |
| Tier 5 | Implementation Plan | `context/implementation-plans/` | The normalized how-to for one story, with scoring and mitigation | Task breakdown |
| Tier 6 | Phase *(optional)* | `context/implementation-plans/` | A safe slice of an over-large story | Sub-task |

Lower tiers give agents strategic context. Higher tiers capture what happened during execution. This prevents agents from operating only on immediate prompts and scattered source files.

### Vocabulary

The overloaded word **`goal`** is retired: the old goal-file container is gone (its grouping role moved to Milestone and Sprint), and the old individual goal is now a **Story**. The word **`task`** is never used as a tier name, because sub-agents already use it for their internal to-do items. The system adopts standard Scrum nouns: **Design → Milestone → Sprint → Story**, with **Phases** as an optional split below the implementation plan.

### Scoring, Orchestration, and Observability

Every story is scored on three orthogonal metrics — **Complexity** (reasoning demand), **Effort** (volume), and **Risk** (uncapped headline plus sub-scores) — before model assignment. Scores drive model routing and risk-driven mitigation (fragment into phases, add test/eval/provenance gates) at planning time. Execution is handed to an **Orchestrator** that chooses the model and reasoning level, runs the story, and produces a **Completion Review** (estimates vs. actuals, model used, and why things were unexpected). The scoring and orchestration logic are right-rail tooling; this starter defines the artifacts they read and write.

## Provenance

Agentic Rails treats provenance as a first-class engineering artifact.

It does not only ask:

> What code changed?

It also asks:

> What was intended, what happened, what evidence proves it, what friction appeared, and how does ownership transfer back to the human?

Meaningful implementation work should live in a dedicated folder under `context/implementation-plans/`:

```text
context/
  implementation-plans/
    STORY_3_1_short-readable-name/
      plan.md
      implementation-log.md
      completion-review.md
```

### `plan.md`

The intended work:

- objective
- estimates block (time, files, effort, complexity, risk)
- complexity / effort / risk scoring and routing intent
- mitigation (phase fragmentation, gates)
- approach, scope, and non-goals
- steps
- acceptance criteria
- optional Tier 6 phase breakdown
- risks and open questions

### `implementation-log.md`

What actually happened:

- execution steps
- deviations from the plan
- failed attempts
- implementation decisions
- validation performed
- remaining uncertainty

### `completion-review.md`

The session-end postmortem, distinct from the implementation log:

- estimates vs. actuals (same units on both sides)
- model used and reasoning level
- narrative review
- why things were unexpected, split by root cause

The following artifacts are optional. They are created only when the corresponding reusable skill or workflow is invoked for the task.

### `complaining.md`

Operational friction:

- missing permissions
- ambiguous requirements
- broken tooling
- risky assumptions
- repeated workarounds
- missing domain knowledge
- unclear validation paths

This is not emotional theatre. It captures actionable friction that would otherwise disappear.

Created by the `complaining` skill.

### `thinking.md`

Sanitised agent notes:

- useful investigation paths
- discovered constraints
- observations for future agents
- things to revisit

This is not a private chain-of-thought dump.

Created by the `thinking-out-loud` skill.

### `evidence.md`

The provenance index:

- files changed
- commits
- tests run
- build results
- validation evidence
- planning inputs
- known unverified claims

Created by the `evidence` skill.

### `handover/`

Ownership transfer artifacts that help the human understand what was done and how to continue.

Created by the `handover` skill or a larger handover workflow.

## Accountability Handover

Agentic Rails treats handover as part of the work, not an afterthought.

### Shallow Handover

Use shallow handover for smaller tasks. It should answer:

> What did you build, did it work, and where can I verify it?

It usually includes:

- elevator pitch
- scope covered
- technical choices
- outcome assessment
- source-grounded evidence
- important decisions
- risks
- suggested next step

### Deep Handover

Use deep handover for larger or production-grade work. It should answer:

> If the AI never comes back, how does the human fully understand, maintain, criticise, and continue this work?

Deep handover can produce:

```text
handover/deep/
  00-index.md
  01-deep-technical-report.md
  02-walkthrough-tour-script.md
  03-post-mortem-retrospective.md
  04-180-performance-review.md
  05-software-bill-of-materials.md
  06-future-maintenance-map.md
```

Deep handover should be grounded in the plan, implementation log, complaints, thinking notes, evidence, source files, git history, tests, and planning documents.

## Warm And Cold Handover

Warm handover happens immediately after the work, while the agent still has conversation context. It can produce stronger retrospectives, decision history, and collaboration assessments.

Cold handover happens later, when the agent was not present. It must rely only on source code, git history, documentation, implementation logs, complaint logs, and evidence files. Cold retrospectives should label claims as verified, inferred, assumed, or unknown.

## Progressive Disclosure

Agentic Rails should not dump every rule into every prompt.

Agents should first detect whether a repository follows Agentic Rails conventions, then load only the relevant project context and skills for the task.

Common detection points include:

- `AGENTIC_RAILS.md`
- `.agentic-rails.json`
- `context/implementation-plans/`
- `AGENTIC_RAILS_README.MD`

Detailed conventions should live in reference files and project documentation, not in every prompt.

## Design Boundaries

`agentic_rails_context_starter` should contain:

- templates
- folder conventions
- starter documentation
- bootstrap files
- persistent framework identity files
- default context structure

It should not contain:

- generic reusable skills
- generic reusable agents
- generic reusable workflows

`agentic_rails_tooling` should contain reusable agentic machinery.

Target project repositories may contain project-specific agents, skills, tools, generated plans, logs, evidence, and handovers when they belong directly to that project.

## Operating Loop

Agentic Rails turns agentic coding from:

```text
Prompt -> Code -> Hope
```

into:

```text
Context -> Backlog -> Plan -> Score -> Execute -> Log -> Review -> Handover -> Ownership
```

The human remains responsible for direction, judgement, priorities, acceptance, taste, risk tolerance, and final ownership. Agents can execute, inspect, explain, complain, and hand over. They do not become the owner.
