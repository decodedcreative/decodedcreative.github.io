# BFF (Backend For Frontend)

## What it is
A dedicated backend service built specifically for one frontend (web, mobile, etc.), sitting between the client and the various downstream services/microservices it actually needs. Rather than the client talking directly to many internal services, it talks to one BFF that aggregates, reshapes, and simplifies those services into exactly what that frontend needs — nothing more. This is a decision about *who owns the aggregation boundary*, independent of whether that BFF happens to expose REST or GraphQL to the client.

## Why it's useful
- Removes the client's need to know about (or directly call) every downstream service — it talks to one purpose-built layer instead of orchestrating multiple calls itself.
- Reduces the client's exposed security surface: internal services, auth tokens for those services, and internal network topology never need to be reachable from the browser at all.
- Lets each frontend (web vs. mobile) get a tailored contract shaped exactly for its own needs, rather than every client consuming the same generic, one-size-fits-all API.

## Classic use-cases
- A frontend that needs data assembled from several internal microservices in one screen, where doing that orchestration client-side would mean multiple round trips and exposed internal endpoints.
- Different client types (web, iOS, Android) each getting their own tailored BFF, shaped for that client's specific needs rather than a shared generic API.
- Hiding legacy or internal-only services behind a clean, purpose-built contract so the frontend never has to deal with their quirks directly.

## Pros
- Meaningfully shrinks the client's attack surface — internal services are never directly reachable from the browser.
- Lets the frontend team own and evolve its own backend contract, decoupled from how internal services are structured.
- Avoids multiple round trips from the client by doing aggregation server-side, closer to the data.

## Cons
- It's another service to build, deploy, and maintain — a real ongoing cost, not a free architectural win.
- Can become a bottleneck or single point of failure if not scaled/designed carefully, since every request now passes through it.
- Risks duplicating logic across multiple BFFs (one per client type) if shared logic isn't factored out carefully.

## Interview questions
1. What problem does a BFF solve that a single shared API serving all clients doesn't?
2. How does introducing a BFF change the client's security exposure compared to calling internal services directly?
3. What's the maintenance cost of having a separate BFF per client type (web, iOS, Android), and how would you avoid duplicating logic across them?
4. How does a BFF relate to framework features like Next.js API routes or Remix loaders — are they the same thing?
5. When would you *not* want a BFF, even with multiple downstream services involved?
