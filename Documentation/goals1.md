---
version: 0.1
owner: "Your Name"
repo: "your-repo"
description: Tier 3 goals template for Milestone 1, capturing deliverables, acceptance criteria, scope, and implementation guidance.
---
# Project Name - Goals (Milestone 1: *Name*)

> **Goals and deliverables for Milestone 1: *Name***
>
> **Status:** Not Started
>
> See `milestones.md` for the full milestone roadmap.

---

## Context

<!-- One-sentence description of the problem this milestone addresses. -->

- **Problem:** *Describe the core problem or need this milestone tackles.*
- **Relevant Tier 0 intake:** *Link raw source notes or addenda only when they materially affect this milestone.*

## Milestone 1 Goals Summary

<!-- Keep this table in sync as goals are added, completed, or modified. -->
<!-- Status values: Complete, In Progress, Not Started, Blocked, Superseded -->

| Goal | Status | Link |
|------|--------|------|
| Goal 1.1 - *Name* | Not Started | [Jump to details](#goal-1-1) |
| Goal 1.2 - *Name* | Not Started | [Jump to details](#goal-1-2) |
| Goal 1.3 - *Name* | Not Started | [Jump to details](#goal-1-3) |

**Milestone Status:** Not Started - 0/? goals complete.

<!-- Optional: List key environment details and constraints. -->
<!--
- **Environment:**
  - **OS:** e.g. Windows 11, Linux, macOS
  - **Runtime:** e.g. .NET 9, Node 20, Python 3.12
  - **Infra:** e.g. Docker, Kubernetes, Serverless
- **Key constraints:**
  - Constraint 1
  - Constraint 2
-->

### Milestone 1 Scope

**Intent:** *One-sentence summary of what "done" looks like for this milestone.*

**What this milestone means:**

- *Deliverable or capability 1*
- *Deliverable or capability 2*
- *Deliverable or capability 3*

**Key deliverables:**

- *Deliverable 1*
- *Deliverable 2*
- *Deliverable 3*

### Explicitly Out of Scope (Milestone 1)

<!-- List things that are intentionally NOT part of this milestone to prevent scope creep. -->

- *Deferred item 1*
- *Deferred item 2*

---

## Solution Overview

### High-Level Architecture

<!-- Describe the major components of the solution for this milestone. -->

- **Component 1:** *What it does*
- **Component 2:** *What it does*
- **Component 3:** *What it does*

### Data Flow

<!-- Describe the primary data flows or processing pipelines for this milestone. -->

#### Pipeline / Flow 1: *Name*

1. **Step 1** - description
2. **Step 2** - description
3. **Step 3** - description

#### Pipeline / Flow 2: *Name*

1. **Step 1** - description
2. **Step 2** - description
3. **Step 3** - description

---

## Milestone 1 Goals and Deliverables

<!-- ============================================================ -->
<!-- GOAL TEMPLATE                                                 -->
<!-- Copy the block below for each new goal within this milestone. -->
<!-- Replace placeholder text with goal-specific content.          -->
<!-- ============================================================ -->

<a id="goal-1-1"></a>

### Goal 1.1 - *Name*

**Intent:** *One-sentence description of what this goal achieves.*

#### Source Context

- **Milestone:** [Milestone 1](milestones.md#milestone-1)
- **Tier 0 source:** *Link only if this goal depends on a specific intake note or addendum.*
- **Design context:** *Link a relevant design section if one exists.*
- **Tier 4 plan:** *Link the implementation plan when this goal is ready for execution.*

#### Deliverables

<!-- List the concrete outputs of this goal. Be specific enough that
     an AI agent or developer can verify completion. -->

- **Deliverable 1:**
  - Detail / sub-item
  - Detail / sub-item

- **Deliverable 2:**
  - Detail / sub-item
  - Detail / sub-item

#### Acceptance Criteria

<!-- Checkboxes that define "done" for this goal. -->

- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

#### Out of Scope

<!-- What this goal explicitly does NOT cover. -->

- *Deferred item 1*
- *Deferred item 2*

---

<a id="goal-1-2"></a>

### Goal 1.2 - *Name*

**Intent:** *One-sentence description of what this goal achieves.*

#### Source Context

- **Milestone:** [Milestone 1](milestones.md#milestone-1)
- **Tier 0 source:** *Link only if applicable.*
- **Tier 4 plan:** *Link when ready.*

#### Deliverables

- **Deliverable 1:**
  - Detail / sub-item

- **Deliverable 2:**
  - Detail / sub-item

#### Acceptance Criteria

- [ ] Criterion 1
- [ ] Criterion 2

#### Out of Scope

- *Deferred item 1*
- *Deferred item 2*

---

<a id="goal-1-3"></a>

### Goal 1.3 - *Name*

**Intent:** *One-sentence description of what this goal achieves.*

#### Source Context

- **Milestone:** [Milestone 1](milestones.md#milestone-1)
- **Tier 0 source:** *Link only if applicable.*
- **Tier 4 plan:** *Link when ready.*

#### Deliverables

- **Deliverable 1:**
  - Detail / sub-item

- **Deliverable 2:**
  - Detail / sub-item

#### Acceptance Criteria

- [ ] Criterion 1
- [ ] Criterion 2

#### Out of Scope

- *Deferred item 1*
- *Deferred item 2*

---

## Non-Functional Guarantees

<!-- List non-functional requirements that apply across all goals in this milestone.
     Examples: idempotency, explainability, security, performance, accessibility.
     Delete or add sections as appropriate for your project. -->

### *Guarantee 1 (e.g., Idempotency)*

- *How this guarantee is achieved*
- *What invariants are maintained*

### *Guarantee 2 (e.g., Observability)*

- *What is logged, traced, or measured*
- *How failures are surfaced*

### *Guarantee 3 (e.g., Security / Privacy)*

- *Data protection measures*
- *Access control approach*

---

## External Dependencies

<!-- List all external services, libraries, or infrastructure this milestone depends on.
     Include version, purpose, and current status. -->

### *Dependency 1*

- **Version:** *x.y.z*
- **Purpose:** *What it provides*
- **Status:** Active / Planned / Optional

### *Dependency 2*

- **Version:** *x.y.z*
- **Purpose:** *What it provides*
- **Status:** Active / Planned / Optional

---

## Agent Guidelines for This Milestone

<!-- Instructions for AI agents working on goals in this milestone. -->

When working on tasks in this milestone, anchor them to the goals above.

### Project Boundaries

<!-- Define which parts of the codebase each type of change should touch. -->

- *Change type 1* -> *which module / directory*
- *Change type 2* -> *which module / directory*

### Development Approach

<!-- List key development principles and conventions for this milestone. -->

- *Principle 1 (e.g., follow SOLID, use dependency injection)*
- *Principle 2 (e.g., keep interfaces separate from implementations)*
- *Principle 3 (e.g., maintain idempotency guarantees)*

### Rules Compliance

<!-- Reference any coding style or convention files agents should follow. -->

- Always respect project-level coding conventions and style guides.
- Check for relevant installed shared rules, skills, workflow-skills, or specialist agents only when the task calls for them.
- Keep repository-local goals and implementation plans authoritative when external tooling gives generic advice.

---

## Related Documents

- **`tier0/`** - Raw intake and addenda
- **`milestones.md`** - Authoritative milestone definitions
- **`design.md`** - Technical architecture specification
- **`agenticworkflow.md`** - How AI agents collaborate on this project

<!-- ============================================================ -->
<!-- GUIDELINES FOR USING THIS TEMPLATE                           -->
<!--                                                               -->
<!-- 1. Create one goals file per milestone (goals1.md, goals2.md) -->
<!-- 2. Each goal has: Intent, Deliverables, Acceptance Criteria   -->
<!-- 3. Goals can have VARIANTS (A/B/C) for alternative approaches -->
<!--    - See agenticworkflow.md for variant conventions           -->
<!-- 4. Goals can have PHASES for large implementations            -->
<!--    - See agenticworkflow.md for phase and handover conventions -->
<!-- 5. Update the summary table at the top as goals progress      -->
<!-- 6. Mark completed goals in both title and table               -->
<!-- 7. Keep Out of Scope sections honest because they prevent creep -->
<!-- 8. Promote accepted Tier 0 changes into maintained goal text   -->
<!-- ============================================================ -->
