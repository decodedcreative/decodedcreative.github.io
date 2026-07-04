# Concurrent React

## What it is
A set of React features (`startTransition`, `useDeferredValue`, Suspense) that let React interrupt, pause, or deprioritize rendering work so the browser can stay responsive to urgent updates (like typing or clicks) even while a large, non-urgent render is in progress.

## Why it's useful
- Lets an app mark certain updates as "non-urgent" (transitions) so React can keep the UI responsive instead of blocking on a big re-render.
- `useDeferredValue` lets a slow-to-render value (e.g., search results for a large list) lag slightly behind an input without freezing the input itself.
- Suspense integrates data-fetching and code-splitting with rendering, showing fallback UI while parts of the tree aren't ready, without manual loading-state plumbing everywhere.

## Classic use-cases
- A search-as-you-type UI where typing must stay instantly responsive even though the results list is expensive to render.
- A tab switch or filter change that triggers a large re-render, where you want the old UI to stay interactive until the new one is ready.
- Data-fetching component trees using Suspense to declaratively show loading states instead of manual `isLoading` checks everywhere.

## Pros
- Improves perceived responsiveness without needing to manually chunk work or debounce renders by hand.
- Declarative model (mark this update as a transition) is simpler than hand-rolled scheduling logic.
- Suspense unifies loading-state handling for code and data across a component tree.

## Cons
- Adds a new mental model (urgent vs. non-urgent updates) that takes time to learn and reason about correctly.
- Not a silver bullet — genuinely expensive renders are still expensive; concurrency just changes how that cost is scheduled, not the total amount of work.
- Suspense for data fetching requires the data layer (or a framework) to integrate with it correctly; not all libraries support it fully.

## Interview questions
1. What problem does `startTransition` solve that plain synchronous rendering can't?
2. How does `useDeferredValue` differ from debouncing the input value manually?
3. How does Suspense change the way loading states are handled compared to manual `isLoading` flags?
4. Does concurrent rendering make a slow computation faster, or does it just change when that cost is paid? Explain.
5. What's an example of a UI interaction that clearly benefits from marking an update as a transition?
