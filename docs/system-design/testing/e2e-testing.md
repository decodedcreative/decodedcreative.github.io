# E2E Testing

## What it is
Testing the full application running in a real (or real-like) browser, driving it through actual user flows — clicking, typing, navigating — against a real or near-real backend. Modern tooling like Playwright or Cypress automates a real browser engine rather than a simulated DOM.

## Why it's useful
- Highest-confidence tests available — they exercise the real browser, real network stack, and (often) a real or staging backend, catching issues no lower-level test can.
- Validates critical user journeys end-to-end (signup, checkout, core workflows) exactly as a real user would experience them.
- Catches cross-cutting issues that only appear in a fully integrated system: routing, auth, third-party scripts, real CSS/layout.

## Classic use-cases
- Smoke-testing critical revenue paths (checkout, signup, login) before every deploy.
- Cross-browser compatibility checks for key flows.
- Regression testing complex multi-step workflows (wizards, multi-page forms) that are hard to fully validate with integration tests alone.

## Pros
- Highest fidelity to real user experience — tests the whole stack as deployed.
- Catches issues unreachable by unit/integration tests: real navigation, real third-party scripts, real timing.
- Modern tools (Playwright) offer strong debugging (trace viewers, video recording) when a test fails.

## Cons
- Slow and comparatively expensive to run — not something you'd run on every keystroke, usually reserved for CI/pre-deploy gates.
- More prone to flakiness (network timing, animations, third-party dependencies) than lower-level tests.
- Expensive to write and maintain in volume — E2E suites are best kept to critical paths, not exhaustive coverage.

## Interview questions
1. Why do E2E tests give the highest confidence but shouldn't be your primary test coverage strategy?
2. What causes E2E test flakiness, and how do you mitigate it (retries, explicit waits, trace debugging)?
3. How would you decide which user flows deserve E2E coverage vs. being covered at the integration/unit level (the "testing pyramid")?
4. How do E2E tests handle authentication/session setup without re-doing a full login flow in every test?
5. How would you structure E2E tests to run reliably in CI against a staging environment?
