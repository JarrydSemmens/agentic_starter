# Agent Instructions

This repository uses a documentation-first workflow and a centralized shared-rules directory.

## Required Startup Workflow

Before making changes, load context in this order:

1. Review the shared rules index at `D:\Code Projects\windsurf_rules\index.md`. If the windsurf rules repo cannot be found at the default location, try here: `C:\Projects\windsurf_rules`. The layout of the repositories is different on various workstations, and this location is valid on portable workstations. If you still cannot find it, go up on folder from the root directory of this project and look for `windsurf_rules`, it's usually there.
2. From that index, load only the rule files relevant to this repository and the current task.
3. Review `Documentation/agenticworkflow.md`. This is the mandatory workflow standard for this repository.
4. Review `Documentation/design.md`. This is always required baseline context.
5. Review `Documentation/milestones.md` when the task touches roadmap, scope, or feature planning.
6. Review the relevant goals file for the feature being discussed or implemented.
7. If continuing phased work, review the relevant handover document in `implementation_plans/` first, as directed by `Documentation/agenticworkflow.md`.

## Shared Rules Policy

- Do not bulk-read all files under `D:\Code Projects\windsurf_rules\`.
- Use `D:\Code Projects\windsurf_rules\index.md` to choose the minimum relevant rule set.
- Apply shared rules together when appropriate, for example C# plus WPF.
- Repository-local instructions override shared rules when they conflict.
- Task-specific instructions override general rules when they conflict.

## Repository Expectations

- Follow the spec-driven workflow defined in `Documentation/agenticworkflow.md`.
- Treat `Documentation/design.md` as always-required context.
- Use `Documentation/milestones.md` and the goals documents to anchor implementation scope and acceptance criteria.
- Do not make git commits or alter repository history.
- You are forbidden from ever making a git pull, push or commit. The penalty is severe, painful and immediate.
