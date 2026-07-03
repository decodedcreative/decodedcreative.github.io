# Cookies

## What it is
A small piece of data (typically up to ~4KB) stored by the browser and automatically attached to every HTTP request to the domain that set it (subject to path/domain/`SameSite` rules). Cookies can be set by the server (via `Set-Cookie` response headers) or by client-side JavaScript, and can have an explicit expiration date or be session-only.

## Why it's useful
- The only client storage mechanism that's automatically sent with every matching HTTP request, making it the natural fit for server-side session/auth state.
- Supports fine-grained security flags (`HttpOnly`, `Secure`, `SameSite`) that other storage types lack.
- Can be scoped to a domain/path and given an explicit expiration, unlike local/session storage.

## Classic use-cases
- Session/auth tokens for logged-in users (often paired with `HttpOnly` to block JS access).
- CSRF tokens.
- Tracking/analytics identifiers and consent flags.
- Server-driven feature flags or A/B bucket assignment that the backend needs to read on every request.

## Pros
- Automatically included in requests, so the server can read state without any client-side plumbing.
- `HttpOnly` flag prevents JavaScript access, mitigating XSS-based token theft.
- `Secure` and `SameSite` flags give control over transport security and cross-site request behavior (CSRF mitigation).
- Supports expiration dates for automatic cleanup.

## Cons
- Very small size limit (~4KB) compared to Web Storage APIs.
- Sent with every matching request, adding overhead to request headers — especially costly if overused.
- Without `HttpOnly`, still readable/writable by JavaScript and vulnerable to XSS.
- `SameSite`/CORS/domain rules are easy to misconfigure, leading to CSRF or cookies silently not being sent.
- Increasingly restricted by browsers for third-party/cross-site use (privacy sandboxing, cookie blocking).

## Interview questions
1. How do `HttpOnly`, `Secure`, and `SameSite` cookie flags each mitigate a specific attack?
2. Why would you choose an `HttpOnly` cookie over local storage for an auth token?
3. Walk through how a CSRF attack works and how `SameSite` cookies help prevent it.
4. What's the difference between a session cookie and a persistent cookie?
5. How do first-party vs. third-party cookies differ, and why are browsers restricting third-party cookies?
6. What happens to a cookie's size/count limits, and what problems arise if you exceed them?
7. How would you design a secure session mechanism using cookies (token storage, rotation, expiration)?
