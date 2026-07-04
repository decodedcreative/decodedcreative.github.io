# TanStack Form

## What it is
A headless, framework-agnostic form-state management library (part of the TanStack family) built with first-class TypeScript type inference for field values, validation, and form state — usable across React, Vue, Solid, and other frameworks.

## Why it's useful
- Strong end-to-end type inference: field names, values, and validation results are statically checked against the form's shape.
- Headless design means it has no bundled UI, giving full control over markup and styling while the library manages state/validation logic.
- Shares design philosophy and ecosystem with TanStack Query/Router, appealing to teams already standardized on TanStack tools.

## Classic use-cases
- TypeScript-first codebases that want compile-time safety across form field names and validation logic.
- Multi-framework organizations that want one form library whose core concepts transfer between React, Vue, and Solid projects.
- Teams already using other TanStack libraries who want a consistent API style and type-inference approach for forms.

## Pros
- Strong, granular TypeScript inference reduces a class of bugs (typo'd field names, mismatched validation schemas).
- Headless/unstyled by design, giving complete UI flexibility.
- Framework-agnostic core, useful for teams working across multiple frontend frameworks.
- Fine-grained subscriptions to avoid unnecessary re-renders, similar in spirit to React Hook Form.

## Cons
- Newer library with a smaller community, fewer tutorials, and less battle-testing than React Hook Form.
- Being headless means more manual wiring compared to more batteries-included form libraries.
- Fewer third-party UI-library integrations/examples currently exist compared to the React Hook Form ecosystem.
- Adopting it mainly for the type-safety benefit requires the surrounding codebase to also be strongly typed to pay off.

## Interview questions
1. What does "headless" mean for a form library, and what tradeoffs does that design choice bring?
2. How does TanStack Form's type inference help prevent bugs that a less-typed form library wouldn't catch?
3. Compare TanStack Form to React Hook Form — what's the core difference in philosophy?
4. Why would a team building on multiple frameworks (React, Vue, Solid) prefer a framework-agnostic form library?
5. How would you structure field-level vs. form-level validation in a headless form library?
