# HTTP Caching & CDN

## What it is
HTTP caching uses response headers (`Cache-Control`, `ETag`, `Last-Modified`) to tell browsers and intermediate caches how long a resource can be reused without re-fetching it. A CDN (Content Delivery Network) extends this by caching and serving assets from edge servers geographically close to the user, reducing the distance data has to travel.

## Why it's useful
- Avoids re-downloading unchanged assets (JS bundles, images, fonts) on repeat visits, cutting load time to near-zero for cached resources.
- Serving from a nearby edge location reduces network latency compared to hitting a single origin server across the world.
- Reduces origin server load, since most requests are served directly from cache/edge without reaching the backend.

## Classic use-cases
- Long-lived caching (with content-hashed filenames) for static JS/CSS/image bundles.
- CDN-fronted static sites and APIs to serve global users with low latency.
- Short-lived or revalidated caching for semi-dynamic content (e.g., an article page that updates occasionally).

## Pros
- One of the highest-leverage, lowest-effort performance wins for repeat visits.
- CDNs reduce both latency (geography) and origin load (fewer requests hit the backend).
- Cache headers are a web standard supported everywhere — no special client code needed.

## Cons
- Cache invalidation is a classically hard problem — stale content can be served if headers/invalidation aren't managed carefully.
- Overly aggressive caching of dynamic/personalized content can leak stale or incorrect data to users.
- Adds an extra layer (CDN configuration, cache-busting via filenames) that needs to be understood and maintained.

## Interview questions
1. What's the difference between `Cache-Control: max-age`, `no-cache`, and `no-store`?
2. How do `ETag`/`Last-Modified` enable revalidation instead of a full re-download?
3. How does content-hashing filenames (e.g., `app.a1b2c3.js`) solve cache invalidation for static assets?
4. How does a CDN decide whether to serve from cache or forward a request to the origin?
5. What are the risks of caching a response that contains user-specific/personalized data?
