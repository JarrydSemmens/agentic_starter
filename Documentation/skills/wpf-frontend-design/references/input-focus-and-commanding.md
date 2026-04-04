---
name: input-focus-and-commanding
version: 1.0
---

# Input, Focus, and Commanding

## Use This Reference When

- Wiring keyboard shortcuts, access keys, or routed commands
- Fixing focus behavior, tab order, focus scopes, or keyboard navigation
- Deciding between direct event handling, behaviors, and routed commanding
- Ensuring pointer interaction and keyboard interaction have equivalent behavior

## Veteran Expert Stance

Great WPF interaction design is not just about mouse clicks. Input, focus, and commanding are part of the control and application contract. If keyboard, focus, and command routing are wrong, the UI is incomplete no matter how polished it looks.

## Core Layers

- Routed commands and command bindings
- Input bindings and gestures
- Access keys
- Logical focus and keyboard focus
- Focus scopes
- Keyboard navigation and tab order
- Behaviors and event-to-command bridges where routed commanding does not fit cleanly

## Practical Heuristics

- Use native command surfaces where controls already support `Command`.
- Use routed commands when the action should travel naturally through the element tree.
- Use input bindings for keyboard gestures instead of ad hoc key event logic when possible.
- Use behaviors or event bridges when a useful event exists but there is no clean command surface.
- Design keyboard and pointer flows together so hover-only affordances do not hide essential functionality.
- Make tab navigation deliberate rather than accepting accidental visual-tree order.
- Treat focus visuals as part of the design, not as cosmetic noise to be removed.

## Focus Discipline

Focus issues often come from not distinguishing concepts:

- Keyboard focus is where keyboard input goes now
- Logical focus is the remembered focus within a scope
- Focus scopes matter for menus, toolbars, dialogs, popups, and composite surfaces

Understanding these distinctions prevents a lot of "focus is weird" debugging.

## Behaviors Versus Routed Commanding

- Prefer routed commanding when the action is fundamentally a command in the WPF sense
- Prefer behaviors when bridging arbitrary events or element-specific interaction patterns into MVVM
- Prefer either over scattering custom key and event logic through code-behind

## Smells

- Mouse-only workflows with no keyboard equivalent
- Arbitrary `KeyDown` handling in code-behind for behavior that should be a command or input binding
- Broken tab order caused by accidental tree structure
- Focus visuals removed without providing an accessible replacement
- Commands that technically exist but do not route to the place users expect

## Goal

Build WPF interaction models that are command-driven, keyboard-credible, focus-correct, and consistent across pointer and non-pointer input paths.
