# Agent Instructions

This file provides mandatory guidance for AI coding agents. Follow these rules in every interaction.

---

## 0: Required Startup Workflow

Before making changes, load context in this order:

### 0.1: Review the shared rules index at `D:\Code Projects\windsurf_rules\index.md`. If the windsurf rules repo cannot be found at the default location, try here: `C:\Projects\windsurf_rules`. The layout of the repositories is different on various workstations, and this location is valid on portable workstations. If you still cannot find it, go up on folder from the root directory of this project and look for `windsurf_rules`, it's usually there.
2. From that index, load only the rule files relevant to this repository and the current task.
3. Review `Documentation/agenticworkflow.md`. This is the mandatory workflow standard for this repository.
4. Review `Documentation/design.md`. This is always required baseline context.
5. Review `Documentation/commit_log_template.md` when work involves staging changes or drafting commit logs.
6. Review `Documentation/milestones.md` when the task touches roadmap, scope, or feature planning.
7. Review the relevant goals file for the feature being discussed or implemented.
8. If continuing phased work, review the relevant handover document in `implementation_plans/` first, as directed by `Documentation/agenticworkflow.md`.

### 0.2: Shared Rules Policy

- Do not bulk-read all files under `D:\Code Projects\windsurf_rules\`.
- Use `D:\Code Projects\windsurf_rules\index.md` to choose the minimum relevant rule set.
- Apply shared rules together when appropriate, for example C# plus WPF.
- Repository-local instructions override shared rules when they conflict.
- Task-specific instructions override general rules when they conflict.

## 0.3: Repository Expectations

- Follow the spec-driven workflow defined in `Documentation/agenticworkflow.md`.
- Treat `Documentation/design.md` as always-required context.
- Use `Documentation/milestones.md` and the goals documents to anchor implementation scope and acceptance criteria.
- Do not execute pull, push, or commit operations in any VCS.
- You may stage all tracked current changes only when explicitly requested.
- When staging is requested, draft the commit message using `Documentation/commit_log_template.md`.
- In Git workflows, commit message text is not part of staged state; provide drafted message text for the user to apply in their client.

## 0.4: Product and assembly versioning

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

## 2. Core Philosophy

These principles drive every decision. When two rules conflict, resolve by applying them in priority order.

1. **Functional First** — Code exists to fulfil a purpose. Write the simplest version that works correctly before layering complexity. Apply Occam's Razor.
2. **Readable** — Code is read at least ten times more than it is written. Optimise for the reader, not the writer. Never write the cleverest thing you can — if you write at the limit of your ability, you will not be able to debug it. Use descriptive names, prefer explicit over implicit, keep code density low.
3. **Understandable** — Write software that fits in your head. Working memory holds roughly four items. Separate concerns, keep nesting shallow, keep functions short. Follow the Principle of Least Astonishment — a method called `MakeCookies` must never return `Potato` objects.
4. **Reliable** — Code should be hard to break. Loosely coupled, testable via dependency inversion, covered by automated tests. Every bug fix ships with a regression test.
5. **Efficient** — Games are real-time software with hard frame-rate targets. But premature optimisation is still the root of all evil. Write correct code first. Do not optimise until a profiler measurement shows a bottleneck, and always verify that the optimisation had the intended effect.
6. **Iterative** — Nobody gets it right the first time. Apply the Rule of Three — refactor only after something is duplicated three times. Use Red-Green-Refactor. Each commit should leave the codebase better than it was.
7. **Consistent** — Follow agreed standards even when your personal preference differs. Consistency reduces cognitive load and onboarding time.

---

## 3. SOLID Principles

All code must respect SOLID:

- **Single Responsibility** — A class has one and only one reason to change. If it handles more than one concern, it must be split. Do not mix gameplay logic, UI logic, persistence, input handling, animation, or infrastructure in a single class.
- **Open/Closed** — Open for extension, closed for modification. Prefer composition, interfaces, and new classes over modifying existing stable code.
- **Liskov Substitution** — Derived types must be fully substitutable for their base types without breaking behaviour.
- **Interface Segregation** — Interfaces must be small and focused. Never force a class to implement methods it does not use.
- **Dependency Inversion** — Depend on abstractions (interfaces), not concrete implementations. Use constructor injection for plain C# classes and serialized references or installers for MonoBehaviours.

Apply these as guiding heuristics. Game code sometimes benefits from pragmatic shortcuts — but document them and revisit them.

---

## 4. Refactoring Rules

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

---

## 5. Definition of Done

A change is complete only when:

- [ ] Explicit variable types are used everywhere (no `var` or `auto`)
- [ ] SOLID principles are respected
- [ ] Each class has a single responsibility
- [ ] Each method performs a single action
- [ ] Serialized references are validated in initialisation
- [ ] Code is readable, maintainable, and refactor-ready
- [ ] Tests exist for new features and bug fixes
- [ ] The console is clean (zero warnings, zero errors)
- [ ] Every changed line traces directly to the user's request
- [ ] No unnecessary abstractions, features, or "improvements" beyond scope