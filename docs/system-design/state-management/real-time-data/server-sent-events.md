# Server-Sent Events (SSE)

## What it is
A one-way, server-to-client streaming protocol built on top of plain HTTP. The client opens a long-lived connection (via `EventSource` in the browser) and the server keeps it open, pushing text-based events to the client as they occur, without the client needing to poll or re-request.

## Why it's useful
- Much simpler than WebSockets when the client only needs to receive updates, not send them back over the same channel.
- Runs over standard HTTP, so it works through existing infrastructure (proxies, load balancers) without special protocol upgrades.
- Browsers handle automatic reconnection for `EventSource` natively, reducing client-side complexity.

## Classic use-cases
- Live notification feeds, activity streams, or progress updates (e.g., streaming an LLM response token by token).
- Stock ticker-style updates or dashboards where only the server pushes new data.
- Any one-directional "server tells client" real-time feature that doesn't need the client to talk back over the same connection.

## Pros
- Simpler than WebSockets — plain HTTP, text-based protocol, no special server infra required.
- Built-in automatic reconnection and event-ID tracking (`Last-Event-ID`) in the browser's `EventSource` API.
- Works well with existing HTTP tooling (caching proxies, load balancers) since it's not a protocol upgrade.

## Cons
- One-way only — the client can't send data back over the same connection (a separate HTTP request is needed for that).
- Limited to text data (no binary), unlike WebSockets.
- Older browsers and some HTTP/1.1 proxies limit the number of concurrent connections per domain, which can be an issue with many open SSE streams.
- Not suited for high-frequency bidirectional interaction — WebSockets are the better fit there.

## Interview questions
1. How does SSE differ from WebSockets in terms of directionality and protocol complexity?
2. How does the `EventSource` API handle automatic reconnection, and what is `Last-Event-ID` used for?
3. When would you choose SSE over WebSockets for a real-time feature?
4. What are the limitations of SSE around binary data and concurrent connection limits?
5. How would you use SSE to stream incremental output from a long-running server process (e.g., an LLM response)?
6. How do proxies and load balancers need to be configured to support long-lived SSE connections?
