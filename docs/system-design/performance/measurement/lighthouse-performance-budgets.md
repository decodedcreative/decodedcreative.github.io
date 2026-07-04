# Lighthouse & Performance Budgets

## What it is
Lighthouse is an automated auditing tool (built into Chrome DevTools, also runnable via CLI/CI) that scores a page on performance, accessibility, SEO, and best practices, producing actionable diagnostics. A performance budget is a set of agreed-upon limits (e.g., max bundle size, max LCP time) that a team treats as a hard constraint, often enforced automatically in CI.

## Why it's useful
- Lighthouse gives a repeatable, automated way to catch performance regressions before they reach users, rather than relying on manual spot-checks.
- Performance budgets turn "we should keep the site fast" into a concrete, enforceable number that CI can gate on.
- Combining the two lets teams catch regressions (e.g., a new dependency blowing up bundle size) at PR time instead of after deployment.

## Classic use-cases
- Running Lighthouse in CI on every PR to catch performance regressions automatically.
- Setting a bundle-size budget so a new dependency can't be merged if it pushes the app over a defined limit.
- Using Lighthouse's lab-based diagnostics to prioritize which specific fix (image size, unused JS, render-blocking resources) will move the needle most.

## Pros
- Automatable and repeatable — removes reliance on someone remembering to manually check performance.
- Concrete budgets give engineers and product a shared, non-negotiable constraint to design within.
- Lighthouse's diagnostics are specific and actionable (e.g., "eliminate render-blocking resources"), not just a single opaque score.

## Cons
- Lab-based scores (Lighthouse) don't always match real-user field data — a page can score well in Lighthouse but perform poorly for actual users on slow networks/devices.
- Budgets that are too strict can block legitimate feature work; too loose and they don't catch real regressions.
- Scores can vary run-to-run due to machine/network variance, requiring care (e.g., averaging runs) to get reliable CI signals.

## Interview questions
1. What's the difference between Lighthouse's lab data and real-user field data, and why can they disagree?
2. How would you set up a performance budget that's strict enough to catch regressions but not so strict it blocks normal feature work?
3. What causes Lighthouse scores to vary between runs, and how would you get reliable signal from it in CI?
4. Give an example of a Lighthouse diagnostic and the concrete fix it points to.
5. How would you enforce a JS bundle-size budget automatically in a CI pipeline?
