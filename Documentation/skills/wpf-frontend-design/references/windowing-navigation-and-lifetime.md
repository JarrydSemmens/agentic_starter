---
name: windowing-navigation-and-lifetime
version: 1.1
---

# Windowing, Navigation, and Lifetime

## Use This Reference When

- Designing startup, shutdown, or application shell behavior
- Working with windows, dialogs, owned windows, or popups at the app-flow level
- Choosing modal versus modeless interactions
- Building navigation flows, frame-based shells, or view-model-driven screen transitions

## Veteran Expert Stance

Desktop application quality depends heavily on shell behavior. Window ownership, modality, startup flow, shutdown semantics, and navigation patterns are architectural decisions, not UI afterthoughts.

## Core Concerns

- Application startup and main-window selection
- Shutdown behavior and lifetime rules
- Owned windows and dialog ownership
- Modal versus modeless flow
- Navigation shells and view switching
- View-model orchestration at the shell level

## Practical Heuristics

- Be explicit about which window owns which child window or dialog.
- Use modal behavior only when the interaction truly blocks the rest of the workflow.
- Keep dialog orchestration compatible with MVVM boundaries instead of embedding app decisions in view code.
- Make startup and shutdown rules easy to reason about.
- Treat navigation state as presentation architecture, not as arbitrary code-behind swapping.
- Keep shell-level commands and global interactions visible in the application architecture.

## Navigation Patterns

Different apps want different shells:

- Window-per-workflow apps
- Single-shell apps with view switching
- Frame-based navigation flows
- Tool-style multi-window applications

Choose the pattern that matches the product shape instead of forcing one shell style everywhere.

## Smells

- Dialogs opened with no ownership or lifetime discipline
- Modal windows used where modeless interaction would be less disruptive
- Navigation implemented as random control replacement in code-behind
- Shutdown logic that depends on accidental window order or hidden state
- Shell view models that know too much about concrete windows

## Goal

Build WPF application shells that feel deliberate, predictable, and maintainable by treating windows, dialogs, navigation, and lifetime as first-class architecture.
