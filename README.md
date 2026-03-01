# Agentic Starter

version: 1.0    
owner: "Your Name"    
repo: "your-repo"    

---

`agentic_starter` is an intentionally empty repository template for new projects that want structure and context before implementation.

It is designed to be forked or copied, then filled in with project-specific architecture, roadmap, goals, and implementation plans. The value of this repository is the documentation workflow and agent collaboration structure, not prebuilt application code.

## HOW TO USE THE AGENTIC STARTER

This works best if you have a great big messy monologue with an AI, or you have an existing design specification document.

Often, I'll build up mine by using ChatGPT voice mode, or Gemini Voice mode while riding my bicycle to work. I'll describe what I want, the tech I'll use, approaches I want to investigate. I'll go on and on about how it helps, the expected outcome of the project and who will use it and why. I'll describe platforms, versions, unwanted patterns (like DI containers, or my hatred of python due to busted wheels) and all the other details about this project. I'll go on about colors, themes, how it's installed, if it's web tech in Node.js or a WPF app on dotnet 8.0 because it's LTS or anything else. I won't listen to the AI when dictating this stuff, since I just want it to listen. 

At the end, I'll ask it to summarise everything into a design document, and put it into a canvas so I can download this rough spec as a markdown file.

Then when I'm at my workstation with a fork or clone of this repo, I'll paste in that rough specification along with a prompt. The prompt will tell the agent in Windsurf\Cursor\Codex\Claude or whatever to populate all the non-specifics found in @design.md @milestones.md and @goals1.md with the project description I have given.

I'll use an expensive model, like Claude Opus, or Codex 5.3 high reasoning. Mistakes at this level will pollute the project forever.

Once all that is done, I'll read everything and correct things by hand. 

This planning session sets up highly detailed context going forward. I'll spend about half my time on maintaining, updating and refining these context files while I work.

The end result, is that I can have all this setup on my ROG Ally, and say in a fresh conversation:

> Implement goal 3.4 as per @goals3.md.

Then I stick the ROG in my backpack on low power mode, and bike ride home. When I get home, I'll have a feature done. Check it into git, and tell it to make another feature.

My context windows don't get clogged, my AI stays focused, and I stay in the fresh and effective part of the context windows while being able to do something else productive while projects built with this clank away at doing work I want.

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
