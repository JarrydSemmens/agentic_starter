# Componentization

## Use This Reference When

- A XAML view is too large or repetitive
- A piece of UI should be reused in multiple places
- Functionality should be attached to existing controls without subclassing
- You need to decide between `UserControl`, custom control, `DataTemplate`, behavior, or attached property

## Senior WPF Stance

Good WPF componentization is not just splitting files. It is choosing the smallest reusable unit that preserves clarity, styling flexibility, and MVVM boundaries.

Start by asking what is actually being reused:

- Reused structure and visuals: consider `UserControl` or `DataTemplate`
- Reused visual identity for an existing control type: consider `Style` or `ControlTemplate`
- Reused interaction or cross-cutting UI behavior: consider a behavior or attached property
- Reused control capability that needs first-class XAML surface area: consider a custom control

## Preferred Decision Order

1. `DataTemplate` when you are repeating presentation for data
2. `Style` when you are standardizing properties or visual treatment
3. `ControlTemplate` when you must replace the control's visual tree
4. `UserControl` when you are packaging a fixed composition of child elements
5. Behavior or attached property when you are packaging functionality
6. Custom control when you are authoring a reusable control primitive

## Practical Heuristics

- Use `UserControl` for composed UI chunks with a stable structure.
- Use custom controls when consumers should restyle or re-template the control deeply.
- Prefer behaviors over inheritance for attachable interaction logic.
- Avoid base-class pyramids for UI composition.
- Expose clear bindable inputs and outputs rather than reaching into child elements from the outside.
- Keep each component's responsibility narrow enough that its purpose is obvious from its name.

## Smells

- A view that repeats the same XAML block three or more times
- Controls that require consumers to know internal element names
- Inheritance used only to share a small piece of UI behavior
- A `UserControl` that should really be a styleable custom control

## Goal

Break UI into reusable pieces without freezing future design options or leaking implementation details.
