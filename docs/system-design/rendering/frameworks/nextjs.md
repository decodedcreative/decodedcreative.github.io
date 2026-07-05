# Next.js

## What it is
A full-stack React meta-framework where the App Router is RSC-first by default — every component is a Server Component unless explicitly marked `"use client"`. It lets a single app mix rendering strategies per route (SSR, SSG, ISR, and Partial Prerendering) rather than committing the whole app to one model, with routing, data fetching, and streaming all expressed through the same file-based conventions.

## Why it's useful
- Makes React Server Components practical to adopt, since the framework (not the app) handles the server/client wiring, streaming, and bundling that RSC requires.
- Per-route rendering strategy selection means a marketing page can be static while a dashboard is server-rendered, without needing separate apps or infrastructure.
- Partial Prerendering (PPR) — a static shell with streaming dynamic "holes" in a single response — is a direct product of Next.js's opinionated integration of Suspense, streaming, and static generation.

## Classic use-cases
- Content sites wanting SSG/ISR for most pages, SSR for a few personalized/dynamic ones, all within one app.
- Products adopting React Server Components without wanting to hand-build the streaming/bundling infrastructure RSC requires.
- Teams wanting file-based routing, API routes, and rendering-strategy choice unified under one framework rather than assembled from separate tools.

## Pros
- The most mature, widely-adopted path to using RSC and mixed rendering strategies in production today.
- Strong defaults and conventions reduce the amount of infrastructure decision-making a team has to do from scratch.
- Backed by significant tooling investment (image optimization, font loading, edge streaming support).

## Cons
- The App Router's RSC-first model is a genuinely different mental model from the earlier Pages Router, and migrating between them is nontrivial (a widely-felt pain point).
- Being opinionated means less flexibility for architectures that don't fit the framework's assumptions.
- RSC support requires ecosystem libraries to have been updated for compatibility — not everything works seamlessly yet.

## Interview questions
1. What does "RSC-first by default" mean in the App Router, and how does `"use client"` opt out of it?
2. How does Partial Prerendering combine static generation and streaming in a single response?
3. What made migrating from the Pages Router to the App Router a significant undertaking for existing apps?
4. How would you decide which rendering strategy (SSR/SSG/ISR/PPR) fits a given route?
5. What are the tradeoffs of committing to a highly opinionated meta-framework like Next.js vs. assembling a more custom stack?
