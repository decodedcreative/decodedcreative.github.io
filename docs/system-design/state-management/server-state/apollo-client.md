# Apollo Client

## What it is
A comprehensive state-management library for GraphQL that fetches, caches, and updates data from a GraphQL API. It maintains a normalized in-memory cache keyed by object identity, so data fetched by one query can automatically satisfy another query that needs the same objects.

## Why it's useful
- Normalizes GraphQL responses into a single cache, avoiding duplicate copies of the same entity across the app.
- Automatically updates the UI everywhere an entity is displayed when that entity changes via a mutation or another query.
- Provides hooks (`useQuery`, `useMutation`, `useSubscription`) that integrate tightly with GraphQL's type system.

## Classic use-cases
- Apps built on a GraphQL API (as opposed to REST) that want automatic caching and normalization.
- Products where the same entity (e.g., a "user" or "product") appears in many different queries/screens and must stay in sync.
- Real-time features via GraphQL subscriptions layered on top of standard queries/mutations.

## Pros
- Normalized cache means updating one entity updates it everywhere it's rendered, with no manual cache-busting.
- Deep GraphQL integration: fragments, pagination helpers, and subscription support are first-class.
- Mature devtools for inspecting the cache and query activity.
- Handles optimistic UI updates and cache writes declaratively.

## Cons
- Only makes sense if the backend is GraphQL — not usable for a plain REST API without a translation layer.
- Cache normalization rules (`typePolicies`, key fields) can be tricky to get right for complex schemas.
- Heavier bundle size and steeper learning curve than simpler query libraries.
- Manual cache updates for mutations that don't map cleanly to existing queries can get complex.

## Interview questions
1. How does Apollo Client's normalized cache work, and what determines an object's cache key?
2. How do you keep the UI in sync after a mutation that doesn't naturally match an existing query shape?
3. Compare Apollo Client's caching model to TanStack Query's — what does normalization buy you?
4. How do GraphQL subscriptions integrate with Apollo Client's cache?
5. What are `typePolicies`, and when would you need to customize them?
6. How would you implement pagination (cursor-based) with Apollo Client's cache merge functions?
