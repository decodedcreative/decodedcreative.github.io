# Abort Controller

## What it is
A browser API (`AbortController` + `AbortSignal`) for cancelling an in-flight asynchronous operation — most commonly a `fetch` request — from outside the operation itself. You create a controller, pass its `signal` into the request, and calling `controller.abort()` cancels it, rejecting the associated promise.

## Why it's useful
- Prevents wasted work and wasted bandwidth from requests the app no longer cares about — a user navigating away or changing a search query before the previous request resolves.
- Avoids race conditions where a slow, now-irrelevant response arrives after a newer one and incorrectly overwrites current UI state ("out of order responses").
- Composable with timeouts (`AbortSignal.timeout()`) and combined conditions, giving fine-grained control over when a request should be cancelled.

## Classic use-cases
- Cancelling an in-flight search-as-you-type request when the user types a new character before the previous request resolves.
- Cancelling requests tied to a component that unmounted before its data fetch completed.
- Implementing request timeouts, aborting a fetch that's taking too long rather than waiting indefinitely.

## Pros
- Directly prevents a whole category of race-condition bugs where a stale response overwrites newer state.
- Native browser API — no library required, works directly with `fetch`.
- Composable with other abort conditions (timeout, user-triggered cancel) via combined signals.

## Cons
- Requires deliberate wiring — a `fetch` call not given a signal simply can't be cancelled after the fact.
- Aborting doesn't automatically undo server-side side effects already triggered by the request (e.g., a POST that already reached the server) — cancellation is a client-side concern only.
- Easy to forget in a codebase that doesn't have a systematic pattern (e.g., inside a shared data-fetching hook) for wiring it up on every request.

## Interview questions
1. How does `AbortController` prevent a race condition where an older, slower response overwrites a newer one?
2. What happens server-side when a client aborts a request that's already reached the server (e.g., a POST)?
3. How would you implement a request timeout using `AbortController`?
4. Where in a React component's lifecycle would you abort an in-flight fetch, and why?
5. How would you combine multiple abort conditions (e.g., a timeout and a user-triggered cancel) for a single request?
