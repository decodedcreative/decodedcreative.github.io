# Zustand

## What it is
A small, unopinionated state-management library for React that creates a store using a single hook, with no providers or boilerplate required. Components subscribe to just the slices of state they use, re-rendering only when those slices change.

## Why it's useful
- Minimal API surface (`create`, a hook, and plain functions to update state) compared to Redux's actions/reducers/dispatch pattern.
- No `Provider` wrapper needed — the store is just a hook importable from anywhere.
- Selective subscriptions mean components only re-render when the specific state they read changes.

## Classic use-cases
- Global UI state shared across distant components (e.g., theme, modal/sidebar open state, current user).
- Mid-sized apps that find Redux too heavyweight but React Context's re-render behavior too coarse.
- Cross-cutting client state that doesn't belong to any single component tree (e.g., shopping cart, auth state).

## Pros
- Very little boilerplate — a store can be defined in a few lines.
- No context provider required, avoiding provider-nesting ("wrapper hell").
- Fine-grained subscriptions avoid unnecessary re-renders without needing `useMemo`/`useSelector` ceremony.
- Works outside React components too (plain JS store), useful for non-React logic.

## Cons
- Less structure/convention than Redux, which can lead to inconsistent patterns across a large team.
- Fewer built-in dev tools and middleware conventions than Redux's mature ecosystem (though Redux Devtools integration exists).
- No built-in server-state features (caching, refetching) — still needs TanStack Query/RTK Query alongside it for API data.
- Smaller talent-pool familiarity compared to Redux, which is more commonly taught/interviewed for.

## Interview questions
1. How does Zustand avoid unnecessary re-renders compared to React Context?
2. Why doesn't Zustand require a `Provider` component, and what are the tradeoffs of that design?
3. How would you structure a large Zustand store — one big store or multiple slices?
4. Compare Zustand to Redux Toolkit: when would you pick one over the other?
5. How do you handle derived/computed state in Zustand?
6. How would you persist Zustand state to local storage, and what are the pitfalls of doing so?
