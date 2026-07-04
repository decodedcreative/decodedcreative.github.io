# Refresh Token Rotation

## What it is
A pattern where a short-lived access token (minutes) is paired with a longer-lived refresh token (days/weeks) used to silently obtain new access tokens without forcing the user to log in again. "Rotation" means each time the refresh token is used, it's invalidated and replaced with a new one — if an old, already-used refresh token is ever presented again, it signals theft and the whole token family is revoked.

## Why it's useful
- Keeps access tokens short-lived (limiting the damage window if one leaks) while still giving users a persistent, non-annoying login session.
- Rotation specifically detects token theft: a stolen refresh token being reused by an attacker after the legitimate user already rotated it is a clear signal to revoke everything.
- Avoids the tradeoff of either "log in constantly" (short-lived tokens only) or "one long-lived token that's catastrophic if leaked" (no rotation).

## Classic use-cases
- Any app wanting "stay logged in" behavior without keeping a single long-lived, high-risk token around.
- Mobile and SPA clients where silent token renewal in the background keeps the user session alive without visible re-authentication.
- Systems needing to detect and respond to token theft rather than just hoping it doesn't happen.

## Pros
- Short-lived access tokens sharply limit the blast radius of a leaked token.
- Rotation provides a built-in theft-detection mechanism, not just a longer-lived credential.
- Balances security with user experience — no need for constant re-login.

## Cons
- Adds real implementation complexity: tracking token families, detecting reuse, handling race conditions across multiple tabs/requests refreshing simultaneously.
- Concurrent requests from multiple tabs can trigger false-positive theft detection if not handled carefully (a benign race condition looking like reuse).
- Requires server-side state to track issued/used refresh tokens, unlike a purely stateless JWT-only approach.

## Interview questions
1. How does refresh token rotation detect that a token has been stolen, specifically?
2. What race condition can occur with multiple browser tabs refreshing tokens simultaneously, and how would you handle it without false-positive lockouts?
3. What's the tradeoff between access token lifetime and how often the client needs to refresh?
4. What should happen when theft is detected — what's the correct response for the whole "token family"?
5. How would you implement silent token renewal in a single-page app without disrupting the user's session?
