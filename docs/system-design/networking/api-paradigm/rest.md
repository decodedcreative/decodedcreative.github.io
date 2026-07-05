# REST

## What it is
An architectural style for APIs organized around resources (nouns — `/users/123`) manipulated through standard HTTP methods (GET, POST, PUT, DELETE) with predictable, cacheable semantics. Each endpoint returns a fixed, server-defined response shape for that resource.

## Why it's useful
- Maps naturally onto HTTP itself — caching, status codes, and methods all carry standard, well-understood meaning without inventing a new convention layer on top.
- Simple, predictable contract per endpoint makes REST APIs easy to understand, cache at the HTTP layer (CDNs, browsers), and debug with generic tools (curl, browser devtools).
- Well-suited to simple, resource-shaped data access where the client generally wants "the whole resource" rather than an arbitrary custom shape.

## Classic use-cases
- CRUD-style APIs where resources map cleanly to entities (users, orders, products).
- Public APIs where broad tooling compatibility (caching proxies, API gateways, generic HTTP clients) matters more than flexible querying.
- Simple client needs where a fixed response shape per endpoint is sufficient and doesn't require picking and choosing fields.

## Pros
- Leverages standard HTTP semantics (caching, status codes, methods) for free, understood by virtually every tool in the ecosystem.
- Simple mental model — one endpoint per resource/action, predictable responses.
- Excellent tooling and infrastructure support (HTTP caching, API gateways, monitoring) built around REST conventions for decades.

## Cons
- Over-fetching (getting more fields than needed) and under-fetching (needing multiple round trips to assemble a full picture) are common as client data needs diverge from the server's fixed resource shape.
- Aggregating data from multiple resources typically means multiple round trips or bespoke aggregation endpoints, unlike GraphQL's single-query aggregation.
- Versioning a REST API's contract (when the resource shape needs to change) requires deliberate strategy (URL versioning, content negotiation) since there's no built-in mechanism for it.

## Interview questions
1. What does "resource-oriented" mean in REST, and how does that map to HTTP methods and status codes?
2. What's the difference between over-fetching and under-fetching, and why does REST commonly run into both?
3. How would you version a REST API's contract without breaking existing clients?
4. Why is a REST API generally easier to cache at the HTTP/CDN layer than a GraphQL API?
5. How would you design a REST endpoint to aggregate data from multiple underlying resources for a single client view?
