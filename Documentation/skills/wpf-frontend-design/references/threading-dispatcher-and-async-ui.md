---
name: threading-dispatcher-and-async-ui
version: 1.0
---

# Threading, Dispatcher, and Async UI

## Use This Reference When

- Background work needs to update the UI safely
- Async loading, progress reporting, or cancellation behavior is being designed
- Observable collections are being updated from multiple threads
- UI-thread ownership or dispatcher behavior is causing bugs or stalls

## Veteran Expert Stance

WPF has a strict UI-thread model. Good async UI engineering respects that model instead of poking at it until the app "mostly works." Smooth desktop experiences come from moving expensive work off the UI thread while returning UI mutations to the dispatcher deliberately and predictably.

## Core Concepts

- The dispatcher owns the UI thread
- Most UI elements have thread affinity
- `SynchronizationContext` influences how continuations return to the UI
- `ObservableCollection` is not magically thread-safe
- Cancellation, progress, and busy state are part of UX, not just plumbing

## Practical Heuristics

- Move expensive I/O or computation off the UI thread.
- Marshal UI-bound mutations back through the dispatcher when needed.
- Use async-aware command patterns so the view can observe running state naturally.
- Keep progress reporting meaningful and bindable.
- Use cancellation when users might navigate away, retry, or close the workflow.
- Use `EnableCollectionSynchronization` or other deliberate coordination patterns when collections genuinely need cross-thread interaction.
- Avoid flooding the dispatcher with too many fine-grained updates.

## Collection Synchronization

Collection work is one of the easiest places to create flaky UI:

- Prefer batching updates where possible
- Be careful when background workers produce many small item changes
- Remember that a thread-safe producer does not automatically imply a thread-safe bound collection

If the collection is large and hot, performance and threading concerns should be considered together.

## Smells

- Long-running work on the UI thread
- Fire-and-forget async work that can fail invisibly
- Background threads mutating bound collections directly
- Progress indicators that are manually toggled and drift out of sync
- Dispatcher usage sprayed everywhere because ownership boundaries were never designed

## Goal

Build WPF experiences that remain responsive under real async work by respecting UI-thread affinity, coordinating dispatcher usage deliberately, and exposing async state clearly to the presentation layer.
