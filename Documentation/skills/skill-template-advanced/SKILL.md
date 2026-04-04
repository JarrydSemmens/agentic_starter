---
name: skill-name
description: Replace this with a clear description of what the skill does and when to use it. Explain the task domains it covers and the concrete situations that should trigger the skill.
---

# Advanced Modular Skill Template

This is a stripped, reusable skill template for domains that are too broad to fit cleanly in one file.

Use this structure when the skill should act like an expert router instead of a knowledge dump:

- Keep the core workflow and stance in this file
- Keep deeper domain truth in `references/`
- Load only the smallest relevant reference set for the current task

The goal is to help the agent identify the problem first, then pull in only the domain guidance that is actually needed.

## Working Style

Start by identifying what kind of problem is being solved. Do not load every reference file up front. Read the smallest relevant set.

Think in this order:

1. What is the user actually trying to build, change, debug, restore, or evaluate?
2. Which domain boundary is in play: principles, architecture, abstractions, workflows, tooling, testing, diagnostics, or performance?
3. What belongs in the core solution, what belongs in supporting infrastructure, and what belongs in process or validation?
4. Which references give enough domain truth without loading unrelated context?

Prefer the least complex solution that cleanly solves the problem. Treat this skill as a catalogue first and a deep reference set second.

## Default Stance

- Prefer clarity over cleverness.
- Prefer the smallest abstraction that preserves future readability.
- Prefer strong boundaries between concerns.
- Prefer explicit workflows over improvised sequences.
- Prefer testing and diagnostics that prove behavior rather than relying on confidence.
- Prefer loading one focused reference file over scanning the whole skill.
- Prefer replacing placeholder guidance with real domain truth only when creating a concrete derived skill.

## Reference Map

Load these references only when they are relevant.

### Strategy and Architecture

- [references/foundations-and-principles.md](references/foundations-and-principles.md)
  Use when defining the domain stance, core design principles, tradeoffs, and non-negotiable rules for the skill.
- [references/architecture-and-boundaries.md](references/architecture-and-boundaries.md)
  Use when the task involves responsibility boundaries, system shape, layering, module ownership, or separation of concerns.
- [references/patterns-and-abstractions.md](references/patterns-and-abstractions.md)
  Use when choosing between implementation patterns, reusable abstractions, extension points, or API shapes.

### Execution and Tooling

- [references/workflows-and-pipelines.md](references/workflows-and-pipelines.md)
  Use when the work depends on a repeatable execution flow, authoring sequence, content pipeline, or operational checklist.
- [references/tools-and-integrations.md](references/tools-and-integrations.md)
  Use when the task touches external tools, build steps, editors, automation, data formats, or third-party integrations.

### Validation and Runtime Behavior

- [references/quality-and-testing.md](references/quality-and-testing.md)
  Use when defining acceptance criteria, regression coverage, test strategy, or quality gates.
- [references/debugging-and-diagnostics.md](references/debugging-and-diagnostics.md)
  Use when investigating failures, tracing behavior, narrowing regressions, or making issues easier to observe.
- [references/performance-and-reliability.md](references/performance-and-reliability.md)
  Use when the task touches runtime cost, stability, resilience, scale limits, memory behavior, or long-term maintainability under load.

## Load Combinations

Typical combinations:

- Initial skill shaping: `foundations-and-principles.md` + `architecture-and-boundaries.md`
- API or system design work: `architecture-and-boundaries.md` + `patterns-and-abstractions.md`
- Process-heavy execution work: `workflows-and-pipelines.md` + `tools-and-integrations.md`
- Quality pass: `quality-and-testing.md` + the domain reference that introduced the behavior
- Debugging pass: `debugging-and-diagnostics.md` + the domain reference closest to the failure
- Performance pass: `performance-and-reliability.md` + `architecture-and-boundaries.md`
- Tool-driven troubleshooting: `tools-and-integrations.md` + `debugging-and-diagnostics.md`

## Execution Checklist

When using this skill:

1. Identify the real problem before loading references.
2. Load only the smallest reference set that gives enough domain truth.
3. Keep decisions aligned with the skill's stated principles and boundaries.
4. Prefer reusable patterns only when they simplify the work instead of obscuring it.
5. Verify behavior with tests, diagnostics, or another concrete check.
6. Keep the skill modular by moving detailed guidance into references rather than bloating this file.

## Do Not

- Do not turn this file into a full knowledge dump.
- Do not load every reference file unless the task truly spans the whole domain.
- Do not leave placeholder text in a derived skill once real domain guidance exists.
- Do not spread the same guidance across multiple references when one file should clearly own it.
- Do not invent abstractions, workflows, or rules that the domain does not need.
