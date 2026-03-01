# Agentic Starter

version: 1.0    
owner: "Your Name"    
repo: "your-repo"    

---

`agentic_starter` is an intentionally empty repository template for new projects that want structure and context before implementation.

It is designed to be forked or copied, then filled in with project-specific architecture, roadmap, goals, and implementation plans. The value of this repository is the documentation workflow and agent collaboration structure, not prebuilt application code.

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
