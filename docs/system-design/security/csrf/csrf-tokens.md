# CSRF Tokens

## What it is
An application-level defense against Cross-Site Request Forgery: the server generates a unique, unpredictable token tied to the user's session and requires it to be included with any state-changing request (form submission, API call). Since an attacker's malicious site can't read or guess that token, it can't forge a valid request even if it can trick the browser into sending the user's cookies.

## Why it's useful
- Provides explicit, application-controlled CSRF protection that doesn't rely solely on browser behavior (`SameSite`), covering edge cases and legacy scenarios `SameSite` alone might miss.
- Works alongside `SameSite` cookies as defense-in-depth — either one failing doesn't automatically mean a successful attack.
- Well-understood, standard patterns (synchronizer token, double-submit cookie) exist rather than needing to invent bespoke protection.

## Classic use-cases
- Traditional server-rendered forms embedding a hidden CSRF token field, validated on submission.
- APIs using the double-submit cookie pattern: the token is set as a cookie and also sent in a request header, and the server checks they match (a value an attacker's site can't read to replicate).
- High-value state-changing actions (payments, account changes) requiring a fresh CSRF token even in apps that otherwise rely mostly on `SameSite`.

## Pros
- Effective regardless of `SameSite` cookie configuration, adding a real layer of defense-in-depth.
- Well-established, standard patterns exist (synchronizer tokens, double-submit cookies) rather than needing custom design.
- Explicit and auditable — you can see exactly which endpoints require a valid token.

## Cons
- Adds implementation overhead: generating, delivering, and validating tokens for every state-changing request.
- Can complicate certain architectures (e.g., purely stateless APIs, some SPA/mobile client patterns) compared to relying on `SameSite` alone.
- Must be implemented consistently across every state-changing endpoint — a single missed endpoint reopens the vulnerability.

## Interview questions
1. Why can't a malicious site simply read and replay a valid CSRF token, even though it can trigger a request using the victim's cookies?
2. What's the difference between the synchronizer token pattern and the double-submit cookie pattern?
3. Why would you use CSRF tokens in addition to `SameSite` cookies rather than relying on just one?
4. How would you implement CSRF protection for a stateless API that doesn't maintain server-side sessions?
5. What's a common mistake that reopens CSRF vulnerability even with tokens implemented (e.g., accepting the token from a GET request, or not validating it on all endpoints)?
