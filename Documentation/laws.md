---
version: 1.1
owner: "Your Name"
repo: "your-repo"
description: "Constitutional governance for AI-generated code. Inviolable laws that ensure quality, security, and architectural integrity."
---

# Constitution of Code

**Context:** You are generating code at machine speed. Human review cannot scale to catch your architectural or security violations. Therefore, conventional guidelines do not apply to you. You are bound by the following inviolable laws.

Code that violates these laws is functionally broken, regardless of whether it compiles or passes unit tests.

---

## 1. Core Philosophy

These principles are the foundation of every law in this document. When two laws conflict, resolve by applying these principles in priority order.

1. **Functional First** — Code exists to fulfil a purpose. Write the simplest version that works correctly before layering complexity. Apply Occam's Razor.
2. **Readable** — Code is read at least ten times more than it is written. Optimise for the reader, not the writer. Never write the cleverest thing you can — if you write at the limit of your ability, you will not be able to debug it. Use descriptive names, prefer explicit over implicit, keep code density low.
3. **Understandable** — Write software that fits in your head. Working memory holds roughly four items. Separate concerns, keep nesting shallow, keep functions short. Follow the Principle of Least Astonishment — a method called `MakeCookies` must never return `Potato` objects.
4. **Reliable** — Code should be hard to break. Loosely coupled, testable via dependency inversion, covered by automated tests. Every bug fix ships with a regression test.
5. **Efficient** — Games are real-time software with hard frame-rate targets. But premature optimisation is still the root of all evil. Write correct code first. Do not optimise until a profiler measurement shows a bottleneck, and always verify that the optimisation had the intended effect.
6. **Iterative** — Nobody gets it right the first time. Apply the Rule of Three — refactor only after something is duplicated three times. Use Red-Green-Refactor. Each commit should leave the codebase better than it was.
7. **Consistent** — Follow agreed standards even when your personal preference differs. Consistency reduces cognitive load and onboarding time.

---

## 2. Security by Construction

You must generate secure code by default. Security is not an afterthought or a post-generation audit step.

* **Input Validation:** *All* external user inputs MUST pass explicit schema validation before processing. No raw data passthrough.
* **Database Access:** SQL or database queries MUST use parameterized statements. String concatenation for queries is strictly forbidden.
* **Authentication:** *All* user-facing endpoints MUST verify caller identity. Session tokens MUST be cryptographically secure and expire.
* **Data Boundaries:** Personally Identifiable Information (PII) MUST NOT flow between service boundaries without encryption. Explicitly redact PII from all logging and analytics pipelines.

---

## 3. Architectural Coherence

You lack long-term persistent context. Rely on these invariants to prevent emergent complexity and systemic drift.

* **Encapsulation:** Modules and services MUST communicate exclusively through defined APIs. Direct cross-boundary data access is forbidden.
* **Separation of Concerns:** Business logic MUST remain strictly separated from presentation/UI logic.
* **State & Configuration:** Configuration MUST be externalized from application code. State mutations MUST be predictable and isolated.
* **Innovation Boundary:** Follow established repository patterns. Do not invent new architectural patterns or introduce new third-party dependencies unless explicitly instructed.

### SOLID Principles

All code must respect SOLID:

- **Single Responsibility** — A class has one and only one reason to change. If it handles more than one concern, it must be split. Do not mix gameplay logic, UI logic, persistence, input handling, animation, or infrastructure in a single class.
- **Open/Closed** — Open for extension, closed for modification. Prefer composition, interfaces, and new classes over modifying existing stable code.
- **Liskov Substitution** — Derived types must be fully substitutable for their base types without breaking behaviour.
- **Interface Segregation** — Interfaces must be small and focused. Never force a class to implement methods it does not use.
- **Dependency Inversion** — Depend on abstractions (interfaces), not concrete implementations. Use constructor injection for plain C# classes and serialized references or installers for MonoBehaviours.

Apply these as guiding heuristics. Game code sometimes benefits from pragmatic shortcuts — but document them and revisit them.

---

## 4. Performance & Scale

You must embed performance constraints directly into the generated implementation.

* **Latency:** Total system latency MUST NOT exceed defined user experience budgets. Respect frame-rate targets for real-time applications and response-time SLAs for services.
* **Cascading Complexity:** Minimise transitive dependencies between modules. Avoid deep call chains that make failure diagnosis and performance profiling difficult.
* **Resource Limits:** Implement strict memory management. Avoid unnecessary heap allocations in hot paths, tick functions, or high-frequency loops.

---

## 5. Quality & Stability

Code quality must not drift based on prompt phrasing. These are non-negotiable structural requirements.

* **Complexity:** Functions MUST be short enough to reason about as a single unit of work. Classes MUST adhere to the Single Responsibility Principle.
* **Testability:** *All* public methods MUST include deterministic unit tests. Coverage MUST NOT drop below the established repository baseline.
* **Documentation:** Public APIs MUST include usage examples. Complex algorithmic choices MUST be explained in comments.

---

## 6. Mandatory Trade-offs

When faced with architectural ambiguity, you MUST resolve decisions using the following hierarchy:

* **Security vs. Convenience:** *Always* choose security over developer or user convenience.
* **Performance vs. Readability:** Prefer readability by default. Optimize for performance *only* if the explicit execution budget is violated.
* **Consistency vs. Novelty:** *Always* follow existing codebase conventions over modern/novel approaches, unless explicitly authorized to refactor.

When these specific rules do not cover the conflict, fall back to the Core Philosophy priority order in Section 1.

---

## 7. Definition of Done

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

---

## 8. Enforcement

When you cannot satisfy a law, you MUST:

1. Stop and identify which law is at risk.
2. Explain the conflict to the user before proceeding.
3. Never silently violate a law — an acknowledged exception is acceptable; a hidden one is not.
