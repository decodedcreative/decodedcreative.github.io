# Hydration

## What it is
The process of attaching event handlers and reactive state to server-rendered HTML on the client, turning static markup into a fully interactive page. Different strategies trade off cost and complexity: **full hydration** (classic React SSR — the entire tree hydrates before anything is interactive), **selective/progressive hydration** (React 18 with Suspense — parts of the tree hydrate independently and out of order), **partial hydration / islands** (Astro — only specific interactive "islands" ship JS at all, the rest stays static HTML forever), and **resumability** (Qwik — skips hydration entirely, resuming exactly where the server left off instead of re-executing everything on the client).

## Why it's useful
- Bridges the gap between "fast to display" (server-rendered HTML) and "usable" (client-side interactivity), which is the fundamental tradeoff SSR introduces.
- Selective/partial hydration strategies mean the cost of hydration is no longer all-or-nothing — a page with mostly static content can ship dramatically less JS.
- Understanding the different models lets you reason about *why* a given app feels slow to become interactive even though it painted quickly.

## Classic use-cases
- Any traditional SSR app (full hydration) needing to become interactive after the initial HTML paints.
- Content-heavy sites (blogs, marketing pages, docs) using islands architecture so 95% of the page ships zero JS.
- Large, complex apps using selective hydration so critical/visible parts of the UI become interactive before less important, off-screen parts.

## Pros
- Lets an app get the fast-paint benefit of server rendering while still becoming fully interactive.
- Non-full-hydration strategies (islands, resumability, selective) directly attack the JS-cost problem that plain SSR doesn't solve on its own.
- A well-understood, actively evolving area — meaningful performance wins are available by choosing the right strategy for a given app's interactivity profile.

## Cons
- Hydration cost is a genuine Time-to-Interactive/INP killer for full-hydration apps with large component trees — the page looks ready before it actually is.
- Hydration mismatches (server-rendered tree not matching what the client would render) cause visible flicker or outright errors, and can be subtle to debug.
- Without RSC, you can end up "double fetching" data — once on the server to render HTML, again on the client during hydration — unless deliberately avoided.

## Interview questions
1. What's the difference between full hydration, selective hydration, and islands architecture, and what problem does each progressively solve?
2. What causes a hydration mismatch, and what does the user actually see when one happens?
3. How does Qwik's "resumability" avoid hydration entirely, and what's the tradeoff of that approach?
4. Why can a server-rendered page look ready before it's actually interactive, and what metric captures that gap?
5. How do you avoid double data-fetching (once on the server, once again during client hydration) in a traditional SSR app?
