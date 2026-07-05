# Remix

## What it is
A React meta-framework built around a `loader`/`action` model tied directly to routes: each route defines a `loader` for fetching the data it needs and an `action` for handling form submissions/mutations, both running on the server. Remix leans heavily on web platform fundamentals — real `<form>` elements, HTTP semantics — treating progressive enhancement as a first-class design goal rather than an afterthought.

## Why it's useful
- The `loader`/`action` model gives each route explicit, colocated control over its own data fetching and mutations, avoiding the scattered `useEffect` data-fetching patterns common in older React apps.
- Building on real `<form>` elements and standard HTTP means the app can meaningfully function (navigate, submit forms) even before JavaScript has finished loading, or if it fails entirely.
- Nested routes map directly to nested layouts and nested data loading, so parent layout data doesn't get needlessly refetched when only a child route changes.

## Classic use-cases
- Apps that want data mutations (create/update/delete) to work through standard form submissions rather than custom client-side fetch logic.
- Products where progressive enhancement genuinely matters — resilience to slow or failed JS, not just a checkbox concern.
- Nested layouts with independent data needs per level (e.g., a dashboard shell, a project layout, a task detail — each loading its own data).

## Pros
- Progressive enhancement is baked into the framework's core model, not bolted on — actions work as real form submissions with or without JS.
- Colocated `loader`/`action` per route keeps data-fetching and mutation logic easy to find and reason about.
- Nested routing avoids redundant re-fetching of shared layout data.

## Cons
- The `loader`/`action` model is a different mental model from client-fetched data (TanStack Query, etc.) that teams coming from a client-heavy background need to adjust to.
- Less RSC-first than Next.js's App Router, so the specific benefits of Server Components (zero-JS components) aren't the framework's central bet in the same way.
- Smaller ecosystem/community than Next.js, meaning fewer third-party integrations and less prior art to draw on.

## Interview questions
1. How does the `loader`/`action` model differ from fetching data with `useEffect` or a client-side query library?
2. How does Remix achieve progressive enhancement so forms work even before JavaScript loads?
3. How do nested routes avoid re-fetching shared layout data when only a child route changes?
4. What's the tradeoff between Remix's loader/action model and an RSC-first framework like Next.js's App Router?
5. How would you handle client-side-only interactive state in an app built primarily around server loaders and actions?
