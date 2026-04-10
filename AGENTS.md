---
version: 1.2    
owner: "Your Name"    
repo: "your-repo"    
description: Mandatory repository-specific instructions that tell AI coding agents how to load context, work within scope, and follow project standards.    
---
# Agent Instructions

This file provides mandatory guidance for AI coding agents. Follow these rules in every interaction.

---

## 0: Required Startup Workflow

Before making changes, load context in this order:

### 0.1: Repository Context Order

1. Review `Documentation/laws.md`. This is the constitutional authority for all code quality, security, and architectural constraints. Laws defined there are inviolable and override any conflicting guidance in this file.
2. Review `Documentation/agenticworkflow.md`. This is the mandatory workflow standard for this repository.
3. Review `Documentation/design.md`. This is always required baseline context.
4. When work involves drafting commit logs or preparing to commit, use the `commit-log` skill at `%USERPROFILE%\\.agents\\skills\\commit-log\\SKILL.md` instead of repository-local commit log instructions. By default, output the commit log in chat for the user to copy. Only perform an actual commit when the user explicitly asks for one.
5. Review `Documentation/milestones.md` when the task touches roadmap, scope, or feature planning.
6. Review the relevant goals file for the feature being discussed or implemented.
7. If continuing phased work, review the relevant handover document in `implementation_plans/` first, as directed by `Documentation/agenticworkflow.md`.

## 0.2: Repository Expectations

- Follow the spec-driven workflow defined in `Documentation/agenticworkflow.md`.
- Treat `Documentation/design.md` as always-required context.
- Use `Documentation/milestones.md` and the goals documents to anchor implementation scope and acceptance criteria.
- Do not execute pull or push operations in any VCS.
- You may stage and commit changes when explicitly requested. Push is never permitted.
- When drafting a commit log or creating a commit, use the `commit-log` skill at `%USERPROFILE%\\.agents\\skills\\commit-log\\SKILL.md`. Default to outputting the commit log in chat unless the user explicitly asks you to create the commit.

## 0.3: Product and assembly versioning

All first-party assemblies in the solution share a four-part numeric identity **W.X.Y.Z** (exposed as `AssemblyVersion` / `FileVersion` and the MSBuild `Version` property where applicable).

| Part | Meaning |
| --- | --- |
| **W** | **Major release** - increments only for a significant product release the organization treats as major (for example a 1.0 GA). **0** means no major release has been shipped yet. |
| **X** | **Milestone** - the current milestone number from [Documentation/milestones.md](Documentation/milestones.md), or the highest milestone the team is actively working against. |
| **Y** | **Highest completed goal** - within that milestone, the largest goal index that is complete. Example: Milestone 2 with Goals 2.1-2.6 complete and 2.7 not started yields **Y = 6**. When a new milestone begins, reset **Y** to **0** until the first goal in that milestone is completed, then advance as goals complete. |
| **Z** | **Reserved** - default **0**. May later be used for a build or commit ordinal (for example CI setting the fourth part from pipeline build number). Until automation exists, keep **Z** at **0**. |

**Example:** Pre-1.0 work on Milestone 2 with Goal 2.6 as the latest completed goal uses **0.2.6.0**.

**Maintenance:** When you complete a goal or change milestone scope, update version properties in every `*.csproj` under `Source/` so all libraries stay aligned. Keep this section aligned with the table above.

---

## 1. Agent Behaviour

### 1.1 Think Before Coding

Don't assume. Don't hide confusion. Surface tradeoffs.

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them — don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

### 1.2 Simplicity First

Minimum code that solves the problem. Nothing speculative.

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- Do not expose internal tuning knobs as user-facing editor controls unless the user explicitly asked for them. Keep them as code defaults or constants until they are proven necessary.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

### 1.3 Surgical Changes

Touch only what you must. Clean up only your own mess.

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it — don't delete it.

When your changes create orphans:
- Remove imports, variables, and functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: every changed line should trace directly to the user's request.

### 1.4 Goal-Driven Execution

Define success criteria. Loop until verified.

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

- For modal or editor features, define both the activation path and the cleanup path up front. If loading or enabling one feature automatically turns on another, clearing or disabling it must explicitly unwind that state.

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

### 1.5 Comments

- Write comments that explain "why", not "what".
- A few high-level comments explaining the purpose of classes or methods is helpful.
- Comments explaining tricky or non-obvious code are helpful.
- Avoid comments that are redundant with the code. Do not comment before each line explaining what it does.
- Do not use formal C# XML doc comments unless it is an important public-facing interface or API.

---

## 2. Refactoring Rules

Immediate refactoring is required when:
- A class grows beyond a single responsibility.
- Methods perform multiple actions.
- Logic is duplicated across scripts.
- Large conditional blocks control behaviour.

Refactoring must prioritise:
- Composition over inheritance.
- Small, focused classes.
- Clear ownership of responsibilities.

Apply the Rule of Three — refactor after something is duplicated three times, not before.

Before adding significant functionality to a large or monolithic file, consider a structural refactor with no intended behaviour changes first. Splitting a file into smaller, composable parts before feature work is often safer than mixing the refactor and the new behaviour in one step. Verify the refactor independently before layering new functionality on top.
