# Integration Testing

## What it is
Testing how multiple units work together — a component tree, its state management, and its interaction with (usually mocked) network requests — closer to how a real user would exercise the system. In the React ecosystem this is typically done with React Testing Library on top of Jest/Vitest, querying the DOM the way a user would rather than testing implementation details.

## Why it's useful
- Catches bugs that unit tests miss — the seams between components, hooks, and state are exactly where integration issues hide.
- Testing Library's philosophy (query by role/text, not implementation detail) makes tests resilient to refactors that don't change behavior.
- Higher confidence per test than a unit test, since it exercises real wiring rather than a single isolated function.

## Classic use-cases
- A form component: filling in fields, submitting, and asserting the right validation errors or success state appear.
- A component that fetches data and renders different states (loading, error, success) with the network layer mocked (e.g., via MSW).
- Testing a feature end-to-end within the frontend only — user interaction through to UI state update, without a real backend or browser.

## Pros
- Better bug-catching power per test than unit tests, since it exercises real component wiring.
- Encourages testing user-observable behavior rather than internals, which survives refactors.
- Sits at a good cost/confidence tradeoff between fast-but-narrow unit tests and slow-but-broad E2E tests.

## Cons
- Slower and more complex to set up than unit tests (rendering trees, mocking network layers).
- Can still miss real backend/browser-environment issues since it typically runs in a simulated DOM (jsdom), not a real browser.
- Flakiness can creep in around async state updates and timing if not handled carefully (`waitFor`, `findBy` queries).

## Interview questions
1. What's the core philosophy behind React Testing Library's "query by what the user sees" approach, and why does it matter?
2. How do you handle mocking network requests in an integration test (e.g., with MSW)?
3. What's the tradeoff between integration tests and E2E tests in terms of speed, confidence, and maintenance cost?
4. How would you test a component with async data fetching without introducing flakiness?
5. What's an example of a bug that a unit test would miss but an integration test would catch?
