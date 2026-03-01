# Agentic Starter

version: 1.0    
owner: "Your Name"    
repo: "your-repo"    

---

`agentic_starter` is an intentionally empty repository template for new projects that want structure and context before implementation.

It is designed to be forked or copied, then filled in with project-specific architecture, roadmap, goals, and implementation plans. The value of this repository is the documentation workflow and agent collaboration structure, not prebuilt application code.

## How To Use This Starter

This template works best when the starting input is messy. In practice, that often means a long voice-dictated monologue, rough notes, or an existing design document that captures everything you want out of the project: the goal, users, tech stack, constraints, dislikes, preferred patterns, deployment model, visual direction, and the tradeoffs you care about.

The point is not to make that first pass neat. The point is to get the real intent out of your head and into text.

Once you have that raw material, use a high-capability planning model to do the expensive thinking work. Have it turn the messy human input into structured project context by filling in `Documentation/design.md`, `Documentation/milestones.md`, and `Documentation/goals1.md`. This is where the AI earns its keep: not by guessing implementation details in a vacuum, but by integrating a pile of human scrawl into a clean multi-tier framework that future agent runs can rely on.

After that, review and correct the documents by hand. This step matters. If the design and goal files are wrong, every later agent session inherits those mistakes.

Once the context is in place, future work becomes much simpler. Instead of restating the whole project in every conversation, you can give a focused instruction such as:

> Implement Goal 3.4 as specified in `goals3.md`.

That keeps context windows cleaner, reduces drift, and lets the agent stay focused on the current task instead of repeatedly rebuilding project understanding from scratch.

## Context Maintenance Expectations

Expect to spend roughly half of your development time maintaining, correcting, and extending the project context in this repository. That is not overhead. It is the management layer that makes the rest of the workflow effective.

The developer's role here is leadership and delegation. Define the work clearly, document the constraints, specify the tools and standards, break the problem into milestones and goals, and keep that context accurate as the project evolves.

There are two equally bad failure modes. The first is treating the AI like a confused junior and hoping vague prompts will somehow produce precise work. The second is acting like an impatient manager who wants perfect output immediately but refuses to provide direction, acceptance criteria, or usable feedback. Both approaches fail for the same reason: the system can only execute well against clear intent.

Good AI output requires good leadership. That means setting expectations, giving concrete instructions, revising the plan when reality changes, and investing in the documentation that future sessions will rely on. If that discipline feels excessive, this workflow is probably being used incorrectly.

The mindset here is closer to deliberate engineering leadership than improvisational prompting. Books like `Radical Candor`, `Software Engineering at Google`, and `The Pragmatic Programmer` are more relevant to this workflow than arguments about clever prompting tricks.

## What This Template Provides

- A documentation-first workflow centered on `Documentation/design.md`, `Documentation/milestones.md`, and `Documentation/goals*.md`
- A Tier 4 implementation plan area in `Documentation/implementation_plans/`
- An optional temporary agent scratchpad in `Documentation/AgentThinking.md`
- A small wiki area for operational reference notes
- Repository instructions in [AGENTS.md](AGENTS.md)
- Compatibility with the external shared-rules and Cursor-rules workflow

## Starter Workflow

1. Fork or copy this repository for a new project.
2. Rename the project in `README.md` and `Documentation/design.md`.
3. Replace placeholders in the design, milestones, and goals documents.
4. Add implementation plans only when a task is ready for execution.
5. Keep `AgentThinking.md` temporary and lightweight.

## Repository Layout

```text
agentic_starter/
|-- AGENTS.md
|-- README.md
`-- Documentation/
    |-- AgentThinking.md
    |-- agenticworkflow.md
    |-- design.md
    |-- milestones.md
    |-- goals1.md
    |-- implementation_plans/
    `-- wiki/
```

## Key Documents

| Document | Purpose |
| --- | --- |
| [Documentation/design.md](Documentation/design.md) | Tier 1 design and architecture template |
| [Documentation/milestones.md](Documentation/milestones.md) | Tier 2 roadmap and milestone template |
| [Documentation/goals1.md](Documentation/goals1.md) | Tier 3 goals template for the first milestone |
| [Documentation/agenticworkflow.md](Documentation/agenticworkflow.md) | Rules for how AI agents should work in this repository |
| [Documentation/AgentThinking.md](Documentation/AgentThinking.md) | Optional temporary scratchpad for longer tasks |
| [Documentation/implementation_plans/IMPLEMENTATION_PLAN_TEMPLATE.md](Documentation/implementation_plans/IMPLEMENTATION_PLAN_TEMPLATE.md) | Tier 4 implementation-plan template |
| [Documentation/wiki/home.md](Documentation/wiki/home.md) | Wiki navigation hub |

## External Rules Workflow

This template is meant to work with an external shared-rules repository and with Cursor-compatible rules when present.

- Shared rules are selected through `D:\Code Projects\windsurf_rules\index.md`
- Cursor compatibility remains part of the workflow through `.cursorrules` support when used in a project that includes it

Those references are intentional and should remain part of the workflow even when the shared rules live outside this repository.

## What This Repository Is Not

- It is not a sample application.
- It does not assume a fixed runtime or framework.
- It should not keep stale project-specific implementation plans, secrets, or architecture details after being generalized into a template.
