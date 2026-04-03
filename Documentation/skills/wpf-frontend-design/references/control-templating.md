# Control Templating

## Use This Reference When

- Restyling an existing WPF control without losing its semantics
- Replacing the visual tree of a built-in control
- Building a platform-specific or brand-specific presentation on top of familiar controls
- Deciding whether a `Style`, `ControlTemplate`, or custom control is the right move

## Senior WPF Stance

Control templating is one of WPF's superpowers. It lets you keep the behavior contract of a control such as `Button`, `TextBox`, or `ListBox` while replacing the visuals almost completely.

The goal is not merely to make a control look different. The goal is to preserve the control's identity while redefining how it is presented.

## What Templates Are For

- Replacing the internal visual structure of a control
- Binding visual parts to control properties
- Hosting visual states, triggers, and named parts
- Producing new interaction surfaces while keeping familiar control behavior

## Practical Heuristics

- Start with the existing control contract before redesigning the visuals.
- Preserve expected keyboard, focus, hover, pressed, disabled, and validation behavior.
- Use `TemplateBinding` or `RelativeSource TemplatedParent` for values that should flow from the control into the template.
- Keep template parts intentional and minimal.
- Put styling variants in styles, not duplicated templates, when only resources or a few setters change.
- Escalate to a custom control only when the control contract itself must change, not just its appearance.

## Platform-Specific UI

Templates are often the right tool when the same control must feel appropriate for:

- Console-focused navigation
- Touch-friendly mobile-like interaction
- Dense desktop productivity tools
- Branded premium UI

The outer control stays familiar. The visual tree and interaction treatment adapt to the platform.

## Smells

- Rebuilding a control from scratch just to change its look
- Losing focus, validation, or command behavior during restyling
- Overusing custom controls where a template would do
- Templates that hard-code values that should come from resources or control properties

## Goal

Deliver radically customized visuals while retaining the familiar strengths of the WPF control model.
