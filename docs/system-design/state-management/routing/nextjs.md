# Next.js

## What it is
A full-stack React framework that provides file-system-based routing along with built-in support for multiple rendering strategies (SSR, SSG, ISR, and CSR) per route, plus API routes, middleware, image optimization, and bundling — all in one integrated toolchain.

## Why it's useful
- Routing is derived directly from the file/folder structure (`app/` or `pages/`), removing the need for a separate router library or manual route configuration.
- Each route can independently choose its rendering strategy — a marketing page can be statically generated while a dashboard page is server-rendered.
- Bundles the concerns that would otherwise require stitching together a router, a bundler, a server, and a rendering strategy by hand.

## Classic use-cases
- Content/marketing sites that want static generation for most pages and SSR for a few dynamic ones.
- Full-stack apps that want API routes and page routes living in the same codebase/deploy.
- E-commerce and content platforms using ISR for product/article pages that update occasionally.

## Pros
- File-based routing removes boilerplate route configuration entirely.
- Per-route rendering strategy selection (SSR/SSG/ISR/CSR) in a single framework.
- Built-in optimizations: image optimization, font loading, code splitting, prefetching links.
- Large ecosystem, strong Vercel-backed tooling, and wide industry adoption.

## Cons
- More opinionated and "batteries-included" than a plain router + bundler setup — less flexibility for unusual architectures.
- The App Router's React Server Components model is a significant paradigm shift with its own learning curve (server vs. client components, streaming).
- Framework lock-in: migrating off Next.js later touches routing, data-fetching, and build tooling all at once.
- Self-hosting to get full feature parity (ISR, image optimization, etc.) requires extra infrastructure vs. deploying on Vercel.

## Interview questions
1. How does Next.js's file-based routing map files/folders to routes, and how do dynamic segments work?
2. How would you choose between SSR, SSG, ISR, and CSR for different routes in the same Next.js app?
3. What is the difference between Server Components and Client Components in the App Router, and when do you need `"use client"`?
4. How do Next.js API routes compare to running a separate backend service?
5. How does Next.js handle code splitting and prefetching for linked routes?
6. What are the tradeoffs of hosting Next.js on Vercel vs. self-hosting for ISR/image optimization?
