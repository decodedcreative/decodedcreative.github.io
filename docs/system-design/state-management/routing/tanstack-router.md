# TanStack Router

## What it is
A fully type-safe routing library for React (part of the TanStack family alongside TanStack Query) that infers route params, search params, and loader data end-to-end in TypeScript. Routes can be defined in code or generated from a file-based structure, with built-in data-loading integration.

## Why it's useful
- End-to-end type safety: navigating to a route, reading its params, and accessing loader data are all statically checked.
- Built-in first-class support for typed search-params (query strings) as real application state, not just strings to parse manually.
- Integrates cleanly with TanStack Query for route-level data loading and caching.

## Classic use-cases
- TypeScript-heavy React SPAs that want compile-time guarantees that a link or redirect points to a valid route with correct params.
- Apps that store meaningful UI state in the URL's search params (filters, pagination, sort order) and want that typed and validated.
- Projects already using TanStack Query that want route loaders to prefetch and cache data consistently.

## Pros
- Strongest type-safety story among React routers — invalid routes/params are caught at compile time.
- First-class typed search-param state, avoiding manual `URLSearchParams` parsing/validation.
- Built-in route loaders, pending states, and error boundaries per route.
- Framework-agnostic core with an ecosystem shared with TanStack Query/Table.

## Cons
- Newer and smaller community/ecosystem than React Router.
- The type-safety benefits require committing to its specific route-definition patterns, which is a bigger shift than a simple router.
- Less prevalent in existing job postings/interviews compared to React Router or Next.js routing.
- Meta-framework features (SSR, file-based routing, deployment) are less mature than Next.js's.

## Interview questions
1. What does "fully type-safe routing" mean in practice, and what bugs does it prevent that a normal router wouldn't catch?
2. How does TanStack Router treat search params as first-class typed state, and why does that matter for filters/pagination?
3. How do route loaders work, and how do they interact with TanStack Query's cache?
4. Compare TanStack Router to React Router — what's the core value proposition of choosing it?
5. How would you migrate an existing React Router app to TanStack Router, and what's the biggest risk in doing so?
