# GraphQL

## What it is
A query language and runtime for APIs where the client specifies exactly which fields it needs across potentially multiple related resources in a single request, and the server resolves and returns exactly that shape — as opposed to REST's fixed, server-defined response per endpoint.

## Why it's useful
- Solves over-fetching and under-fetching directly: the client asks for precisely the fields it needs, in one request, even if that spans multiple underlying resources/services.
- A single, strongly-typed schema serves as a contract and living documentation for the whole API, with tooling (introspection, codegen) built around it.
- Aggregating data from multiple backend sources into one response is a first-class use case, not a bespoke aggregation endpoint you have to build by hand.

## Classic use-cases
- Client-driven UIs (mobile and web) where different screens need different slices of overlapping data, and a fixed REST shape would mean chronic over/under-fetching.
- Aggregating data from multiple microservices/backends into a single client-facing query via a GraphQL gateway.
- APIs serving many different client types (web, mobile, third-party) with different data needs from the same underlying resources.

## Pros
- Client gets exactly the shape of data it needs in one round trip, regardless of how many underlying resources that spans.
- Strongly-typed schema provides genuine API documentation and enables strong tooling (autocomplete, codegen, validation).
- Reduces the number of purpose-built aggregation endpoints a REST API would otherwise accumulate.

## Cons
- HTTP-layer caching (CDNs, browser cache) doesn't work the same way it does for REST, since most GraphQL traffic is POST requests with varying query bodies — caching has to be handled at the application/client layer instead.
- Poorly-designed queries can trigger the "N+1 problem" on the server (resolving a list, then separately querying for each item's related data), requiring deliberate batching (e.g., DataLoader).
- More operational complexity than REST: query cost/depth limiting, persisted queries, and schema evolution all need deliberate handling that REST's simpler model doesn't require.

## Interview questions
1. How does GraphQL solve REST's over-fetching and under-fetching problems?
2. Why is HTTP-layer caching harder for GraphQL than for REST, and how do teams work around that?
3. What is the N+1 problem in GraphQL, and how does a tool like DataLoader address it?
4. How would you protect a GraphQL API from a maliciously deep or expensive query?
5. When would you choose REST over GraphQL, even knowing GraphQL's flexibility advantages?
