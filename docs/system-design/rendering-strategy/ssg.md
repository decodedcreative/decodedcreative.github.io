# Static Site Generation (SSG)

## What it is
HTML pages are generated once, ahead of time, at build time — not per request. The output is a set of plain HTML/CSS/JS files that get deployed to a CDN and served directly, with no server-side rendering work at request time.

## Why it's useful
- Serving pre-built files from a CDN is about as fast and cheap as it gets.
- No server rendering cost per request, so it scales to huge traffic with minimal infrastructure.
- Great SEO — search engines get complete, ready-made HTML.

## Classic use-cases
- Marketing sites, landing pages, documentation sites.
- Blogs and content sites where content doesn't change on every request (e.g., built with Gatsby, Hugo, Jekyll, Next.js `getStaticProps`).
- E-commerce catalog pages that update infrequently (rebuilt periodically or via webhook on content change).

## Pros
- Extremely fast load times — files are pre-built and served from a CDN edge.
- Cheap and simple to host; scales effortlessly under traffic spikes.
- Excellent SEO.
- Very secure — no live server/database to attack per request.

## Cons
- Content can go stale between builds — not suitable for frequently changing or personalized data.
- Build times grow with the number of pages; can become slow for very large sites (thousands+ of pages).
- Any content update requires a full (or partial) rebuild and redeploy.
- Not a good fit for per-user or real-time content.

## Interview questions
1. How does SSG differ from SSR in terms of when rendering happens?
2. What happens when a site has 100,000 pages — how do you keep build times manageable?
3. How do you handle content that changes after the site has been built and deployed?
4. What's the deployment pipeline for an SSG site typically look like (build, CDN, cache invalidation)?
5. When would SSG be the wrong choice, even though it's the fastest option?
6. How do webhooks/CMS integrations trigger rebuilds for SSG sites?
7. Compare SSG vs. SSR vs. ISR — what's the decision framework?
