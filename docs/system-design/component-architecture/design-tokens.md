# Design Tokens

## What it is
The smallest, named units of a design system — colors, spacing, typography scales, border radii, shadows — stored as data (JSON/YAML or a tool like Figma Tokens) rather than hardcoded in component styles, and transformed into platform-specific outputs (CSS variables, JS constants, iOS/Android values).

## Why it's useful
- Single source of truth for design decisions — change a token once and it propagates everywhere it's used, instead of hunting down hardcoded hex values across the codebase.
- Keeps design and code in sync — designers work with the same named values (`color.primary.500`) that developers reference in code.
- Enables theming (light/dark mode, white-labeling) by swapping token values without touching component logic.

## Classic use-cases
- Powering light/dark mode or multi-brand theming by swapping a token set rather than rewriting components.
- Keeping a design system consistent across multiple products/platforms (web, iOS, Android) sharing the same token definitions.
- Enforcing design consistency by making "off-palette" colors/spacing impossible to reach for, since only tokens are exposed.

## Pros
- Eliminates drift between design tools and shipped code — one source of truth for values.
- Makes systemic design changes (rebrand, theme swap) a data change instead of a code change.
- Scales cleanly across multiple platforms/products sharing a design system.

## Cons
- Requires tooling and process investment (token pipeline, build step to generate outputs) that's overkill for a small, single-product app.
- Token naming/organization itself is a design decision that's easy to get wrong early and expensive to restructure later.
- Can be over-engineered — too many token layers/abstractions makes it harder to reason about than just using values directly.

## Interview questions
1. What problem do design tokens solve that hardcoded values in component styles don't?
2. How would you structure a token pipeline that outputs to CSS variables, JS, and native mobile formats from one source?
3. How do design tokens enable theming (light/dark mode) without touching component implementation?
4. What are the risks of over-engineering a token system for a small team/product?
5. How do you keep design tool (Figma) token definitions in sync with what's actually shipped in code?
