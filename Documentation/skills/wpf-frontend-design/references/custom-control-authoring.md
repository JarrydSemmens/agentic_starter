---
name: custom-control-authoring
version: 1.1
---

# Custom Control Authoring

## Use This Reference When

- Building a reusable control library rather than a one-off composed view
- Authoring controls that should be fully restylable through `ControlTemplate`
- Wiring `DefaultStyleKey`, `Generic.xaml`, named parts, or `OnApplyTemplate`
- Defining control states, automation peers, and default theme behavior for a custom control

## Veteran Expert Stance

Custom control authoring is the full discipline of producing a reusable WPF control primitive that behaves like it belongs in the framework. The control contract, property system, template contract, default style lookup, accessibility surface, and theming conventions all need to line up.

If `UserControl` is a packaged composition, a custom control is a reusable contract.

## Full Lifecycle

The typical lifecycle is:

1. Define the control contract and public dependency properties
2. Decide the required named parts and visual states
3. Override `DefaultStyleKey` metadata so the control resolves its default style
4. Place the default style in `Themes/Generic.xaml`
5. Implement `OnApplyTemplate` to find and wire template parts safely
6. Expose automation behavior if the control needs meaningful accessibility semantics
7. Keep the control usable even when consumers restyle or partially reshape the template

## Core Building Blocks

- `DefaultStyleKey`
- `Generic.xaml`
- `ThemeInfo`
- `OnApplyTemplate`
- Named `PART_*` elements
- `VisualStateManager`
- Dependency properties
- Automation peers where needed

These pieces should feel like one coherent system, not separate tricks.

## Practical Heuristics

- Only require named parts that are genuinely necessary for behavior.
- In `OnApplyTemplate`, detach from old parts before wiring new ones.
- Be defensive when a template omits optional parts. Fail gracefully where possible.
- Document required parts and visual states clearly within the control code or reference guidance.
- Keep behavior in the control and look in the template.
- Prefer state changes through `VisualStateManager` over hand-toggling visual elements directly.
- Ensure the control has a sensible default template so it is usable immediately when dropped into XAML.

## Default Style Lookup

Default style resolution is a core part of custom control authoring:

- Override `DefaultStyleKey` metadata on the control type
- Keep the default style in `Themes/Generic.xaml`
- Make sure assembly-level `ThemeInfo` and resource build actions support theme lookup correctly
- Treat the default style as part of the control's contract, not as optional decoration

If default style lookup is wrong, the control often "works" in code but feels broken to every consumer.

## Template Parts And States

Named parts and visual states are how a reusable control exposes structured expectations to templates:

- Required parts should be minimal and behavior-driven
- State groups should reflect real control behavior such as interaction, validation, selection, or edit mode
- Templates should be free to restyle the control without losing the contract

The best control contracts are powerful but narrow.

## Automation And Accessibility

Reusable controls should not stop at visuals:

- Provide `AutomationPeer` support when the control introduces meaningful custom interaction
- Preserve keyboard interaction and focus behavior
- Ensure screen-reader semantics still make sense after templating
- Treat accessibility as part of default control quality, not as a later retrofit

## Smells

- A custom control with no clear reason to exist beyond fixed composition
- `OnApplyTemplate` code that assumes parts always exist and never detach
- Massive required part lists that make templating fragile
- Default styles that live outside expected theme conventions
- A control that looks customizable but breaks as soon as the template changes
- Accessibility behavior that disappears once the default template is replaced

## Goal

Author reusable WPF controls that honor the framework's property system, theming model, templating contract, and accessibility expectations so consumers can adopt them as real control primitives.
