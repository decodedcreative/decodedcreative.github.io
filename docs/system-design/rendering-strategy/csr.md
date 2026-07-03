# Client-Side Rendering (CSR)

## What it is
The server sends a mostly empty HTML shell plus a JavaScript bundle. The browser downloads and runs the JS, which then builds the page and fetches any data it needs. All rendering happens in the browser.

## Why it's useful
- Once loaded, navigation feels instant — no full page reloads, just JS swapping content in and out.
- Clear separation between frontend and backend (backend is just an API).
- Great for highly interactive, app-like experiences.

## Classic use-cases
- Web apps behind a login where SEO doesn't matter: admin dashboards, internal tools, SaaS products.
- Single Page Applications (SPAs) like Gmail, Trello, Figma-style tools.
- Apps with heavy client-side interactivity (drag-and-drop, real-time editing, complex forms).

## Pros
- Rich, app-like interactivity after initial load.
- Reduced server load — server just serves static assets and APIs.
- Easier to build as a pure frontend/backend split; simple hosting (static files on a CDN).
- Smooth client-side navigation without full-page reloads.

## Cons
- Slow initial load — blank/loading screen until JS downloads, parses, and runs.
- Poor SEO by default (crawlers may not execute JS, or index incomplete content).
- Weak performance on slow devices/networks (all rendering work happens on the client).
- Larger JS bundles as the app grows, increasing load time further.

## Interview questions
1. Why does CSR typically hurt SEO, and how can you work around it?
2. Explain the loading sequence of a CSR app from first request to interactive.
3. What's the difference between CSR and an SPA — are they the same thing?
4. How would you improve the initial load time of a CSR app (code splitting, lazy loading, etc.)?
5. When would you choose CSR over SSR/SSG for a given product?
6. How does client-side routing work without full page reloads?
7. What are the tradeoffs of shipping a large JS bundle for CSR?
8. How do you handle authentication and protected routes in a CSR app?
