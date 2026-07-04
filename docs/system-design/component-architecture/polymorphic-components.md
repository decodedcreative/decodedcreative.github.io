# Polymorphic Components

## What it is
A component that can render as a different underlying HTML element or component while keeping the same styling/behavior, typically via an `as` prop (e.g., `<Text as="h1">`, `<Button as="a" href="...">`). The component's visual/behavioral API stays consistent regardless of what it ultimately renders to the DOM as.

## Why it's useful
- Avoids duplicating a component's styling/behavior across near-identical variants that only differ by the underlying HTML tag (e.g., a `Button` that's sometimes a `<button>` and sometimes an `<a>`).
- Preserves correct semantic HTML and accessibility (a link should be an `<a>`, a button should be a `<button>`) without forcing consumers into the wrong element for styling convenience.
- Lets a design system's typography/layout primitives (`Text`, `Box`, `Stack`) stay flexible about their rendered tag while keeping consistent props/styling.

## Classic use-cases
- A `Button` component that renders as `<a>` when given an `href`, keeping identical visual styling whether it's a real button or a link.
- Typography components (`Heading`, `Text`) that can render as `h1`–`h6` or `p`/`span` depending on context, without separate components for each.
- Layout primitives (`Box`, `Stack`) that need to render as different semantic elements (`div`, `section`, `nav`) depending on usage.

## Pros
- Prevents duplicating styling/behavior across nearly-identical components that differ only by tag.
- Preserves correct semantic HTML/accessibility rather than sacrificing it for convenience.
- Keeps a design system's component API small while still being flexible about output markup.

## Cons
- Typing polymorphic components correctly in TypeScript (so `as="a"` correctly requires an `href` prop, for example) is notably tricky and verbose.
- Overuse can make it unclear what a component actually renders to without checking usage, hurting readability.
- Forwarding refs correctly across different possible underlying elements adds implementation complexity.

## Interview questions
1. How does the `as` prop pattern let a component change its rendered element while keeping consistent styling and behavior?
2. Why is typing a polymorphic component's props correctly in TypeScript particularly difficult, and how would you approach it?
3. What accessibility problems can arise if a component is *not* polymorphic and consumers are forced into the wrong semantic element?
4. How do you handle ref forwarding for a component that can render as many different underlying elements?
5. When would you avoid making a component polymorphic, even though it's technically possible?
