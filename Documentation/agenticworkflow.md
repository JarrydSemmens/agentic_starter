---
version: 1.1
owner: "Your Name"
repo: "your-repo"
description: Workflow guide for how AI agents should use the repository's five-tier context system, phased handovers, companion tooling, and execution process.
---
# Agentic Workflow

**How AI agents collaborate with the developer in this repository**

[Back to Design Specification](design.md)

---

## Five-Tier Context Hierarchy

The project uses a five-tier context system that moves from raw human intent to concrete implementation work.

```text
Tier 0: Raw Intake and Addenda (tier0/)
  |  Dictated notes, rough source material, and recurring supplemental vision
  |
  +--> Tier 1: Design Specification (design.md)
  |     Project-wide architecture, principles, and constraints
  |
  +--> Tier 2: Milestones (milestones.md)
  |     Thematic groupings of related deliverables
  |
  +--> Tier 3: Goals (goals1.md, goals2.md, ...)
  |     Individual features, bugs, or significant changes
  |
  +--> Tier 4: Implementation Plans and Execution Records (implementation_plans/)
        Task-specific implementation plans, implementation logs, and optional provenance artifacts
```

When this repository refers to "context files," it means this five-tier system.

### Tier 0 Intake

Tier 0 is raw source material. It may be an initial dictated design document, a later addendum, a transcript from a voice-based AI session, or notes captured while away from the keyboard.

Use Tier 0 when:

- starting a new project from messy human intent
- enriching existing design, milestone, or goal documents
- splitting, deleting, merging, or reordering milestones
- revising goals and acceptance criteria after the vision changes
- regenerating or correcting Tier 4 implementation plans

Tier 0 is recurring input, not archival clutter. However, it is not authoritative after synthesis. Agents must integrate relevant Tier 0 material into Tiers 1 through 4 and preserve explicit assumptions, open questions, and source links where they matter.

### Goal Variants

When a goal requires research or prototyping of multiple alternative approaches, use lettered variants such as `Goal 1.2A`, `Goal 1.2B`, and `Goal 1.2C`. Only one variant is ultimately selected; the others should be marked as failed, rejected, or superseded.

Variants answer: *Which approach should we use?*

### Goal Phases

When a goal is too large for a single pass, split it into sequential phases such as Phase 1, Phase 2, and Phase 3. Phases are execution steps for one chosen approach, not competing alternatives.

Phases answer: *What order do we build this in?*

---

## WISC as Supporting Practice

WISC (Write, Isolate, Select, Compress) is useful vocabulary for the discipline this starter already encourages. Treat it as a supporting practice, not a replacement name for the repository.

| WISC Step | How this starter applies it |
| --- | --- |
| Write | Externalize memory into Tier 0 notes, maintained specs, implementation plans, implementation logs, progress files, and opt-in handovers. |
| Isolate | Keep work slices small, use focused agent sessions, and use specialist agents or subagents for bounded research and execution. |
| Select | Load only the context needed for the task instead of dumping every document into every prompt. |
| Compress | Summarize long work into maintained docs, phase handovers, progress files, and compacted state before context quality degrades. |

The practical goal is fewer hallucinations, less context pollution, smaller tasks, and cleaner iterative development.

---

## Phase Execution and Context Management

Phase splitting exists to manage AI context limitations. A single conversation should not carry the entire history of a large feature if a smaller, cleaner handoff can do the job.

### AgentThinking.md

`AgentThinking.md` is an optional scratchpad for temporary working notes during a long or complex task.

**Rules:**

- Do not use `AgentThinking.md` unless explicitly instructed or genuinely needed for task continuity.
- Treat it as temporary working memory, not as authoritative project documentation.
- Reset or replace its contents when switching to a different feature, goal, or bug.
- Avoid committing it unless preserving context across separate AI runs is important.

### Phase Handover Documents

At the end of a phase, create a handover document so a fresh AI session can continue the work without depending on prior chat history.

**Location:** Prefer the active task folder under `Documentation/implementation_plans/`. If the work predates folder-based plans, use `Documentation/implementation_plans/`.

**Naming convention:**

| Context | Naming Pattern | Example |
| --- | --- | --- |
| Goal-based work | `GOAL_<M>_<G>_<variant>_handover_from_phase<N>.md` | `GOAL_1_3_A_handover_from_phase1.md` |
| Bug fix | `BUG_<short-slug>_handover_from_phase<N>.md` | `BUG_timeout_error_handover_from_phase1.md` |
| Feature without a goal | `FEATURE_<short-slug>_handover_from_phase<N>.md` | `FEATURE_export_csv_handover_from_phase1.md` |

**Minimum contents:**

1. What was completed in this phase
2. What exists in the repository now
3. Explicit next steps
4. Key decisions and rationale
5. Known issues, risks, or open questions
6. Important files and sections to read next

### How the Next AI Starts a Later Phase

1. Read the handover document first.
2. Then read only the necessary project documents:
   - `design.md`
   - `milestones.md` when scope or roadmap matters
   - the relevant goals file
   - `tier0/` files only when the task involves intake synthesis or rationale recovery
   - `AgentThinking.md` only if it was used and is still relevant
3. Continue from the documented repo state rather than reconstructing the full prior conversation.

---

## Optional Plan Artifacts

Every Tier 4 implementation-plan folder should contain:

```text
plan.md
implementation-log.md
```

Other provenance artifacts are opt-in. Use them only when the task, user, plan, or installed skill explicitly calls for them.

| Artifact | Created By | Purpose |
| --- | --- | --- |
| `complaining.md` | `complaining` skill | Records actionable friction, blockers, ambiguity, risky assumptions, and tooling failures |
| `thinking.md` | `thinking-out-loud` skill | Records sanitized investigation notes, discovered constraints, useful observations, and revisit items |
| `evidence.md` | `evidence` skill | Indexes changed files, validation, commits, planning inputs, and unverified claims |
| `handover/shallow-handover.md` | `handover` skill | Transfers ownership back to the human or forward to another agent |

Do not create these optional files by default.

---

## Companion Repository: agentic_rails_tooling

`agentic_rails_context_starter` is the project-local context system. The sibling `agentic_rails_tooling` repository is the recommended reusable capability system. A generated project should work without `agentic_rails_tooling`, but it can become much stronger when those reusable assets are installed into the agentic IDE's expected locations.

Use this conceptual split:

| Layer in `agentic_rails_tooling` | Purpose |
| --- | --- |
| `rules/` | Concise standards, style guidance, and stack-specific rules selected just in time. |
| `skills/` | Reusable task capabilities such as `commit-log`, compatibility checks, and focused process guidance. |
| Workflow-skills | Orchestrated processes such as implementation-plan generation or plan execution. These may live under `skills/` when the IDE does not support a separate workflow primitive. |
| `agents/` | Specialist personas and reference packs for domains such as WPF, gamedev, or XNA. |
| `prompt_dev/` | Source prompt material used to generate or evolve reusable tooling artifacts. |

Custom tooling may copy these assets into locations such as global skill folders, IDE rule directories, or provider-specific agent folders. This repository should describe that relationship without hardcoding a full per-IDE installation matrix.

Repository-local context wins when it conflicts with reusable tooling. Shared rules, skills, workflow-skills, and agents supplement the project; they do not replace its design, milestones, goals, or implementation plans.

---

## Multi-Model Orchestration

This project uses capability-tiered model allocation so the level of model effort matches the difficulty of the task.

| Task Domain | Model Tier | Examples |
| --- | --- | --- |
| Architecture and planning | High-capability | design decisions, milestone definition, major refactors |
| Intake synthesis | High-capability | turning Tier 0 notes into maintained context |
| Implementation plans | High-capability | detailed Tier 4 job packets |
| Implementation execution | Mid-capability | routine coding, doc updates, scoped feature work |
| Review and analysis | High-capability | code review, system analysis, deeper synthesis |

### Actual Workflow

1. The developer researches, dictates, and captures requirements into Tier 0.
2. Requirements are brought into the agentic IDE workflow.
3. A high-capability model revises plans against the on-disk repository and current documentation.
4. Tier 1 through Tier 3 documents are updated as needed.
5. A Tier 4 implementation plan is created when work is ready for execution.
6. An implementation-focused agent executes against that plan and the repository.
7. Handovers or progress files compress state when the work spans phases or sessions.

---

## Documentation Lifecycle

- `tier0/*.md` contains raw intake and addenda that should be synthesized before implementation decisions rely on it.
- `design.md`, `milestones.md`, and the goals files are authoritative and maintained.
- `implementation_plans/` contains task folders with `plan.md` and `implementation-log.md`. Optional skill-generated artifacts may live beside those files.
- `AgentThinking.md` is temporary and should stay lightweight.
- Wiki and reference material support the project but may become stale; check them against the source of truth before relying on them.

---

## Agent Operational Guidelines

When assigned work in this repository:

1. Check for a relevant handover document first if the work is phased.
2. Read the minimum necessary context in this order:
   - `laws.md` always — constitutional authority for code quality, security, and architectural constraints
   - `design.md`
   - `milestones.md` when scope or roadmap matters
   - the relevant goals file
   - `implementation_plans/*.md` when a task plan exists
   - `tier0/*.md` only when the task involves intake, enrichment, major scope revision, or rationale recovery
   - `AgentThinking.md` only when explicitly needed
3. If a Tier 4 implementation plan exists for the task, follow it closely.
4. Keep repository structure, naming, and documentation conventions consistent.
5. Update status fields in milestone and goal documents when the task requires it.
6. When ending a phase mid-stream, create a handover document only when a handover is needed or explicitly requested.
7. Use installed reusable tooling only when it is relevant and available; do not make the project depend on external tooling silently.

---

## IDE-Specific Agent Rules

When working within agentic IDEs such as Codex, Claude, Cursor, Windsurf, Gemini CLI, or similar tools, additional language-specific, framework-specific, skill, or agent rules may exist outside this repository.

These rules supplement the repository docs. Keep the repository workflow authoritative, but honor relevant external tooling when it has been installed for the current IDE.
