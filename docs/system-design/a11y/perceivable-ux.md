# Perceivable UX

## What it is
Making sure information and interface elements are perceivable regardless of a user's visual ability or environment — sufficient color contrast, not relying on color alone to convey meaning, respecting reduced-motion preferences, and supporting text resizing/zoom without breaking the layout.

## Why it's useful
- Low vision, color blindness, and situational impairments (bright sunlight, a cracked screen) are far more common than full blindness, making perceivability a high-leverage accessibility investment.
- WCAG contrast ratios are concrete, testable numbers, not subjective judgment calls, making this one of the easier accessibility categories to actually verify and enforce.
- Respecting `prefers-reduced-motion` prevents excessive animation from causing genuine discomfort (vestibular disorders) for users who've explicitly opted out of it at the OS level.

## Classic use-cases
- Verifying text/background color contrast meets WCAG AA (or AAA) ratios, especially for body text and interactive elements.
- Using icons/patterns/text labels alongside color to convey status (not just red/green) so colorblind users aren't excluded.
- Reducing or disabling non-essential animations when `prefers-reduced-motion: reduce` is set.
- Ensuring layouts don't break when text is zoomed/resized significantly (WCAG requires support up to 200% zoom without loss of content or function).

## Pros
- Concrete, measurable criteria (contrast ratios, zoom percentages) make this category easier to test and enforce than more subjective accessibility concerns.
- Benefits a very wide range of users, including many without a diagnosed disability (glare, small screens, aging vision).
- Respecting `prefers-reduced-motion` is a small implementation cost for meaningfully reducing discomfort for affected users.

## Cons
- Retrofitting sufficient contrast onto an existing brand/design system can create real tension with visual design preferences.
- Relying on manual review to catch "color alone" issues is easy to miss without a deliberate design system convention.
- Supporting significant text zoom without breaking layout requires deliberate, tested responsive design — it's not automatic.

## Interview questions
1. What are the WCAG contrast ratio requirements for normal text vs. large text, and how would you verify a design meets them?
2. Why is relying on color alone to convey status (e.g., red/green only) a real accessibility problem, and how would you fix it?
3. What does `prefers-reduced-motion` do, and what kind of animations should respect it?
4. How would you test that your application remains usable at 200% text zoom?
5. What's the difference between designing for permanent disabilities vs. situational/temporary impairments, and why do both matter?
