# Cross-Site Scripting (XSS)

## What it is
A vulnerability where an attacker gets their own JavaScript to execute in the context of your site, usually by injecting it into content that later gets rendered as HTML/JS rather than plain text. The three classic types: **stored** (malicious input saved server-side and served to other users, e.g., a comment field), **reflected** (malicious input echoed back immediately, often via a crafted URL), and **DOM-based** (the vulnerability lives entirely in client-side code, e.g., unsafely reading `location.hash` into the DOM).

## Why it's useful
- Understanding XSS is foundational to nearly every other front-end security topic — CSP, sanitization, and cookie flags (`HttpOnly`) all exist specifically to blunt XSS's impact.
- React auto-escapes values rendered in JSX by default, which prevents the most common injection vector — but `dangerouslySetInnerHTML` is an explicit opt-out that removes that protection, making it the natural audit point in a React codebase.
- Once you understand the three types, you can reason about where injected script could actually execute in a given system, rather than treating "XSS" as one vague catch-all threat.

## Classic use-cases (as an attack, and where defenses apply)
- A comment/review field that isn't sanitized before being rendered to other users (stored XSS).
- A search page that echoes the query string back into the page without escaping (reflected XSS).
- Client-side code reading `location.hash` or `postMessage` data and inserting it into the DOM unsafely (DOM-based XSS).

## Pros (of understanding/defending against it)
- Framework auto-escaping (React's JSX) removes the most common injection vector by default.
- A small, auditable set of "escape hatches" (`dangerouslySetInnerHTML`, direct DOM manipulation) gives you a clear list of what to review.
- Defense in depth (escaping + CSP + `HttpOnly` cookies) means a single missed sanitization bug doesn't automatically mean full account compromise.

## Cons (why it remains a persistent risk)
- Any place user-generated content is rendered as HTML (markdown-to-HTML pipelines, rich text editors) is a recurring source of risk that needs ongoing vigilance, not a one-time fix.
- Third-party scripts and embeds run with the same privileges as your own code, and are a common vector outside your direct control.
- DOM-based XSS can be easy to miss in code review since the "sink" (unsafe DOM write) and vulnerable "source" (user-controlled input) are often in different files.

## Interview questions
1. What's the difference between stored, reflected, and DOM-based XSS?
2. Why does React's JSX auto-escaping prevent most XSS, and what specifically bypasses that protection?
3. How would you safely render user-generated rich text (e.g., from a markdown editor) without introducing an XSS vulnerability?
4. What's a real example of a DOM-based XSS vector (e.g., involving `location.hash` or `postMessage`)?
5. How do CSP and `HttpOnly` cookies act as defense-in-depth even if an XSS bug slips through sanitization?
