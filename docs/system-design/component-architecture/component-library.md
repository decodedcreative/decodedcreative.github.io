# Component Library

## What it is
A shared, versioned package of reusable UI components (buttons, inputs, modals, layout primitives) built once and consumed across multiple applications/teams, typically published as an internal npm package with its own release cycle.

## Why it's useful
- Eliminates duplicate implementation of the same UI patterns across every product/team, saving significant engineering time.
- Centralizes accessibility, theming, and design consistency — fix or improve a component once, every consumer benefits.
- Creates a shared vocabulary between design and engineering for what components exist and how they're meant to be used.

## Classic use-cases
- A company with multiple product teams (web app, marketing site, internal tools) sharing one design system's components.
- Enforcing consistent UX (spacing, interaction patterns, accessibility) across a large organization without every team reinventing it.
- Powering rapid feature development by giving teams pre-built, tested building blocks instead of custom one-offs.

## Pros
- Massive duplication reduction across teams/products building similar UI.
- Centralizes quality (accessibility, testing, cross-browser support) in one well-maintained place.
- Speeds up feature development once the library covers common needs.

## Cons
- Versioning and breaking changes across many consumer apps is a real coordination cost — someone has to manage upgrades.
- Overly rigid/opinionated components can slow teams down when they need something the library doesn't support.
- Requires ongoing investment (a dedicated team or clear ownership) to avoid becoming outdated or abandoned.

## Interview questions
1. How would you manage breaking changes in a shared component library consumed by many independent teams?
2. What's the tradeoff between a flexible, unopinionated component API and a rigid, easy-to-use one?
3. How do you decide what belongs in a shared component library vs. what should stay app-specific?
4. How would you structure versioning/releases so consumer teams can upgrade independently and safely?
5. What ownership model works for a component library used by many teams — a dedicated platform team, or shared contribution?
