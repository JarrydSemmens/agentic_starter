---
name: accessibility-automation-and-localization
version: 1.1
---

# Accessibility, Automation, and Localization

## Use This Reference When

- Making a control or view keyboard-first and screen-reader friendly
- Adding automation properties or custom automation peers
- Designing for high contrast, scalable layout, or readable focus cues
- Making UI text, formatting, and layout behave correctly across cultures and languages

## Veteran Expert Stance

Accessibility and localization are part of product quality, not compliance garnish. WPF gives strong primitives for keyboarding, automation, resource-based localization, and adaptable presentation, but they only help if they are designed in from the beginning.

## Core Concerns

- Keyboard-first interaction
- Automation properties and automation peers
- Focus visuals and interaction clarity
- High-contrast and theme resilience
- Scalable typography and adaptable layout
- Culture-aware formatting and localized resources

## Practical Heuristics

- Ensure every important workflow is possible without a pointer.
- Use automation properties intentionally on important controls and content surfaces.
- Provide custom automation peers when a reusable custom control introduces meaningful new interaction.
- Preserve visible focus cues and interaction feedback.
- Avoid color-only communication for critical status.
- Expect localized text to grow and layouts to stretch.
- Keep formatting culture-aware instead of hardcoding date, number, and currency assumptions.

## High Contrast And Adaptability

Premium design still needs to survive hostile conditions:

- High contrast
- Larger fonts
- Different language lengths
- Keyboard-only interaction
- Assistive technology traversal

If the UI only works under default palette and mouse use, it is not done.

## Smells

- Hover-only actions with no keyboard path
- Custom controls with no meaningful automation surface
- Focus cues removed because they look unfashionable
- Hardcoded string layout that breaks in translation
- Color as the only indicator of state or error

## Goal

Build WPF applications and controls that remain usable, understandable, and automatable across keyboard-first use, assistive technology, theme variation, and localization pressure.
