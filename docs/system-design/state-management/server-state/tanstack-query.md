# TanStack Query

## What it is
A data-fetching and server-state library (formerly React Query) that handles fetching, caching, synchronizing, and updating asynchronous data from a server. It treats server data as a distinct concern from client/UI state, managing loading/error states, background refetching, and cache invalidation automatically.

## Why it's useful
- Removes the need to hand-roll loading/error/caching logic around `fetch`/`axios` calls.
- Deduplicates identical requests fired from multiple components at once.
- Keeps server data fresh via background refetching, window-focus refetching, and polling, without manual wiring.

## Classic use-cases
- Fetching and caching REST API data in a dashboard with many independent widgets.
- Paginated or infinite-scroll lists that need cache-per-page and prefetching.
- Mutations (create/update/delete) that need optimistic updates and automatic cache invalidation afterward.

## Pros
- Automatic caching, deduplication, and background refetching out of the box.
- Built-in support for pagination, infinite queries, and optimistic updates.
- Framework-agnostic core with bindings for React, Vue, Svelte, Solid, etc.
- Devtools make cache state and query lifecycles easy to inspect.

## Cons
- Adds a dependency and a mental model (query keys, cache lifetimes) that takes time to learn.
- Not a replacement for global client state — still need something else (Context, Zustand, Redux) for pure UI state.
- Over-aggressive caching/refetch defaults can surprise newcomers if not configured (`staleTime`, `cacheTime`).
- Query key design becomes its own discipline; getting it wrong causes cache bugs.

## Interview questions
1. How does TanStack Query decide when to refetch a query, and how do `staleTime` and `cacheTime` (`gcTime`) differ?
2. What is a query key, and how do you structure them for a large app with many related queries?
3. How would you implement an optimistic update for a mutation, and how do you roll it back on failure?
4. How does TanStack Query handle request deduplication across multiple components?
5. When would you still need Redux/Zustand/Context alongside TanStack Query?
6. How do you handle pagination vs. infinite scrolling differently with this library?
7. How would you invalidate related queries after a mutation succeeds?
