# Idempotency Keys

## What it is
A client-generated unique identifier attached to a state-changing request (typically a POST) so that if the same request is retried — due to a network failure, a timeout, or an automatic retry mechanism — the server can recognize it as a duplicate and return the original result instead of performing the action again.

## Why it's useful
- Makes retries safe for operations that aren't naturally idempotent (creating an order, charging a card), which is exactly the category of request that automatic retry-with-backoff logic would otherwise risk duplicating.
- Solves a genuinely ambiguous failure case: if a client sends a request and the connection drops before it sees the response, it has no way to know whether the server actually processed it — the idempotency key lets it safely retry to find out.
- Widely adopted, standard pattern (used by Stripe and similar payment APIs) rather than a bespoke solution needed for every system.

## Classic use-cases
- Payment/checkout submissions, where accidentally processing the same charge twice is a serious problem.
- Any "create" operation triggered by a client that might retry after a timeout or dropped connection (order creation, account signup).
- APIs exposed to clients with unreliable retry behavior (mobile clients on flaky networks) where duplicate submissions are a real, common risk.

## Pros
- Directly closes the "did my request actually go through" ambiguity that timeouts and dropped connections create.
- Makes retry-with-backoff safe to apply even to non-idempotent operations.
- Well-established pattern with clear precedent (Stripe, many payment/critical-action APIs) to follow rather than invent from scratch.

## Cons
- Requires the server to store and check keys for some retention window, adding infrastructure (even if just a cache with a TTL).
- The client must generate and consistently reuse the same key across retries of the *same* logical request — getting that wrong (e.g., generating a new key per retry) defeats the whole purpose.
- Doesn't help if the client itself doesn't know a request should be retried (e.g., silently swallowed errors) — it's a safety net for retries, not a guarantee of eventual delivery.

## Interview questions
1. What specific ambiguity does an idempotency key resolve that a plain retry doesn't?
2. How would you generate and store idempotency keys correctly across retries of the same logical request?
3. How long should a server retain an idempotency key, and what are the tradeoffs of that retention window?
4. Why are idempotency keys especially critical for payment/checkout flows specifically?
5. What happens if a client mistakenly generates a new idempotency key on every retry attempt?
