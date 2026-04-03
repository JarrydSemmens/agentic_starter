# Dependency Properties

## Use This Reference When

- Creating a custom control or extending an existing one in code
- Exposing bindable state to XAML
- Participating in styling, animation, templating, or value inheritance
- Adding control capabilities that should feel native to WPF

## Senior WPF Stance

Dependency properties are not just a WPF formality. They are the contract that lets a control participate naturally in the XAML property system.

Use a dependency property when the value should support one or more of these:

- Binding
- Styling
- Animation
- Default metadata
- Value inheritance
- Change callbacks
- Layout or render invalidation

If the property is only internal implementation detail, a normal CLR property is often enough.

## What Good DP Design Looks Like

- The property name reads like it belongs beside built-in WPF properties.
- Metadata reflects real rendering or layout consequences.
- Change callbacks are narrow and predictable.
- The control remains usable from pure XAML.
- The property enables composition instead of forcing consumers into code-behind.

## Practical Heuristics

- Register the property with the correct owner type and metadata.
- Use `FrameworkPropertyMetadata` when layout, rendering, binding, or inheritance behavior matters.
- Add property-changed callbacks only when the control must react immediately.
- Keep callbacks free of business logic.
- Prefer coercion or validation only when the property truly has invariant rules.
- Use attached properties when the capability logically belongs on many unrelated elements.

## Novel Control Work

When building new control behavior, think in terms of native control affordances:

- What should be set in XAML?
- What should be stylable?
- What should be animatable?
- What should templates be able to consume?

If the answer is "yes" to any of those, a dependency property is usually part of the solution.

This is also the mechanism for deeply permuting existing controls in a native-feeling way. If a control should gain a new bindable capability, editing surface, or state model without feeling bolted on, dependency properties are usually part of that design.

## Smells

- Plain CLR properties for values that must bind or animate
- Code-behind fields that should be exposed to templates
- Property callbacks that mutate half the control tree
- Dependency properties used only because "custom controls need them"

## Goal

Author controls and abstractions that plug into WPF naturally, even when the behavior itself is novel.
