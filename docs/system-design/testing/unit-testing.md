# Unit Testing

## What it is
Testing individual functions, hooks, or components in isolation from the rest of the system, with dependencies mocked or stubbed out. In the React ecosystem this is typically done with Jest or Vitest as the test runner/assertion library.

## Why it's useful
- Fast feedback loop — unit tests run in milliseconds to seconds, so they can run constantly during development and in CI on every commit.
- Isolates failures to a specific unit, making it immediately clear what broke and why.
- Encourages testable, decoupled code, since hard-to-unit-test code is often a signal of tangled dependencies.

## Classic use-cases
- Pure functions (formatters, validators, calculations) with well-defined inputs/outputs.
- Custom hooks tested in isolation (e.g., with `renderHook`).
- Reducer/state-transition logic (`useReducer`, Redux reducers) where inputs and outputs are easy to assert against.

## Pros
- Extremely fast to run, enabling tight feedback loops and large test suites without slowing down CI.
- Pinpoints exactly which unit broke, unlike broader integration/E2E failures.
- Cheap to write and maintain for well-isolated logic.

## Cons
- Doesn't catch integration bugs — units can each pass in isolation while the system breaks when wired together.
- Over-mocking can make tests pass even when the real implementation is broken, giving false confidence.
- Excessive unit testing of trivial code (simple getters, pass-through components) adds maintenance cost without much value.

## Interview questions
1. What makes a function or component easy vs. hard to unit test, and what does that usually indicate about its design?
2. How do you decide what to mock vs. what to test with real implementations?
3. What's the risk of over-mocking, and how can it hide real bugs?
4. How would you unit test a custom React hook that has internal state?
5. Where's the line between a unit test and an integration test, and why does that distinction matter for test strategy?
