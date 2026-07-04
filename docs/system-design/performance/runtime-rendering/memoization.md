# Memoization

## What it is
Caching the result of an expensive computation or a component's rendered output so it isn't recalculated/re-rendered unless its inputs actually change. In React, this is done with `React.memo` (skip re-rendering a component if props are unchanged), `useMemo` (cache a computed value), and `useCallback` (cache a function reference).

## Why it's useful
- Avoids redundant re-renders of components whose props haven't meaningfully changed, especially in large trees.
- Prevents expensive calculations (sorting, filtering, derived data) from re-running on every render.
- Stabilizes function/object references passed as props or dependencies, avoiding unnecessary downstream re-renders or effect re-runs.

## Classic use-cases
- A large list where only one item's data changes but the rest shouldn't re-render.
- An expensive derived value (e.g., filtering/sorting thousands of rows) recomputed only when the source data changes.
- Passing a stable callback to a memoized child component so it doesn't re-render just because the parent re-rendered.

## Pros
- Can meaningfully cut wasted render work in components with expensive subtrees or computations.
- Fine-grained — you memoize exactly the components/values that need it.
- Well-supported, built into React with no extra dependency.

## Cons
- Memoization itself has a cost (comparing props, storing cached values) — overusing it on cheap components can make things slower, not faster.
- Easy to memoize incorrectly (e.g., passing a new object/array literal as a prop) and silently defeat the optimization.
- Adds cognitive overhead — `useMemo`/`useCallback` dependency arrays are a common source of subtle bugs (stale closures).

## Interview questions
1. When does memoization actually help, and when does it add overhead without benefit?
2. What's the difference between `useMemo` and `useCallback`, and when do you need each?
3. How can passing a new object or array literal as a prop silently break `React.memo`?
4. What is a "stale closure" bug, and how does an incorrect `useMemo`/`useCallback` dependency array cause it?
5. How would you profile a React app to find components that would actually benefit from memoization?
