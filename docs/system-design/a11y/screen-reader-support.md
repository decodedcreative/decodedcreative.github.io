# Screen Reader Support

## What it is
Ensuring that a screen reader (VoiceOver, NVDA, JAWS) can accurately announce what's on the page — correct accessible names for interactive elements, meaningful alt text for images, live regions for dynamic content updates — validated through both automated tooling (axe-core, Lighthouse) and manual testing with real screen readers.

## Why it's useful
- Automated tools (axe-core, Lighthouse) catch a meaningful subset of accessibility issues (missing labels, contrast, ARIA misuse) automatically in CI, but they can't catch everything — many real problems only surface when you actually listen to a screen reader use the page.
- Live regions (`aria-live`) let dynamic content changes (a validation error appearing, a toast notification) get announced to screen reader users who wouldn't otherwise see it happen visually.
- Correct accessible names (not just visible text) ensure icon-only buttons, complex controls, and images are actually understandable when read aloud.

## Classic use-cases
- Adding meaningful `alt` text to informative images and empty `alt=""` to purely decorative ones.
- Using `aria-live` regions for asynchronous updates (form validation errors, toast notifications, live search result counts).
- Running automated accessibility audits (axe-core, Lighthouse) in CI to catch regressions, supplemented by periodic manual screen reader testing.

## Pros
- Automated auditing tools integrate cleanly into CI, catching a real subset of issues automatically and continuously.
- Live regions solve a real, otherwise-invisible problem: dynamic content changes that sighted users see but screen reader users wouldn't otherwise know about.
- A relatively small set of practices (accessible names, alt text, live regions) covers a large share of real-world screen reader issues.

## Cons
- Automated tools have real limits — they catch maybe a third to half of real accessibility issues; manual testing with an actual screen reader is still necessary for full confidence.
- Overusing `aria-live` or announcing too much can overwhelm screen reader users with noise, which is its own usability problem.
- Manual screen reader testing requires learning the tool itself (VoiceOver/NVDA have their own navigation model), which most sighted engineers haven't done.

## Interview questions
1. What kinds of accessibility issues can automated tools like axe-core catch, and what do they typically miss?
2. What is an `aria-live` region, and what problem does it solve for dynamic content updates?
3. How would you decide what alt text an image needs, versus when it should be marked purely decorative?
4. Why is manual screen reader testing still necessary even with strong automated tooling in place?
5. What's a risk of overusing live regions or ARIA announcements?
