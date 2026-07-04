# Content Security Policy (CSP)

## What it is
An HTTP response header (`Content-Security-Policy`) that tells the browser which sources of scripts, styles, images, and other resources are allowed to load and execute on a page. It's a browser-enforced allowlist that acts as defense-in-depth against XSS — even if malicious script gets injected into the page, CSP can stop it from executing if it violates the policy.

## Why it's useful
- Provides a second line of defense against XSS: even if sanitization/escaping fails somewhere, a strict CSP can still block the injected script from running.
- Forces explicit, auditable decisions about what's allowed to run on your site — inline scripts, `eval`, third-party origins — rather than an implicit "anything goes."
- `Content-Security-Policy-Report-Only` mode lets you test a policy in production (collecting violation reports) before actually enforcing it, reducing rollout risk.

## Classic use-cases
- Locking down `script-src` to `'self'` plus specific trusted third-party origins (analytics, payment providers).
- Using a per-request `nonce` to allow specific inline scripts while blocking all other inline script execution.
- Rolling out a new/stricter policy in report-only mode first to catch what it would have broken, before enforcing it.

## Pros
- Meaningfully reduces the real-world impact of an XSS bug, even one that bypasses your primary defenses.
- Report-only mode gives a safe rollout path with real production data before enforcement.
- Forces a clear, reviewable inventory of what's allowed to execute on your site.

## Cons
- Retrofitting CSP onto an existing app with lots of inline scripts/styles and various third-party embeds can be a significant migration effort.
- Overly strict policies can break legitimate third-party embeds (maps, video players) that weren't accounted for.
- `unsafe-inline`/`unsafe-eval` are common escape hatches that undermine CSP's protection if teams reach for them to avoid the migration work.

## Interview questions
1. How does CSP act as defense-in-depth against XSS, even after other defenses have already failed?
2. What's the difference between `Content-Security-Policy` and `Content-Security-Policy-Report-Only`, and how would you use them together during rollout?
3. How does a nonce-based CSP allow specific inline scripts while blocking all others?
4. Why do `unsafe-inline` and `unsafe-eval` undermine the protection CSP is meant to provide?
5. What's a realistic migration path for adding a strict CSP to an app that currently has none?
