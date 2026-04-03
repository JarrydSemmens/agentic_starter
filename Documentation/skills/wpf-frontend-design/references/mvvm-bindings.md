# MVVM Pattern And Bindings

## Use This Reference When

- The task involves `DataContext`, binding, commands, validation, or view model shape
- You are deciding whether logic belongs in XAML, code-behind, or the view model
- A view is too event-driven and needs to become more declarative
- A screen or control should fully participate in MVVM

## Senior WPF Stance

WPF is at its strongest when the view describes structure and state projection while the view model owns behavior and application logic.

Binding is not just a convenience. It is the backbone of how a WPF surface stays testable, maintainable, and expressive.

## Core Rules

- Set up a coherent `DataContext` boundary.
- Use bindings for state flow.
- Use `ICommand` for user intent.
- Avoid click handlers for application behavior unless there is a narrow view-only reason.
- Keep code-behind for view plumbing, not business decisions.

## Practical Heuristics

- Favor explicit, readable bindings over clever binding graphs.
- Put derived display state on the view model before reaching for converters.
- Use commands for buttons, menus, gestures, and repeated interaction patterns.
- Keep validation rules and error presentation consistent with the binding model in use.
- Prefer one clear binding source over multiple hops through named elements.
- When a view model gets bloated, split responsibilities before adding more bindings around it.

## Where Logic Goes

- View model: state, commands, business rules, orchestration
- View: layout, templates, visual states, view-only interaction glue
- Behavior or attached property: reusable UI interaction that should not live in a specific view model

## Smells

- Click handlers implementing workflow logic
- Converters doing business logic
- Deep `ElementName` chains for application state
- View models that know about concrete controls

## Goal

Use WPF's binding system to keep the UI declarative and the behavior testable.
