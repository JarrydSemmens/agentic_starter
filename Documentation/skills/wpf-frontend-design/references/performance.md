# Performance

## Use This Reference When

- The UI feels janky, heavy, or over-invalidated
- The task involves animation cost, redraw scope, virtualization, or rendering throughput
- A control updates frequently or hosts complex visuals
- You need to reason about WPF retained-mode rendering behavior

## Senior WPF Stance

WPF performance work starts with understanding what actually causes invalidation, layout work, and redraw. Performance is usually won by reducing unnecessary work, not by micro-optimizing random code paths.

## Core Performance Ideas

- Separate layout cost from render cost
- Prefer retained visuals that change cheaply
- Avoid invalidating more of the tree than necessary
- Reuse immutable graphical objects where possible
- Keep high-frequency updates tightly scoped
- Use caching and retained visual strategies deliberately when a surface is expensive to redraw

## Practical Heuristics

- Prefer `RenderTransform` over layout-affecting movement when possible.
- Use virtualization for large item collections.
- Freeze `Freezable` objects such as brushes, geometries, and transforms when they are static and reused.
- Consider `BitmapCache` or other retained-visual strategies when a complex visual is animated more than it is structurally changed.
- Be cautious with deep visual trees, excessive effects, and unnecessary opacity layers.
- Limit the frequency and scope of bindings or animations that update constantly.
- Understand which dependency property changes trigger measure, arrange, or render invalidation.

## Retained-Mode Mindset

WPF keeps a visual scene graph. Efficient UI work often comes from:

- Updating fewer properties
- Updating cheaper properties
- Updating a smaller part of the visual tree
- Reusing objects instead of recreating them

## Smells

- Animating `Width`, `Height`, or margins when a transform would do
- Large non-virtualized item controls
- Recreating brushes and geometries every frame-like update
- Performance fixes attempted before identifying the invalidation source

## Goal

Build and animate WPF UI in ways that respect the rendering pipeline and keep the experience smooth.
