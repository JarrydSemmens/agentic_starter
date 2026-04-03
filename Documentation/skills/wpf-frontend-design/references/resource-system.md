# Resource System

## Use This Reference When

- Organizing colors, brushes, thicknesses, styles, templates, or theme values
- Standardizing visuals across multiple views or controls
- Building layered theming or skinning
- Reducing duplication and controlling redraw scope through smart resource usage

## Senior WPF Stance

The resource system is how mature WPF applications stop being collections of isolated XAML files and become a coherent design system.

Treat resources as architecture, not garnish.

## What Good Resource Design Achieves

- Consistent visuals across the app
- Controlled override points
- Reusable styles and templates
- Theme or skin separation from control logic
- Minimal churn when visuals evolve
- More precise control over what actually needs to redraw

## Practical Heuristics

- Put durable shared values in resource dictionaries, not inline markup.
- Layer dictionaries intentionally: foundation, theme, control styles, feature-specific overrides.
- Prefer `StaticResource` by default.
- Use `DynamicResource` only when runtime theme swaps or live resource changes are genuinely needed.
- Keep resource names stable and semantic rather than color-chip specific when the value represents a role.
- Move template and style duplication into shared dictionaries early.

## Deferred Loading And Overrides

- Split large resource sets into focused dictionaries.
- Merge dictionaries at the appropriate scope rather than globally by habit.
- Design override points so skins can replace visuals without modifying control code.
- Think about the redraw and invalidation consequences of dynamic resources before using them widely.
- Use dictionary boundaries to keep theming flexible without broad, unnecessary visual churn.

## Smells

- Inline brushes and repeated magic numbers across views
- One giant dictionary with no layering model
- `DynamicResource` everywhere with no runtime need
- Skins that require editing control implementation files

## Goal

Make visuals reusable, themeable, and maintainable without tangling them with control logic.
