# SameSite Cookies

## What it is
A cookie attribute (`SameSite=Strict`, `Lax`, or `None`) that controls whether a cookie is sent along with cross-site requests. It's the primary modern browser-level defense against CSRF: `Lax` (the current browser default) blocks cookies on cross-site requests except top-level navigations, `Strict` blocks them entirely for cross-site requests, and `None` (requiring `Secure`) sends cookies everywhere, opting back out of this protection.

## Why it's useful
- Blocks the core mechanism CSRF relies on — a malicious site making an authenticated request using the victim's cookies — without requiring any application-level token logic.
- `Lax` as a browser default means a large share of CSRF risk is mitigated automatically, even for apps that haven't implemented explicit CSRF tokens.
- Simple to reason about and set correctly compared to building a custom token-based CSRF defense from scratch.

## Classic use-cases
- Session cookies for a web app set to `SameSite=Lax` or `Strict` by default.
- `SameSite=None; Secure` specifically for legitimate cross-site cookie use cases (e.g., third-party embedded widgets, cross-domain SSO), consciously opting back into the risk.
- High-value actions (changing account settings, payments) using `Strict` for extra protection beyond the default `Lax`.

## Cons
- `SameSite` doesn't protect against attacks originating from a malicious subdomain of your own site, or GET-based state changes that `Lax` still allows through top-level navigation.
- `SameSite=None` (needed for legitimate cross-site cookie scenarios) requires `Secure` and re-opens the exact risk `SameSite` was closing.
- Doesn't replace the need for CSRF tokens on the highest-value actions, since it's a browser-side mitigation with some documented edge cases and legacy browser gaps.

## Interview questions
1. What's the difference in behavior between `SameSite=Strict`, `Lax`, and `None`?
2. Why does the browser default of `Lax` still allow some CSRF-style attacks through, specifically around top-level navigations?
3. When would a legitimate use case require `SameSite=None`, and what risk does that reintroduce?
4. Does `SameSite=Strict` fully replace the need for CSRF tokens? Why or why not?
5. How would you decide which cookies in an app need `Strict` vs. `Lax`?
