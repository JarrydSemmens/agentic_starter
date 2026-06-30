---
name: agenticworkflow
description: Workflow guide for how AI agents use the repository's seven-tier, backlog-driven, Scrum-aligned context system, scoring, orchestration, and execution process.
metadata:
  version: "2.0"
  agentic_rails_source_version: "2.0"
  owner: "Your Name"
  repo: "your-repo"
---
# Agentic Workflow

**How AI agents collaborate with the developer in this repository**

[Back to Design Specification](design.md)

---

## Seven-Tier Context Hierarchy

The project uses a seven-tier context system that moves from raw human intent to concrete, executable work. It is **backlog-driven and Scrum-aligned**: rough design and milestones are set up front, then work is planned close to execution by pulling only what is needed right now. The backlog is allowed to be messy. You refine and execute what is next, and you move forward rather than perpetually re-planning the whole project.

```text
Tier 0: Transcription (tier0/)
  |  Raw dictation. A brain-dump of the rough shape of a project. No structure imposed yet.
  |
  +--> Tier 1: Design (design.md)
  |     The whole deliverable, how it breaks into its largest pieces.
  |     The Milestones Index lives as a subsection here.
  |
  +--> Tier 2: Milestone (milestones/*.md)
  |     A macro-feature or major delivery phase. Each milestone doc is an
  |     index of a grouped collection of sprints. There are multiple milestone docs.
  |
  +--> Tier 3: Sprint (sprints/*.md)
  |     A time-bounded chunk of work toward a milestone with a clear deliverable.
  |     A milestone may require several sprints.
  |
  +--> Tier 4: Story (backlog/*.md, then scheduled into a sprint)
  |     One discrete work unit: a bug fix, a feature, a refactor. ~A dozen per sprint.
  |
  +--> Tier 5: Implementation Plan (implementation-plans/*/plan.md)
  |     The detailed, normalized "how-to" for executing one story.
  |     Carries the scoring metrics and any mitigation.
  |
  +--> Tier 6: Phases (optional)
        A fracture of a single implementation plan when one story is too
        large or risky to execute in one pass. Each phase is independently executable.
```

When this repository refers to "context files," it means this seven-tier system.

### Tier focus (one sentence each)

| Tier | Name | Focus / Output | Scrum equivalent |
| --- | --- | --- | --- |
| T0 | **Transcription** | Capture the raw, unstructured shape of a project. | Pre-planning / raw input |
| T1 | **Design** | Produce the application / whole deliverable, with the milestones index as a subsection. | Product vision / roadmap |
| T2 | **Milestone** | Produce a macro-feature or major phase; index its grouped sprints. | Theme / large initiative |
| T3 | **Sprint** | Deliver a time-bounded, coherent chunk toward a milestone. | Sprint |
| T4 | **Story** | Complete one discrete unit of work. | Story |
| T5 | **Implementation Plan** | Specify exactly how to execute one story, with scoring and mitigation. | Task breakdown |
| T6 | **Phase** *(optional)* | Execute one safe slice of an over-large story. | Sub-task / split delivery |

### Vocabulary rules

- The word **`goal`** is retired. The old "goal file" container is gone, and the old individual "goal" work unit is now a **Story**.
- Grouping is done by **Milestone** docs (T2). The time-bounded execution batch is the **Sprint** (T3). The discrete work unit is the **Story** (T4).
- The word **`task`** is **never** used as a tier name. Sub-agents already use "task" for items on their internal to-do lists; reusing it at the hierarchy level induces confusion.
- The system adopts standard Scrum nouns where they fit: **Design → Milestone → Sprint → Story**, with **Phases** as an optional split below the implementation plan.

### Migration from the old five-tier system

| Old (5-tier) | New (7-tier) | Action |
| --- | --- | --- |
| Transcriptions | Transcription (T0) | Kept; folder is `tier0/` |
| Design doc | Design (T1) | Kept; absorbs the milestones index as a subsection |
| Master breakdown / `milestones.md` | Milestone (T2) | Reframed as grouped sprint indexes; multiple docs under `milestones/` |
| — | Sprint (T3) | **New** time-bounded execution batch under `sprints/` |
| Goal files (`goals*.md`) / goals | Story (T4) | **Renamed**; container concept removed; stories live in `backlog/` then schedule into sprints |
| Implementation plans | Implementation Plan (T5) | Kept; gains estimates, scoring, and mitigation |
| — | Phases (T6) | **New**, optional fracture of an implementation plan |

---

## When to use the full system

The seven-tier system is heavy and only worth it for large projects. Small, discrete jobs (a reboot script, a one-off tool) skip most of it and go straight to a single implementation plan.

**The human is the judge** of whether a project warrants the full system. There is no automated project-scale gatekeeping. Do not build or invoke a validation step that estimates total project scale to decide tier depth.

---

## Planning workflow: how the tiers are built

### 1. Transcription to Design + Milestones (interactive)

1. **T0 Transcription:** dictate the rough shape of the project. Output: a rough Design doc. No breakdown yet.
2. **Fragment into Milestones — conversationally.** Propose a milestone breakdown, then negotiate with the human until the milestone shape fits their capacity and priorities. This is a thinking partner, not an automation. The AI might propose 15 milestones; the human may say "no, 3." Milestones are grouped around large-scale deliverables.

### 2. Build the backlog (once)

From Design + Milestones, build a **backlog** of stories.

- Each **backlog file is capped at a maximum of 30 stories**; overflow spawns a new backlog file.
- The backlog is **sortable and refinable**: most urgent, important, concrete, and doable items go to the **front** backlog files; wishful, experimental, least-concrete, least-urgent items sink to the **back**.
- The backlog is **evergreen and messy by design**. It can represent six months to several years of work and is not meant to be perfectly organized end to end.
- Some items will be mis-sized. A backlog item written as a "story" may, once scored, reveal itself to be a **Milestone (an epic)**. Reclassify it upward. Supplement the backlog as understanding improves.

### 3. Sprint planning (per-milestone OR per-sprint)

Sprint planning is where the hard thinking happens: work is broken down, risks mitigated, phases cut. It runs at two granularities using the same approach:

- **Per-milestone:** for a fresh project, plan a whole milestone's worth of sprints at once to drain the relevant backlog items. Example: milestone "Dockerize the app" → search the backlog for everything about Docker scripts, containerization, and secrets → gather them → compute cumulative effort/complexity/risk → assemble one or more sprints **ordered by interdependency** (you cannot do secrets until the Docker scripts exist). A milestone may yield multiple sprints planned at once.
- **Per-sprint (ad-hoc):** re-run on an existing sprint at any time (multiple times a day, weekly, monthly). If stories have blown out in size and no longer fit, **spawn a secondary sprint and shunt the overflow into it**, leaving each sprint with a clear, concise deliverable.

This flexibility removes the old credit-resistance failure: you never have to hold the whole plan in your head, and you never plan far-future sprints that would only be re-planned anyway.

### 4. Implementation plans and execution

When a story is ready to execute, it gets a **Tier 5 implementation plan** in `implementation-plans/`. Mitigation (fragmentation into phases, test and evaluation gates) happens at the **planning stage**, not at execution. By the time execution starts, the work is fragmented, normalized, and ready.

---

## Scoring model: Complexity, Effort, Risk

Every story is scored on **three orthogonal metrics** before model assignment. These metrics drive both model routing and mitigation. The scoring itself is performed by right-rail tooling (see *Companion Repository*); this repository defines where the scores live (the implementation-plan estimates block) and how they are used.

### Complexity

How much *reasoning* the work demands: architectural trade-offs, ambiguity, decision points. Measured against a per-model budget (steps, files, decision points, dependencies as units). A dependency graph may be emitted in the same analysis pass; only bake it into routing if it actually changes the model choice, otherwise it is overhead.

### Effort

**Orthogonal to complexity.** A 5,000-file style-guide sweep is *low complexity, high effort*. Effort is volume: file count, lines of code in scope, number of discrete chunks, number of subsystems touched. Estimation starts deliberately dumb (count files, count LOC, count modules, weight roughly) and is calibrated over time against recorded actuals.

### Risk

A judge reviews the **story summary** (a short, couple-paragraph pre-plan summary — cheaper to evaluate than the full plan) and emits a risk profile:

- **One headline risk number**, nominally 1–10 but **uncapped** — something extraordinarily risky can blow past 10 with a forecast of where it would land on an extended scale (e.g. "this is effectively a 1,000 — insane").
- **Sub-numbers** capturing the *types* of risk (technical, architectural, dependency, and so on) collapsed under the headline.

Risk is computed *before* mitigation. Establishing the risk is a separate step from mitigating it.

### Routing logic (combined)

- High **complexity** → escalate to a stronger reasoning model.
- High **effort**, low complexity → prefer parallelization / smaller-model batching over a single large call.
- High **risk** → may demand a strong model *and* triggers mitigation, even when complexity is low. Zero fault tolerance: a low-complexity but high-risk change still needs bulletproof execution.

### Risk-driven mitigation

Risk is not only a routing signal; it triggers mitigation strategy. A story scoring intolerably high (e.g. 10) is **not executed as-is**. Mitigations include:

- **Fragment into Phases (T6)**, each carrying a tolerable risk score (e.g. several phases each at ~3, worked sequentially).
- **Add gates:** unit tests, smoke tests, evaluations, provenance checks between phases.
- When risk is irreducible, accept it but wrap it in heavy validation.

---

## Orchestration: human as planner, skill as executor

The human **stops executing directly**. No more "model, go implement plan 2.2" in conversation, which forces the human to manually pick model and reasoning level for every story.

- **Planning stage owns:** scoring, fragmentation into phases, normalization, mitigation. Its output is execution-ready.
- **Orchestrator owns:** model choice, reasoning level, running the story, and capturing the completion review.

Once planning is done, execution is "pull a story off the board and do it." You only loop back to the human when you hit an **unknown** mid-execution. Otherwise it is fire-and-forget with observability baked in. The Orchestrator itself is right-rail tooling; this repository provides the normalized, scored plans it consumes and the completion-review artifact it produces.

---

## Observability: estimates vs. actuals

### Estimates block (top of every plan)

Every implementation plan carries an **estimates section at the top**: estimated time, files, effort, complexity, and risk. Planning tooling populates these values.

### Completion Review / Postmortem

A dedicated **Completion Review** (postmortem) is produced at session end, distinct from the implementation log (which records what was *done*). It is generated by walking the git diff and the conversation history, follows its own template, and is machine-ingestible. It captures:

- **Estimates vs. actuals** for time, files, effort, complexity, and tokens. Estimates and actuals must use the **same units** (do not estimate "file count" but measure "lines changed").
- **Model used** and reasoning level.
- **Narrative review** of how it went, what it struggled with, and what was unexpected.
- **Why things were unexpected** — distinguishing root causes: "took twice as long because subsystem X had hidden dependencies" (tune the effort estimator) versus "took twice as long because the model kept hallucinating" (change model tier or improve context). Different root causes need different fixes.

The Completion Review template lives beside the plan in the implementation-plan template folder. See [implementation-plans/IMPLEMENTATION_PLAN_TEMPLATE/completion-review.md](implementation-plans/IMPLEMENTATION_PLAN_TEMPLATE/completion-review.md).

### The Oracle (interim staging)

Estimate-vs-actual records are eventually ingested by a token/quota dashboard ("the Oracle") to answer questions like "when I estimate effort at X, how often am I right?" and feed routing. **Interim:** before that infrastructure exists, completion reviews stage as markdown files on disk so no time is wasted on premature infrastructure.

### Model Resumes

A central, **cross-task** artifact lives outside the tier hierarchy: one **Model Resume** per model. The framing is deliberate — *picking a model for work is hiring for a team*. A resume records empirical, your-workflow-specific data (not vendor benchmarks): complexity ranges the model is good or bad at, effort thresholds where it struggles, token efficiency, speed, and observed error patterns.

- Resumes are **rebuilt from scratch, never appended** — appending over-weights the most recent job (recency bias).
- Updates are **batched**: collect completion reviews over a few days, then rebuild.
- Rebuilds use **compaction** to control cost (golden-set / stratified sampling of the juiciest logs, or incremental merge of partial resumes).

Model Resumes live under [model-resumes/](model-resumes/). The rebuild logic is right-rail tooling.

---

## Implementation plans and execution records

Every Tier 5 implementation-plan folder should contain:

```text
plan.md
implementation-log.md
completion-review.md
```

`plan.md` carries the estimates block, scoring, mitigation, and (when needed) the Tier 6 phase breakdown. `implementation-log.md` records what actually happened. `completion-review.md` is the postmortem.

Other provenance artifacts are opt-in. Use them only when the task, user, plan, or installed skill explicitly calls for them.

| Artifact | Created By | Purpose |
| --- | --- | --- |
| `complaining.md` | `complaining` skill | Records actionable friction, blockers, ambiguity, risky assumptions, and tooling failures |
| `thinking.md` | `thinking-out-loud` skill | Records sanitized investigation notes, discovered constraints, useful observations, and revisit items |
| `evidence.md` | `evidence` skill | Indexes changed files, validation, commits, planning inputs, and unverified claims |
| `handover/shallow-handover.md` | `handover` skill | Transfers ownership back to the human or forward to another agent |

Do not create these optional files by default.

---

## Story Variants and Phases

### Story variants

When a story requires research or prototyping of multiple alternative approaches, use lettered variants such as `Story 1.2A`, `Story 1.2B`, and `Story 1.2C`. Only one variant is ultimately selected; the others are marked failed, rejected, or superseded. Variants answer: *Which approach should we use?*

### Phases (Tier 6)

When a story is too large or risky for a single pass, split it into sequential phases such as Phase 1, Phase 2, and Phase 3. Phases are execution steps for one chosen approach, not competing alternatives, and each phase is an independently executable, risk-bounded unit. Phases answer: *What order do we build this in, and how do we keep each slice safe?*

---

## Phase Execution and Context Management

Phase splitting exists to manage AI context limitations. A single conversation should not carry the entire history of a large story if a smaller, cleaner handoff can do the job.

### AgentThinking.md

`AgentThinking.md` is an optional scratchpad for temporary working notes during a long or complex task.

**Rules:**

- Do not use `AgentThinking.md` unless explicitly instructed or genuinely needed for task continuity.
- Treat it as temporary working memory, not authoritative project documentation.
- Reset or replace its contents when switching to a different story, sprint, or bug.
- Avoid committing it unless preserving context across separate AI runs is important.

### Phase Handover Documents

At the end of a phase, create a handover document so a fresh AI session can continue without depending on prior chat history.

**Location:** Prefer the active plan folder under `context/implementation-plans/`.

**Naming convention:**

| Context | Naming Pattern | Example |
| --- | --- | --- |
| Story-based work | `STORY_<sprint>_<story>_<variant>_handover_from_phase<N>.md` | `STORY_1_3_A_handover_from_phase1.md` |
| Bug fix | `BUG_<short-slug>_handover_from_phase<N>.md` | `BUG_timeout_error_handover_from_phase1.md` |
| Feature without a story | `FEATURE_<short-slug>_handover_from_phase<N>.md` | `FEATURE_export_csv_handover_from_phase1.md` |

**Minimum contents:**

1. What was completed in this phase
2. What exists in the repository now
3. Explicit next steps
4. Key decisions and rationale
5. Known issues, risks, or open questions
6. Important files and sections to read next

### How the next AI starts a later phase

1. Read the handover document first.
2. Then read only the necessary project documents:
   - `laws.md`
   - `design.md`
   - the relevant `milestones/*.md` and `sprints/*.md` when scope or sequencing matters
   - the relevant `backlog/*.md` story
   - `tier0/` files only when the task involves transcription synthesis or rationale recovery
   - `AgentThinking.md` only if it was used and is still relevant
3. Continue from the documented repo state rather than reconstructing the full prior conversation.

---

## WISC as Supporting Practice

WISC (Write, Isolate, Select, Compress) is useful vocabulary for the discipline this starter already encourages. Treat it as a supporting practice, not a replacement name for the repository.

| WISC Step | How this starter applies it |
| --- | --- |
| Write | Externalize memory into Tier 0 transcriptions, maintained specs, backlog, sprints, implementation plans, logs, completion reviews, and opt-in handovers. |
| Isolate | Keep work slices small, use focused agent sessions, and use specialist agents or subagents for bounded research and execution. |
| Select | Load only the context needed for the task instead of dumping every document into every prompt. |
| Compress | Summarize long work into maintained docs, phase handovers, completion reviews, and compacted state before context quality degrades. |

The practical goal is fewer hallucinations, less context pollution, smaller stories, and cleaner iterative development.

---

## Epics (acknowledged, not a tier)

**Epics are a cross-cutting concern, not a tier.** They track thematic work that spans multiple milestones — for example an epic "build the heads-up display" whose stories live across different milestones (get it working → make it look nice → migrate it), where those stories do not sit together because of how delivery is sequenced.

The seven-tier system is meant to be **progressive**: complete a milestone and move on rather than perpetually revisiting old milestones to add work. Epics are therefore **completely optional**, used only for tracking related work, and may not be mentioned in most projects. When a backlog "story" scores as an epic-sized item, that is the same as it actually being a **Milestone** — reclassify accordingly.

---

## Companion Repository: agentic_rails_tooling

`agentic_rails_context_starter` is the project-local context system (the left rail). The sibling `agentic_rails_tooling` repository is the recommended reusable capability system (the right rail). A generated project should work without `agentic_rails_tooling`, but it becomes much stronger when those reusable assets are installed into the agentic IDE's expected locations.

Use this conceptual split:

| Layer in `agentic_rails_tooling` | Purpose |
| --- | --- |
| `rules/` | Concise standards, style guidance, and stack-specific rules selected just in time. |
| `skills/` | Reusable task capabilities such as `commit-log`, compatibility checks, and focused process guidance. |
| Workflow-skills | Orchestrated processes such as backlog building, sprint planning, implementation-plan generation, plan execution, scoring, and resume rebuilds. These may live under `skills/` when the IDE does not support a separate workflow primitive. |
| `agents/` | Specialist personas and reference packs for domains such as WPF, gamedev, or XNA. |
| `prompt_dev/` | Source prompt material used to generate or evolve reusable tooling artifacts. |

The following capabilities are **right-rail tooling**. This repository defines the artifacts they read and write, but does not implement them:

| Right-rail capability | Reads | Writes |
| --- | --- | --- |
| Complexity + effort scorer | story summary, repo state | estimates block in `plan.md` |
| Risk judge | story summary | risk headline + sub-scores in `plan.md` |
| Backlog builder | design, milestones | `backlog/*.md` |
| Sprint planner (per-milestone / per-sprint) | backlog, milestones | `sprints/*.md`, scored `plan.md`, phases |
| Orchestrator | normalized scored `plan.md` | execution, `completion-review.md` |
| Completion-review / postmortem | git diff, conversation | `completion-review.md` |
| Model-resume rebuild | corpus of completion reviews | `model-resumes/*.md` |

Repository-local context wins when it conflicts with reusable tooling. Shared rules, skills, workflow-skills, and agents supplement the project; they do not replace its design, milestones, sprints, stories, or implementation plans.

---

## Context Lifecycle

- `tier0/*.md` contains raw transcription that should be synthesized before implementation decisions rely on it.
- `design.md` (including its Milestones Index), `milestones/*.md`, `sprints/*.md`, and `backlog/*.md` are authoritative and maintained.
- `implementation-plans/` contains story folders with `plan.md`, `implementation-log.md`, and `completion-review.md`. Optional skill-generated artifacts may live beside those files.
- `model-resumes/*.md` is a cross-task artifact rebuilt (never appended) from completion reviews.
- `AgentThinking.md` is temporary and should stay lightweight.
- Wiki and reference material support the project but may become stale; check them against the source of truth before relying on them.

---

## Agent Operational Guidelines

When assigned work in this repository:

1. Check for a relevant handover document first if the work is phased.
2. Read the minimum necessary context in this order:
   - `laws.md` always — constitutional authority for code quality, security, and architectural constraints
   - `design.md`
   - the relevant `milestones/*.md` and `sprints/*.md` when scope or sequencing matters
   - the relevant `backlog/*.md` story
   - `implementation-plans/*` when a plan exists
   - `tier0/*.md` only when the task involves transcription synthesis, enrichment, major scope revision, or rationale recovery
   - `AgentThinking.md` only when explicitly needed
3. If a Tier 5 implementation plan exists for the story, follow it closely.
4. Keep repository structure, naming, and documentation conventions consistent.
5. Update status fields in milestone, sprint, and backlog documents when the work requires it.
6. When ending a phase mid-stream, create a handover document only when a handover is needed or explicitly requested.
7. Produce a completion review at session end for meaningful execution work.
8. Use installed reusable tooling only when it is relevant and available; do not make the project depend on external tooling silently.

---

## IDE-Specific Agent Rules

When working within agentic IDEs such as Codex, Claude, Cursor, Windsurf, Gemini CLI, or similar tools, additional language-specific, framework-specific, skill, or agent rules may exist outside this repository.

These rules supplement the repository docs. Keep the repository workflow authoritative, but honor relevant external tooling when it has been installed for the current IDE.
