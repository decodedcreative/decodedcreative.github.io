# Server-Side Rendering (SSR)

## What it is
The server generates the full HTML for a page on each request and sends it to the browser already populated with content. The browser then "hydrates" it — attaching JavaScript so it becomes interactive.

## Why it's useful
- Users see meaningful content immediately, without waiting for JS to download and run.
- Search engines and social media crawlers get real HTML to index/preview, no JS execution required.
- Works well on slow devices/networks since the heavy rendering work happens on the server.

## Classic use-cases
- Content sites where SEO matters: news sites, blogs, marketplaces, e-commerce product pages.
- Pages with per-request personalization (logged-in dashboards, localized pricing).
- Social sharing cards that need real meta tags/content in the initial HTML.

## Pros
- Fast perceived load (First Contentful Paint) — content is visible before JS runs.
- Strong SEO out of the box.
- Always fresh data — rendered per request.
- Works without JavaScript enabled (basic content at least).

## Cons
- Higher server load — every request costs CPU time to render.
- Slower Time to First Byte (TTFB) compared to serving static files, since rendering happens synchronously per request.
- More complex infrastructure (need a running server, not just a CDN).
- "Hydration" can cause a delay between page looking interactive and actually being interactive.

## Interview questions
1. Walk me through what happens between a browser request and a fully interactive SSR page.
2. What is hydration, and what problems can it cause (e.g., hydration mismatch)?
3. How does SSR affect Time to First Byte vs. Time to Interactive?
4. How would you scale an SSR application under high traffic?
5. Compare SSR vs. CSR for SEO and explain why.
6. What is "streaming SSR" and how does it improve perceived performance?
7. How do you handle caching for SSR pages that are expensive to render?
8. What are common causes of a hydration mismatch error, and how do you debug one?
