---
version: 0.1
owner: "Your Name"
repo: "your-repo"
description: Starter repository overview explaining the five-tier context workflow, project structure, and companion tooling model.
---
# Agentic Starter

`agentic_starter` is an intentionally empty repository template for new projects that want structure and context before implementation.

It is designed to be forked or copied, then filled in with project-specific intake notes, architecture, roadmap, goals, and implementation plans. The value of this repository is the documentation workflow and agent collaboration structure, not prebuilt application code.

## How To Use This Starter

This template works best when the starting input is messy. In practice, that often means a long voice-dictated monologue, rough notes, or an existing design document that captures everything you want out of the project: the goal, users, tech stack, constraints, dislikes, preferred patterns, deployment model, visual direction, and the tradeoffs you care about.

The point is not to make that first pass neat. The point is to get the real intent out of your head and into text.

Put durable raw intake in `Documentation/tier0/`, then use a high-capability planning model to do the expensive synthesis work. Have it turn the messy human input into maintained project context by filling in `Documentation/design.md`, `Documentation/milestones.md`, and one or more `Documentation/goals*.md` files. This is where the AI earns its keep: not by guessing implementation details in a vacuum, but by integrating human intent into a clean five-tier framework that future agent runs can rely on.

After that, review and correct the documents by hand. This step matters. If the design and goal files are wrong, every later agent session inherits those mistakes.

Once the context is in place, future work becomes much simpler. Instead of restating the whole project in every conversation, you can give a focused instruction such as:

> Implement Goal 3.4 as specified in `goals3.md`.

That keeps context windows cleaner, reduces drift, and lets the agent stay focused on the current task instead of repeatedly rebuilding project understanding from scratch.

### Tier 0 Intake Instructions

Tier 0 is the raw intake layer for dictated notes, rough design documents, and addenda. It is not just a one-time bootstrap. Return to Tier 0 whenever the project vision changes, new ideas arrive, milestones need to split or merge, goals need to move, or implementation plans need to be regenerated from updated direction.

Common Tier 0 sources include:

- long voice-dictated project seeds
- supplemental design addenda
- notes captured while commuting, exercising, doing chores, or thinking away from the keyboard
- revised scope, deleted milestones, reordered goals, and implementation-plan corrections
- comparison notes from conversations with ChatGPT, Gemini, Grok, or other AI tools

Agents should treat Tier 0 as source material to synthesize into maintained context, not as the authoritative project state. The maintained source of truth lives in Tiers 1 through 4 after the intake has been reviewed and integrated.

## The Five-Tier Context System

| Tier | Layer | Location | Purpose |
| --- | --- | --- | --- |
| 0 | Raw Intake and Addenda | `Documentation/tier0/` | Messy source notes, dictated seeds, and recurring supplemental vision |
| 1 | Design | `Documentation/design.md` | Project architecture, principles, constraints, and system shape |
| 2 | Milestones | `Documentation/milestones.md` | Roadmap stages and milestone intent |
| 3 | Goals | `Documentation/goals*.md` | Specific deliverables, acceptance criteria, scope, and status |
| 4 | Implementation Plans and Handovers | `Documentation/implementation_plans/` | Task-ready execution plans and phase handovers |

When this repository says "context files," it means this five-tier system.

## Context Maintenance Expectations

Expect to spend real development time maintaining, correcting, and extending the project context in this repository. That is not overhead. It is the management layer that makes the rest of the workflow effective.

The developer's role here is leadership and delegation. Define the work clearly, document the constraints, specify the tools and standards, break the problem into milestones and goals, and keep that context accurate as the project evolves.

There are two equally bad failure modes. The first is treating the AI like a confused junior and hoping vague prompts will somehow produce precise work. The second is acting like an impatient manager who wants perfect output immediately but refuses to provide direction, acceptance criteria, or usable feedback. Both approaches fail for the same reason: the system can only execute well against clear intent.

Good AI output requires good leadership. That means setting expectations, giving concrete instructions, revising the plan when reality changes, and investing in the documentation that future sessions will rely on. If that discipline feels excessive, this workflow is probably being used incorrectly.

The mindset here is closer to deliberate engineering leadership than improvisational prompting. Books like `Radical Candor`, `Software Engineering at Google`, and `The Pragmatic Programmer` are more relevant to this workflow than arguments about clever prompting tricks.

## Companion Tooling

This starter is designed to pair well with the sibling `agentic_tooling` repository, but it does not require it.

- `agentic_starter` owns per-project context: intake, design, milestones, goals, implementation plans, handovers, and wiki notes.
- `agentic_tooling` owns reusable agent capabilities: shared rules, skills such as `commit-log`, workflow-skills, specialist agents, and prompt-development source material.

Custom tooling can copy assets from `agentic_tooling` into the locations each agentic IDE expects. This template documents the relationship conceptually so new projects remain IDE-agnostic and usable even when the companion tooling is not installed.

## What This Template Provides

- A five-tier context workflow centered on `Documentation/tier0/`, `Documentation/design.md`, `Documentation/milestones.md`, `Documentation/goals*.md`, and `Documentation/implementation_plans/`
- An optional temporary agent scratchpad in `Documentation/AgentThinking.md`
- A small wiki area for operational reference notes
- Repository instructions in [AGENTS.md](AGENTS.md)
- Compatibility with external shared rules, skills, workflows, and specialist agents when available

## Starter Workflow

1. Fork or copy this repository for a new project.
2. Rename the project in `README.md` and `Documentation/design.md`.
3. Add raw project notes or addenda under `Documentation/tier0/`.
4. Synthesize the intake into design, milestones, and goals.
5. Add implementation plans only when a task is ready for execution.
6. Keep `AgentThinking.md` temporary and lightweight.

## Repository Layout

```text
agentic_starter/
|-- AGENTS.md
|-- README.md
`-- Documentation/
    |-- AgentThinking.md
    |-- agenticworkflow.md
    |-- design.md
    |-- laws.md
    |-- milestones.md
    |-- goals1.md
    |-- tier0/
    |   `-- TIER0_NOTE_TEMPLATE.md
    |-- implementation_plans/
    `-- wiki/
```

## Key Documents

| Document | Purpose |
| --- | --- |
| [Documentation/laws.md](Documentation/laws.md) | Constitutional code quality and security laws — loaded first by all agents |
| [Documentation/tier0/README.md](Documentation/tier0/README.md) | Tier 0 raw intake and addendum guidance |
| [Documentation/design.md](Documentation/design.md) | Tier 1 design and architecture template |
| [Documentation/milestones.md](Documentation/milestones.md) | Tier 2 roadmap and milestone template |
| [Documentation/goals1.md](Documentation/goals1.md) | Tier 3 goals template for the first milestone |
| [Documentation/implementation_plans/IMPLEMENTATION_PLAN_TEMPLATE.md](Documentation/implementation_plans/IMPLEMENTATION_PLAN_TEMPLATE.md) | Tier 4 implementation-plan template |
| [Documentation/agenticworkflow.md](Documentation/agenticworkflow.md) | Rules for how AI agents should work in this repository |
| [Documentation/AgentThinking.md](Documentation/AgentThinking.md) | Optional temporary scratchpad for longer tasks |
| [Documentation/wiki/home.md](Documentation/wiki/home.md) | Wiki navigation hub |

## External Tooling Workflow

This template is meant to work with IDE-agnostic external tooling when available.

- Shared rules should be selected from the companion tooling's rules index or equivalent installed rule location.
- Reusable skills such as `commit-log` should come from installed global skills when present.
- Workflow-skills and specialist agents can be used when the task clearly benefits from them.
- Repository-local instructions remain authoritative when they conflict with shared tooling.

Those references are intentional and should remain part of the workflow even when the reusable tooling lives outside this repository.

## What This Repository Is Not

- It is not a sample application.
- It does not assume a fixed runtime or framework.
- It does not require the sibling `agentic_tooling` repository to exist.
- It should not keep stale project-specific implementation plans, secrets, or architecture details after being generalized into a template.
