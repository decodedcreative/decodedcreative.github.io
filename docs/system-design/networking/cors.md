# CORS (Cross-Origin Resource Sharing)

## What it is
A browser-enforced mechanism that controls whether a web page running on one origin can make requests to a server on a different origin, and what the response is allowed to expose back to the calling page. For "non-simple" requests (custom headers, non-standard methods, certain content types), the browser first sends an automatic **preflight** `OPTIONS` request to check whether the actual request would be allowed, before sending it.

## Why it's useful
- Protects users from a malicious site silently making authenticated cross-origin requests to another site on their behalf and reading the response — CORS is what stops that response from being readable by the malicious page.
- Preflight requests let the server explicitly declare what it permits (origins, methods, headers) before the real request is sent, rather than discovering incompatibility after the fact.
- Understanding CORS clearly separates two related but distinct concerns: what a request can *do* (partially governed by CSRF defenses) vs. what the response can be *read* by the calling page (governed by CORS).

## Classic use-cases
- A frontend hosted on one domain calling an API hosted on a different domain/subdomain.
- Third-party widgets or SDKs making requests back to their own origin from embedding on other sites.
- Public APIs deciding which origins are allowed to consume them directly from the browser.

## Pros
- Gives servers explicit, granular control over which origins/methods/headers are allowed, rather than an all-or-nothing model.
- Preflight checks catch disallowed requests before they're sent, avoiding partial side effects from a request that would've been rejected anyway.
- Well-understood browser standard — every browser enforces it consistently.

## Cons
- `Access-Control-Allow-Origin: *` combined with credentialed requests (cookies) is explicitly forbidden by the spec — a common source of confusing errors when teams try to allow "any origin" for an authenticated endpoint.
- Preflight requests add an extra round trip for non-simple requests, which is a real (if usually small) latency cost.
- CORS misconfiguration is a common source of both broken legitimate integrations and, if too permissive, real security exposure.

## Interview questions
1. What's the difference between what CORS prevents and what CSRF protections prevent?
2. When does a browser send a preflight `OPTIONS` request, and what determines whether one is needed?
3. Why is `Access-Control-Allow-Origin: *` forbidden alongside credentialed (cookie-carrying) requests?
4. How would you configure CORS for an API that needs to support multiple specific frontend origins?
5. What's a real debugging scenario where a request fails due to CORS, and how would you diagnose it from the browser's network tab?
