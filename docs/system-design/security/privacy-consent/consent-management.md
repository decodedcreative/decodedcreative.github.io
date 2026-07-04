# Consent Management

## What it is
The system and UI (cookie banners, preference centers) responsible for asking users what data collection/tracking they'll allow, recording that choice, and ensuring the rest of the application actually honors it — including standards like the IAB's Transparency & Consent Framework (TCF), which lets advertising/adtech vendors exchange a standardized signal of what a user has consented to.

## Why it's useful
- Turns "did the user agree to tracking" from a vague assumption into an explicit, auditable, enforceable piece of state.
- IAB TCF gives adtech vendors a common format to pass consent signals to each other, so consent collected once can be honored consistently across a chain of downstream partners.
- Done right, consent becomes actual application state that gates behavior (don't fire this pixel, don't load this SDK) rather than a banner that's cosmetically dismissed but ignored.

## Classic use-cases
- Blocking analytics/advertising scripts from loading at all until the user has made a choice ("consent-before-load").
- An adtech platform needing to know, for any given user/audience segment, exactly what data usage they've consented to before it can even be displayed or activated.
- Propagating a consent signal (via IAB TCF or Google Consent Mode) to every downstream vendor/pixel a page loads.

## Pros
- Makes compliance genuinely enforceable rather than just a banner for show — real script-loading behavior is gated on the recorded choice.
- Standardized formats (IAB TCF, Consent Mode) let consent state interoperate across many third-party vendors consistently.
- Treating consent as first-class application state makes it something you can reason about architecturally, not bolt on as an afterthought.

## Cons
- Blocking scripts until consent is granted can measurably affect performance/analytics completeness and even Core Web Vitals if not implemented carefully.
- Consent requirements vary significantly by jurisdiction (EU vs. US vs. UK), which pushes real complexity into the UI/logic layer.
- Keeping the actual behavior of every third-party script/pixel in sync with the recorded consent state requires ongoing governance, not a one-time implementation.

## Interview questions
1. What does "consent-before-load" mean in practice, and how does it interact with page performance/LCP?
2. How does the IAB TCF let multiple advertising vendors share a consistent understanding of what a user consented to?
3. For an adtech product specifically, why might consent state need to be treated as top-level application state rather than an isolated banner component?
4. How would you audit that every third-party pixel/script on a page actually honors the recorded consent choice?
5. How do consent requirements differ across jurisdictions (GDPR vs. CCPA), and how does that affect your UI/architecture?
