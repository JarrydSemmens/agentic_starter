---
name: data-templating-and-items-controls
version: 1.1
---

# Data Templating and Items Controls

## Use This Reference When

- Building list, grid, tree, menu, or repeated-item UI
- Choosing between `DataTemplate`, `ItemContainerStyle`, and custom item containers
- Using `CollectionViewSource`, grouping, sorting, or filtering
- Tuning item-template complexity, container generation, or virtualization behavior

## Veteran Expert Stance

In WPF, repeated UI is usually a data templating problem before it is a custom control problem. The shape of item presentation, the item container, the panel, and the collection view all matter, and high-quality WPF work keeps those layers distinct.

## Core Layers

- Data item or view model
- `DataTemplate` for visual presentation
- Container such as `ListBoxItem` or `TreeViewItem`
- `ItemContainerStyle` for container behavior and chrome
- `ItemsPanelTemplate` for layout strategy
- Collection view for sorting, grouping, filtering, and current item behavior

When one of these layers is misused, the whole item surface gets harder to reason about.

## Practical Heuristics

- Use `DataTemplate` for the item's visuals.
- Use `ItemContainerStyle` for selection chrome, focus behavior, padding, alignment, and per-container state.
- Use `ItemsPanelTemplate` to control layout behavior and virtualization compatibility.
- Use `DataTemplateSelector` only when template selection truly depends on runtime branching that cannot be expressed more simply.
- Use `HierarchicalDataTemplate` for tree-like presentation when the hierarchy is data-driven.
- Keep item templates shallow. Virtualization helps count, not per-item cost.
- Use `CollectionViewSource` or the collection view layer instead of rebuilding sorted or grouped UI manually.

## Grouping, Sorting, And Filtering

Collection views are the native WPF place for these concerns:

- Sort at the view layer when the ordering is presentation-specific
- Group at the view layer when visual grouping is a UI concern
- Filter at the view layer when the filter is screen-specific
- Keep the underlying domain collection free of view-only restructuring where possible

The collection view is part of presentation architecture, not an afterthought.

## Virtualization Interactions

Item UIs often become slow because the item system and the panel system are working against each other:

- Prefer virtualizing panels where supported
- Be careful with nested scroll viewers
- Be careful with grouping because it can affect virtualization behavior
- Avoid item templates that behave like mini applications
- Remember that container generation cost matters in addition to template cost

## Smells

- Building repeated item UI by manually adding controls in code
- Pushing selection or container chrome into the data template instead of the item container
- Massive item templates with deep panel nesting and many bindings
- Using template selectors where a small number of typed templates or triggers would be clearer
- Treating grouping, sorting, or filtering as imperative collection rebuilding

## Goal

Build item-driven WPF surfaces that stay declarative, performant, and understandable by keeping data templates, containers, panels, and collection views in their proper roles.
