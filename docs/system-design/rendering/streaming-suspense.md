# Streaming & Suspense

## What it is
Shipping a page's HTML in chunks as each part becomes ready, rather than waiting for the entire page (including its slowest data dependency) before sending anything. In React, Suspense boundaries mark the units that can stream independently — the shell and fast content go out immediately, while a boundary waiting on slow data streams in later, out of order, once it resolves.

## Why it's useful
- Lets fast content reach the browser (and start painting) without being blocked by the single slowest data dependency on the page.
- Suspense boundaries make "what can load independently" an explicit, declarative decision in the component tree, rather than something hidden inside data-fetching logic.
- Out-of-order streaming means a boundary that resolves later doesn't hold up boundaries that were already ready — each streams in as soon as it can.

## Classic use-cases
- A page with a fast primary content area and a slower secondary widget (e.g., recommendations, comments) — the primary content streams immediately, the slower widget fills in after.
- Dashboards composing several independently-loading data sources, each in its own Suspense boundary.
- Server Components streaming their rendered output progressively as different parts of a data-fetching tree resolve.

## Pros
- Directly improves perceived performance — meaningful content appears sooner, without waiting on the slowest dependency.
- Declarative boundary placement (`<Suspense>`) is a clean way to express "this part can load independently" directly in the component tree.
- Pairs naturally with error boundaries per Suspense boundary, isolating failures to just the part that failed rather than the whole page.

## Cons
- Boundary placement is a real design decision — too coarse and you get no streaming benefit; too fine and you get a page that visibly "pops in" piece by piece in a jarring way.
- Every streamed boundary needs a deliberate loading state, turning what used to be implicit into UI you have to design.
- Streaming shifts the tradeoff toward lower Time to First Byte at the cost of pushing some rendering work later — it doesn't eliminate total work, just reorders when the user sees it.

## Interview questions
1. How does streaming SSR technically differ from traditional SSR that waits for the full page before responding?
2. How would you decide where to place Suspense boundaries — what makes a boundary too coarse or too fine?
3. What's the relationship between streaming, Time to First Byte, and Largest Contentful Paint?
4. Why does each Suspense boundary typically need its own paired error boundary?
5. How does out-of-order streaming let a slow boundary resolve later without blocking boundaries that were already ready?
