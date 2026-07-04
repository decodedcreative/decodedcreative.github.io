# Apollo + graphql-ws

## What it is
The combination of Apollo Client (or Apollo Server) with `graphql-ws`, the modern WebSocket transport implementation for GraphQL subscriptions. It lets a GraphQL API push real-time updates to subscribed clients over a WebSocket connection, integrated with Apollo's normalized cache on the client.

## Why it's useful
- Adds real-time subscription support to an existing GraphQL/Apollo setup without switching to a different real-time transport.
- `graphql-ws` is the actively maintained, spec-aligned protocol for GraphQL over WebSockets (superseding the older `subscriptions-transport-ws`).
- Subscription data flows into the same normalized Apollo cache as queries/mutations, so the UI stays consistent across all three operation types.

## Classic use-cases
- Adding live updates (new comments, live scores, presence indicators) to an app already built on GraphQL and Apollo Client.
- Real-time collaborative features where subscription payloads need to update cached entities also used by regular queries.
- Notification systems where a GraphQL subscription pushes events to specific connected clients.

## Pros
- Reuses existing GraphQL schema/types for real-time events — no separate real-time API to design.
- Cache integration means a subscription update can automatically refresh every component displaying that entity.
- `graphql-ws` is the modern, actively maintained standard, avoiding the deprecated legacy protocol.

## Cons
- Only useful if the app already is (or is willing to become) GraphQL-based — not a fit for a REST-first backend.
- Requires running a WebSocket-capable server for subscriptions, in addition to the standard GraphQL query/mutation endpoint.
- Subscription-specific resolvers, pub/sub infrastructure (e.g., Redis pub/sub for multi-instance servers), and cache-update logic add real complexity.
- Migrating from the older `subscriptions-transport-ws` protocol to `graphql-ws` requires coordinated client/server updates.

## Interview questions
1. How do GraphQL subscriptions work end-to-end with `graphql-ws`, from client subscription to server push?
2. Why did the GraphQL ecosystem move from `subscriptions-transport-ws` to `graphql-ws`?
3. How does a subscription's incoming data get merged into Apollo Client's normalized cache?
4. How would you scale GraphQL subscriptions across multiple server instances (e.g., using a pub/sub backend)?
5. When would you choose GraphQL subscriptions over plain WebSockets or SSE for real-time features?
6. What are common failure modes for long-lived subscription connections, and how do you handle reconnection/resubscription?
