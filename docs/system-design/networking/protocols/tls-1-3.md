# TLS 1.3

## What it is
The current version of Transport Layer Security, the protocol that encrypts HTTP traffic (making it HTTPS). TLS 1.3's main improvements over 1.2 are a simplified, faster handshake (one round trip instead of two, with **0-RTT** resumption for repeat connections) and dropping legacy, insecure cryptographic algorithms that older versions still permitted.

## Why it's useful
- A faster handshake directly reduces connection setup latency, which matters on every single new HTTPS connection a browser makes.
- 0-RTT resumption lets a returning client send encrypted application data on its very first packet to a server it's connected to before, skipping a full round trip.
- Removing legacy weak ciphers/algorithms by default closes off entire categories of downgrade attacks that were possible against older TLS versions.

## Classic use-cases
- Every modern HTTPS connection — this isn't an opt-in feature for specific use cases, it's the baseline expectation for secure web traffic today.
- Mobile and high-latency connections, where shaving a round trip off the handshake has an outsized relative impact on perceived load time.
- Any system wanting to eliminate legacy, vulnerable cipher suites as an attack surface entirely, rather than just discouraging their use.

## Pros
- Meaningfully faster handshake, directly improving connection setup latency for every new HTTPS connection.
- 0-RTT resumption further speeds up repeat connections to a known server.
- Simplified, more secure default cipher suite selection reduces the risk of protocol-downgrade attacks.

## Cons
- 0-RTT data is technically replayable by an attacker who intercepts it (since there's no server round-trip to guarantee freshness before that data is processed), so it's not appropriate for non-idempotent requests.
- Some older clients, servers, or corporate middleboxes don't yet fully support TLS 1.3, occasionally requiring fallback handling.
- Migrating legacy infrastructure still pinned to older TLS versions/cipher suites can be nontrivial.

## Interview questions
1. What makes the TLS 1.3 handshake faster than TLS 1.2's?
2. What is 0-RTT resumption, and why is it risky to use for non-idempotent requests like a payment submission?
3. Why does removing legacy cipher suites by default improve security beyond just "encouraging" better choices?
4. What's a scenario where a server might still need to support TLS 1.2 alongside 1.3?
5. How does TLS interact with HTTP/3's QUIC-based connection setup?
