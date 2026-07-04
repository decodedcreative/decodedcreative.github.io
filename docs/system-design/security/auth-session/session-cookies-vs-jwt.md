# Session Cookies Vs JWT

## What it is
Two different models for tracking that a user is logged in across requests. Session cookies store a random session ID in an `HttpOnly` cookie, with the actual session data kept server-side (in a database or cache) — the server looks up who the user is on each request. JWTs (JSON Web Tokens) instead encode the user's identity/claims directly in a signed token that the client holds and sends with each request, requiring no server-side lookup to validate.

## Why it's useful
- Session cookies with `HttpOnly` are inaccessible to JavaScript, meaningfully reducing the impact of an XSS vulnerability on session theft.
- JWTs avoid a server-side session store lookup on every request, which can simplify horizontal scaling for stateless APIs.
- Understanding both lets you choose the right tradeoff: cookies for security-sensitive session state, JWTs for stateless, scalable API authorization.

## Classic use-cases
- Traditional web apps: `HttpOnly` session cookies for the primary login session.
- Stateless APIs/microservices: short-lived JWTs passed as Bearer tokens, avoiding a shared session store across services.
- Mixed approach: a session cookie for the browser session, with short-lived JWTs issued for specific API calls.

## Pros
- Session cookies: `HttpOnly` + `Secure` + `SameSite` meaningfully protects against both XSS token theft and CSRF (with `SameSite`).
- JWTs: stateless validation (no DB lookup), easy to scale horizontally, easy to pass between services.
- Choosing correctly for your architecture avoids both unnecessary server load (session store lookups at huge scale) and unnecessary security exposure (JWTs stored insecurely).

## Cons
- JWTs stored in `localStorage` are readable by any injected script — a single XSS vulnerability means full session compromise, which is why this pattern is broadly discouraged.
- JWTs can't be easily revoked before they expire (no server-side lookup to invalidate) without extra infrastructure (a revocation/deny list).
- Session cookies require server-side session storage, adding infrastructure (shared cache/DB) that a purely stateless JWT approach avoids.

## Interview questions
1. Why is storing a JWT in `localStorage` for authentication considered risky, and where should it live instead?
2. How would you revoke a JWT before its expiry, given it's normally validated statelessly?
3. What does `HttpOnly` actually protect against, and what does it not protect against?
4. When would you choose session cookies over JWTs for a given system, and vice versa?
5. How do `Secure` and `SameSite` cookie attributes complement `HttpOnly` in securing a session cookie?
