# React Hook Form

## What it is
A form-state library for React that manages form values, validation, and submission state using uncontrolled inputs and refs by default, minimizing re-renders compared to controlled-input approaches.

## Why it's useful
- Uses uncontrolled inputs internally, so keystrokes don't trigger a re-render of the whole form on every character typed.
- Provides a simple `register`/`handleSubmit` API that integrates with native form elements with minimal wiring.
- Integrates with schema validation libraries (Zod, Yup) for declarative validation rules.

## Classic use-cases
- Large forms with many fields where performance (avoiding re-renders per keystroke) matters.
- Forms needing schema-based validation shared between client and server (e.g., a Zod schema used in both places).
- Multi-step forms/wizards where field-level state and validation need to be tracked across steps.

## Pros
- Minimal re-renders by default thanks to its uncontrolled-input approach.
- Small bundle size relative to the functionality it provides.
- First-class integration with schema validators (Zod, Yup, Joi) via resolvers.
- Good support for complex scenarios: field arrays, conditional fields, nested objects.

## Cons
- The uncontrolled-input model is a different mental model from typical controlled-component React patterns, which can be confusing initially.
- Integrating with custom/complex UI component libraries sometimes requires extra wiring (`Controller` component) to bridge controlled components.
- Less useful for forms that need constant access to live field values for other UI logic (though `watch` exists for this, it can reintroduce re-renders).

## Interview questions
1. How does React Hook Form minimize re-renders compared to a fully controlled-components approach?
2. When would you need the `Controller` component, and what problem does it solve?
3. How would you integrate a Zod or Yup schema for validation with React Hook Form?
4. How do you handle dynamic field arrays (e.g., adding/removing list items) in a form?
5. What are the performance tradeoffs of using `watch` to reactively read form values?
6. Compare React Hook Form's uncontrolled approach to Formik's controlled approach — what problem was RHF solving?
