# Headless Vs Styled

## What it is
Two philosophies for building shared UI components. A **headless** component (Radix, React Aria, Downshift) provides behavior, state management, and accessibility — but zero visual styling — leaving all markup and CSS entirely up to the consumer. A **styled** component (Chakra UI, Material UI) ships both behavior and a complete, opinionated visual design out of the box.

## Why it's useful
- Headless components let a team build a fully custom-looking design system without reimplementing the genuinely hard, easy-to-get-wrong parts (focus management, keyboard interaction, ARIA) from scratch.
- Styled component libraries get a product to a polished, consistent look far faster when custom visual design isn't the priority.
- Understanding the distinction clarifies a real build vs. buy decision teams face early in a design system's life: how much of "the hard part" do we want to own?

## Classic use-cases
- A company with a strong, distinct brand identity building custom-styled components on top of headless primitives (Radix + custom CSS) to get correct behavior without fighting someone else's visual opinions.
- An internal tool or MVP reaching for a fully styled library (Material UI, Chakra) to move fast when visual distinctiveness isn't the priority.
- Migrating from a styled library to a headless one as a product matures and needs a more distinctive, on-brand visual design.

## Pros
- Headless: full visual control while still getting correct, accessible interaction behavior for free.
- Styled: fastest path to a polished, consistent UI, especially valuable early on or for internal tools.
- Understanding both lets a team make a deliberate choice rather than defaulting to whichever library they found first.

## Cons
- Headless: you still have to build and maintain all the actual visual design and CSS yourself — it solves behavior, not aesthetics.
- Styled: fighting a library's built-in visual opinions to achieve a custom look is often harder than building from a headless base in the first place.
- Switching from one philosophy to the other later (styled → headless, or vice versa) is a significant migration, not a small refactor.

## Interview questions
1. What does a headless component library actually provide, if not styling?
2. When would you choose a fully styled library over a headless one, and vice versa?
3. What's the risk of trying to heavily re-skin a styled component library to match a custom brand?
4. How does a headless library like Radix or React Aria handle accessibility concerns (focus, keyboard, ARIA) on your behalf?
5. What would migrating from a styled library to a headless one involve for an existing product?
