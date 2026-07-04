# React Router

## What it is
The most widely used client-side routing library for React, mapping URL paths to components so a single-page app can render different views without a full page reload. Modern versions (v6.4+) also support data loaders, actions, and nested routes that closely resemble server-rendered routing patterns.

## Why it's useful
- Enables SPA navigation (no full page reload) while keeping the URL in sync with what's displayed.
- Supports nested routes and layouts, so shared UI (headers, sidebars) doesn't need to be re-rendered per page.
- Newer data APIs (`loader`, `action`) let route transitions fetch data before rendering, reducing loading-spinner waterfalls.

## Classic use-cases
- Any client-side-rendered React SPA that needs multiple "pages"/views tied to distinct URLs.
- Apps needing nested layouts (e.g., a dashboard shell with different content per sub-route).
- Apps migrating toward data-loader-based routing to prefetch data per route instead of fetching inside components after mount.

## Pros
- De facto standard for React routing — huge community, documentation, and Stack Overflow coverage.
- Nested routes and layouts map naturally to nested UI structure.
- Data APIs (loaders/actions) bring some of the benefits of server-driven routing (prefetching, pending states) to a client-only SPA.
- Framework-agnostic beyond React Router itself; works with any bundler/build setup.

## Cons
- Client-side-only routing means the initial HTML is typically blank until JS loads (unless paired with SSR).
- The data APIs (loaders/actions) are a different mental model from the simpler `<Route>`-only usage of older versions, adding a learning curve.
- Doesn't handle SEO/SSR itself — needs a framework (Next.js, Remix) or extra setup for that.
- Version churn (v5 → v6 → data APIs) means a lot of outdated tutorials/patterns still circulate.

## Interview questions
1. How does React Router keep the browser URL in sync with the rendered component tree without full page reloads?
2. What problem do the `loader`/`action` data APIs solve compared to fetching data in a `useEffect` after mount?
3. How do nested routes and layouts work, and what's the benefit over one flat route list?
4. How would you implement route-based code splitting with React Router?
5. Compare client-side routing (React Router) to server-driven routing/frameworks like Next.js — what SEO/perf tradeoffs exist?
6. How do you handle protected/authenticated routes with React Router?
