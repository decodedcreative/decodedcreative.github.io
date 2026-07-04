# Sanitization (DOMPurify)

## What it is
The practice of stripping or neutralizing dangerous HTML/JS from user-generated or third-party content before rendering it, so it can be safely inserted into the DOM as real markup rather than escaped plain text. DOMPurify is the most widely used library for this — it parses HTML and removes anything that could execute script (event handlers, `<script>` tags, `javascript:` URLs) while preserving safe formatting markup.

## Why it's useful
- Necessary whenever you genuinely need to render user-generated content *as HTML* (rich text, markdown-to-HTML output) rather than plain escaped text — escaping alone isn't an option there.
- Purpose-built sanitization libraries handle the many non-obvious attack vectors (malformed HTML, obscure event handler attributes, mutation-based XSS) that a naive regex or blocklist would miss.
- Pairs directly with React's `dangerouslySetInnerHTML` — sanitizing before passing content to it closes the exact gap that prop opens.

## Classic use-cases
- Rendering user-submitted rich text (comments, descriptions) that supports basic formatting (bold, links, lists).
- Rendering markdown converted to HTML, where the markdown parser's output still needs sanitizing before insertion into the DOM.
- Sanitizing content pulled from third-party APIs/embeds before rendering it directly.

## Pros
- Handles a wide, actively-maintained set of known attack vectors that are easy to miss when hand-rolling sanitization.
- Configurable allowlists (which tags/attributes are permitted) let you tune strictness to what your content actually needs.
- Directly closes the risk introduced by `dangerouslySetInnerHTML` and similar direct-HTML-insertion APIs.

## Cons
- Sanitization happens at render time (or before storage) and must be applied consistently everywhere the content is rendered — missing one spot reintroduces the vulnerability.
- Overly permissive allowlists (allowing `style` attributes, certain tags) can reopen attack surface if not configured carefully.
- Adds a dependency and processing step; skipping it "just this once" for convenience is a common source of real vulnerabilities.

## Interview questions
1. Why isn't simple HTML escaping sufficient when you actually need to render user content as real HTML (e.g., rich text)?
2. What specific gap does DOMPurify close when used alongside `dangerouslySetInnerHTML`?
3. What are the risks of using an overly permissive sanitization allowlist?
4. Where in a rendering pipeline (server-side, client-side, both) should sanitization happen, and why does that matter?
5. How would you audit an existing codebase for places where sanitization might be missing?
