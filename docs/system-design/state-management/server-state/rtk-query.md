# RTK Query

## What it is
A data-fetching and caching layer built into Redux Toolkit. It generates Redux slices, hooks, and cache-management logic from a declarative API definition, so server state lives in the Redux store but is managed automatically instead of by hand-written reducers/thunks.

## Why it's useful
- Eliminates the boilerplate of writing thunks, loading/error reducers, and manual caching for every endpoint.
- Integrates directly with an existing Redux store, so teams already using Redux don't need a second, separate data-fetching library.
- Provides automatic cache invalidation via "tags," so related queries refresh after a mutation.

## Classic use-cases
- Apps already using Redux Toolkit for client state that want to add server-state caching without introducing a new library.
- CRUD-heavy admin panels where mutations need to automatically invalidate and refresh related list/detail queries.
- Apps needing normalized, centralized state where server data and client state coexist in the same store.

## Pros
- No extra library needed if the app is already on Redux Toolkit — shares the same store and devtools.
- Declarative endpoint definitions auto-generate hooks (`useGetXQuery`, `useAddXMutation`).
- Tag-based cache invalidation is powerful for keeping related data in sync after mutations.
- Built-in support for polling, prefetching, and optimistic updates.

## Cons
- Ties server-state caching to Redux — adopting it without Redux elsewhere isn't the typical use case.
- Tag-based invalidation has a learning curve compared to TanStack Query's key-based model.
- Redux Toolkit's overall setup (store, slices, provider) is heavier than a standalone query library.
- Smaller ecosystem/community size for RTK Query specifically compared to TanStack Query.

## Interview questions
1. How does RTK Query's tag-based cache invalidation work, and how does it compare to TanStack Query's query-key invalidation?
2. Why would a team choose RTK Query over adding TanStack Query to a Redux Toolkit app?
3. How do you handle optimistic updates in RTK Query?
4. What generates the auto-generated hooks, and how does code-splitting work with `injectEndpoints`?
5. How would you structure `providesTags`/`invalidatesTags` for a normalized list + detail view pattern?
6. What are the tradeoffs of keeping server state inside the Redux store vs. a separate cache?
