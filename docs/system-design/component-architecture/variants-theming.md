# Variants + Theming

## What it is
The system by which a component supports multiple visual variations (a `Button` with `primary`/`secondary`/`danger` variants, `small`/`medium`/`large` sizes) and adapts to a theme (light/dark mode, brand-specific styling) — typically implemented via a `variant`/`size` prop mapped to predefined style combinations, backed by design tokens for the actual color/spacing values.

## Why it's useful
- Gives consumers a small, constrained set of supported looks (`variant="primary"`) instead of exposing raw style props that could produce inconsistent, off-design results.
- Centralizing variant definitions means a design update (e.g., changing what "primary" looks like) is a single change that propagates everywhere that variant is used.
- Theming support (light/dark, multi-brand) lets the same component tree render correctly across different visual contexts without component-level logic branching on the theme.

## Classic use-cases
- A design system's core components (`Button`, `Badge`, `Alert`) each supporting a fixed set of variants matching the design system's defined styles.
- Light/dark mode support driven by swapping theme values rather than rewriting component styles.
- Multi-brand or white-label products where the same component library needs to visually adapt per brand/tenant.

## Pros
- Keeps visual consistency by construction — consumers pick from supported variants rather than reaching for arbitrary custom styles.
- A single point of change for what a given variant looks like across the entire product.
- Theming plugs into the same variant system, so supporting light/dark or multi-brand doesn't require separate component logic.

## Cons
- A rigid variant API can't cover every one-off design need, creating pressure to either expand the variant set indefinitely or allow style overrides that undermine consistency.
- Implementing variants well (especially combined with theming) usually depends on a solid design token foundation — retrofitting this onto an ad-hoc styling setup is real work.
- Deciding what belongs in the fixed variant set vs. what's a one-off exception is an ongoing design/engineering negotiation, not a one-time decision.

## Interview questions
1. How would you implement a component's `variant` prop so it maps cleanly to a fixed, type-safe set of supported styles?
2. How does a token-based theming system let the same component render correctly in both light and dark mode?
3. What's the tradeoff between a rigid variant API and allowing arbitrary style overrides on a shared component?
4. How would you support a multi-brand/white-label product using the same underlying component library?
5. Where do you draw the line between "this deserves a new variant" and "this is a one-off that shouldn't be supported"?
