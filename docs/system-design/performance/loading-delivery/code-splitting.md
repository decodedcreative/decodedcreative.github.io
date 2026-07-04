# Code Splitting & Lazy Loading

## What it is
Breaking a JavaScript bundle into smaller chunks that are loaded on demand instead of all upfront. In React, this is typically done with dynamic `import()` and `React.lazy`, so a route or component's code is only fetched when it's actually needed.

## Why it's useful
- Shrinks the initial bundle a user has to download before the app becomes interactive.
- Defers the cost of rarely-used features (admin panels, modals, heavy widgets) until they're actually opened.
- Pairs naturally with route-based splitting, since most users only visit a subset of an app's routes per session.

## Classic use-cases
- Splitting each route in a single-page app so users only download the code for the page they're on.
- Lazy-loading heavy, rarely-used components (rich text editors, charting libraries, modals).
- Deferring below-the-fold or admin-only functionality that most visitors never trigger.

## Pros
- Directly reduces Time to Interactive by shrinking the initial JS payload.
- Scales well as an app grows — new features don't have to bloat every user's initial download.
- Framework support is mature (`React.lazy`/`Suspense`, Next.js automatic route splitting).

## Cons
- Adds loading states (spinners/skeletons) that need to be designed for each split boundary.
- Poorly chosen split points can create request waterfalls (chunk A loads, then triggers chunk B, etc.).
- Overly granular splitting increases the number of network requests, which can hurt performance on high-latency connections.

## Interview questions
1. How does `React.lazy` combined with `Suspense` work under the hood?
2. What's the difference between route-based and component-based code splitting, and when would you use each?
3. How would you decide where to draw split boundaries in a large app?
4. What is a request waterfall, and how can bad code-splitting decisions cause one?
5. How do you handle the loading state UX for a lazily-loaded component without causing layout shift?
