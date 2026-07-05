# Astro

## What it is
An HTML-first meta-framework built around "islands architecture": pages are static HTML by default, and JavaScript is only shipped for the specific interactive components ("islands") that explicitly opt into it — via directives like `client:load`, `client:visible`, or `client:idle` that control exactly when and how each island hydrates.

## Why it's useful
- Ships zero JavaScript by default — a page full of static content (the common case for blogs, marketing sites, docs) genuinely costs nothing on the client unless something explicitly opts in.
- Fine-grained hydration directives (`client:visible`, `client:idle`) let you defer an island's JS cost until it's actually needed, rather than paying for it upfront.
- Framework-agnostic islands — a single Astro page can mix React, Vue, and Svelte components as islands, since each only needs to hydrate itself independently.

## Classic use-cases
- Content-heavy sites (marketing, blogs, documentation) where most of the page is static and only a handful of widgets need interactivity (a search box, a carousel, a comment form).
- Migrating a site incrementally by mixing components from different frameworks as independent islands.
- Sites that want the absolute minimum JS payload without giving up isolated interactive functionality where it's genuinely needed.

## Pros
- The strongest "ship nothing unless needed" default among mainstream meta-frameworks — genuinely minimal JS for mostly-static content.
- Fine-grained control over exactly when each island hydrates, rather than an all-or-nothing hydration model.
- Framework-agnostic islands reduce lock-in to a single component framework.

## Cons
- Less suited to apps that are mostly interactive/stateful throughout — the islands model shines specifically for mostly-static content with pockets of interactivity, not full SPAs.
- Sharing state between separate islands isn't automatic the way it is within a single framework's component tree — cross-island communication needs deliberate design.
- Smaller ecosystem and different conventions than React-centric frameworks, which is a real adoption cost for teams already invested in one component framework.

## Interview questions
1. What is "islands architecture," and how does it differ from selective/partial hydration in a framework like Next.js?
2. What do hydration directives like `client:visible` and `client:idle` control, and why would you choose one over `client:load`?
3. How would you share state between two independent islands on the same page?
4. Why is Astro a strong fit for content-heavy sites but a poor fit for a highly interactive SPA?
5. What's the tradeoff of Astro's framework-agnostic islands model compared to committing to a single component framework throughout?
