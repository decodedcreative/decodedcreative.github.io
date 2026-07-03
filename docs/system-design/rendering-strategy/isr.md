# Incremental Static Regeneration (ISR / "ISG")

Note: this pattern is most commonly called **ISR (Incremental Static Regeneration)**, popularized by Next.js. Some people call it "Incremental Static Generation" (ISG) — same idea, different name.

## What it is
A hybrid of SSG and SSR: pages are statically generated like SSG, but can be automatically regenerated in the background after a set time interval (or on-demand), without requiring a full site rebuild. Visitors get a fast static page, and the page quietly refreshes itself periodically.

## Why it's useful
- Gets the speed and low cost of static pages, without the staleness problem of pure SSG.
- Avoids rebuilding the entire site just because one page's content changed.
- Scales to sites with huge numbers of pages (e.g., large e-commerce catalogs) where full rebuilds would be too slow.

## Classic use-cases
- E-commerce product pages where prices/stock change occasionally but not every second.
- News/content sites that want mostly-static speed but can't rebuild on every edit.
- Large catalogs (thousands to millions of pages) where pre-building everything at once is impractical — pages can instead be generated on first request and cached ("on-demand ISR").

## Pros
- Combines static speed with fresher content than pure SSG.
- No full-site rebuild needed for content updates.
- Scales well to very large sites via on-demand generation.
- Reduces server load compared to SSR, since most requests hit a cached static page.

## Cons
- Content can still be briefly stale (served until the next regeneration completes) — typically uses "stale-while-revalidate" behavior.
- More complex caching/invalidation logic than plain SSG or SSR.
- Not ideal for truly real-time data (e.g., live stock prices, chat).
- Framework/hosting support varies — not all platforms support ISR natively.

## Interview questions
1. How does ISR differ from both SSG and SSR? Walk through the request lifecycle.
2. What is "stale-while-revalidate" and how does it apply to ISR?
3. How would you design on-demand ISR for a product catalog with a million SKUs?
4. What happens if two requests trigger a regeneration at the same time — how do you avoid duplicate work?
5. How do you handle cache invalidation when content is updated via a CMS webhook?
6. When would you choose ISR over SSR, and when would SSR still be necessary?
7. What are the failure modes of ISR (e.g., regeneration fails — what does the user see)?
