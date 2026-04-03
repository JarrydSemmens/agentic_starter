---
name: wpf-frontend-design
description: Use this skill when the user is building, styling, refactoring, or troubleshooting WPF UI such as views, user controls, custom controls, templates, bindings, resource dictionaries, animations, or MVVM-driven desktop experiences. This skill encodes senior WPF frontend engineering judgment and loads deeper reference files only for the WPF domain currently in play.
version: 1.0
---

# WPF Frontend Design

This skill is for production-grade WPF UI work. It should guide the agent toward solutions that feel native to the WPF ecosystem rather than treating XAML as a generic markup language.

The goal is not just to make the UI work. The goal is to shape UI that is:

- Architecturally sound
- Reusable and composable
- Native-feeling in XAML
- Visually polished
- MVVM-friendly
- Performance-aware

## Working Style

Start by identifying what kind of WPF problem is actually being solved. Do not load every reference file up front. Read the smallest relevant set.

Think in this order:

1. What is the user trying to build or change: a screen, a reusable control, a visual redesign, a behavior, a theme, or a performance fix?
2. What is the right WPF abstraction: `Style`, `ControlTemplate`, `DataTemplate`, `UserControl`, custom control, attached behavior, attached property, dependency property, or view model?
3. Which parts belong in XAML, which belong in view models, and which belong in control code?
4. What would make this feel native to WPF instead of improvised?

Prefer the least powerful abstraction that cleanly solves the problem. Do not jump to inheritance or custom controls when a template, behavior, style, or attached property is enough.

## Default WPF Stance

- Prefer composition over inheritance.
- Prefer MVVM and binding over code-behind event handling.
- Prefer styles, templates, and resources over duplicated markup.
- Prefer render-only animation and cheap state transitions over layout-heavy motion.
- Prefer control authorship patterns that preserve native WPF expectations.
- Preserve the behavior of existing controls when reskinning them unless the user explicitly wants a different interaction model.

## Reference Map

Load these references only when they are relevant:

- [references/componentization.md](references/componentization.md)
  Use when breaking a large view into reusable pieces, deciding between `UserControl`, templates, behaviors, and attached properties, or removing duplication without overengineering.
- [references/dependency-properties.md](references/dependency-properties.md)
  Use when building or extending controls in code, defining dependency properties, exposing bindable state, or making custom functionality feel native to XAML.
- [references/control-templating.md](references/control-templating.md)
  Use when restyling existing controls, replacing control visuals without losing control semantics, or building platform-specific presentation on top of familiar controls.
- [references/beautify.md](references/beautify.md)
  Use when the task is about visual quality, polish, animation, theming, visual states, storyboards, or premium-feeling interaction design.
- [references/mvvm-bindings.md](references/mvvm-bindings.md)
  Use when the task involves view models, bindings, commands, `DataContext`, validation, or deciding whether logic belongs in the view or the view model.
- [references/resource-system.md](references/resource-system.md)
  Use when organizing shared colors, brushes, styles, templates, themes, merged dictionaries, or deferred resource loading.
- [references/performance.md](references/performance.md)
  Use when the task touches rendering cost, invalidation, virtualization, `Freezable` usage, animation efficiency, or retained-mode rendering behavior.

If a task crosses multiple domains, load only the smallest useful combination. Typical pairings:

- Reusable control work: `componentization.md` + `dependency-properties.md`
- Reskinning a control: `control-templating.md` + `beautify.md`
- App-wide theming: `resource-system.md` + `beautify.md`
- UI logic cleanup: `mvvm-bindings.md` + `componentization.md`
- Slow or janky UI: `performance.md` plus the domain that introduced the issue

## Execution Checklist

When using this skill:

1. Identify the correct WPF abstraction before writing code.
2. Keep the visual tree, bindings, and state model understandable.
3. Preserve MVVM boundaries unless there is a clear WPF-specific reason not to.
4. Reuse resources and templates instead of cloning markup.
5. Keep interactions smooth and cheap.
6. Verify that the result still feels like a native WPF control or view.

## Do Not

- Do not treat WPF like web frontend work.
- Do not default to code-behind click handlers for application behavior.
- Do not subclass controls when styles, templates, behaviors, or attached properties are sufficient.
- Do not place all knowledge in this file. Keep domain depth in the reference files and load them on demand.
