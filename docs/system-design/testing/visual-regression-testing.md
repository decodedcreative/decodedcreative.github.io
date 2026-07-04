# Visual Regression Testing

## What it is
Automated comparison of a component or page's rendered visual output (a screenshot) against a stored baseline image, flagging pixel-level differences for human review. Tools like Chromatic (built for Storybook) and Percy automate capturing, diffing, and reviewing these snapshots across PRs.

## Why it's useful
- Catches unintended visual regressions (broken layout, wrong color, misaligned spacing) that functional tests don't check for at all — a test can pass logically while the UI looks broken.
- Reviewing a visual diff is far faster than manually re-checking every component/page after a shared style or dependency change.
- Works well alongside a component library/Storybook, giving visual coverage of every component variant, not just full pages.

## Classic use-cases
- Catching regressions in a shared design system after updating a base component (button, input) used across many screens.
- Verifying a CSS/dependency upgrade (e.g., a new version of a UI library) didn't silently break layouts.
- Reviewing the visual impact of a PR before merging, especially for shared/foundational components.

## Pros
- Catches an entire category of bugs (visual/layout) invisible to functional or logic-based tests.
- Automates what would otherwise be tedious manual visual QA across many components/pages.
- Pairs naturally with a component library — one snapshot per variant gives broad visual coverage cheaply.

## Cons
- Prone to noisy false positives from font rendering differences, anti-aliasing, or non-deterministic content (dates, animations) unless carefully controlled.
- Requires human review of diffs, which is a manual step that doesn't fully automate away — someone still has to approve/reject changes.
- Baseline management (updating "approved" snapshots after intentional design changes) adds process overhead.

## Interview questions
1. What category of bugs does visual regression testing catch that unit/integration tests fundamentally cannot?
2. How do you reduce false-positive noise from things like font rendering or animation timing?
3. How would you integrate visual regression testing into a CI pipeline and PR review process?
4. Why does visual regression testing pair especially well with a component library/Storybook setup?
5. How do you handle updating baselines after an intentional design change without losing the ability to catch real regressions?
