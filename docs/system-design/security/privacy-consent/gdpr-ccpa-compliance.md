# GDPR/CCPA Compliance

## What it is
GDPR (EU) and CCPA (California) are the two most influential privacy regulations shaping how applications must handle personal data — covering things like requiring a legal basis for data collection, giving users the right to access/delete their data (Data Subject Access Requests), and requiring disclosure of what data is collected and why.

## Why it's useful
- Non-compliance carries real regulatory/financial risk, making this a genuine engineering constraint, not just a legal department's problem.
- Understanding the baseline requirements (consent, data access/deletion rights, data minimization) shapes real architectural decisions — what you log, what you store, how long you retain it.
- For a company operating internationally, differences between regulations (GDPR's opt-in consent model vs. CCPA's opt-out model) directly affect UI/UX decisions like default cookie banner behavior.

## Classic use-cases
- Implementing a "delete my account and all my data" flow to satisfy the right to erasure.
- Building a data export feature to satisfy Data Subject Access Requests.
- Choosing default consent behavior (opt-in banners for EU users, opt-out links for California users) based on which regulation applies.

## Pros
- Forces genuinely good data hygiene practices (data minimization, clear retention policies) that are good engineering regardless of legal requirement.
- Having clear compliance processes in place reduces both legal risk and the ad-hoc engineering scramble when a request or audit comes in.
- Understanding this well is a differentiator in regulated industries (adtech, fintech, healthtech) where it's a first-order concern.

## Cons
- Compliance requirements are genuinely complex and vary by jurisdiction, region, and even how data is used — this isn't a simple, one-size-fits-all checklist.
- Retrofitting compliance (deletion flows, audit trails, data minimization) onto an existing system that wasn't built with it in mind is often significant work.
- Regulations continue to evolve, requiring ongoing attention rather than a one-time implementation.

## Interview questions
1. What's the core difference between GDPR's consent model and CCPA's, and how does that affect default UI behavior?
2. How would you implement a "right to be forgotten" request across a system with data spread across multiple services/databases?
3. What does "data minimization" mean in practice, and how would you apply it to an analytics/logging pipeline?
4. Why is compliance a genuine engineering concern rather than purely a legal/policy one?
5. How would you design a system's data model from the start to make future compliance requests (access, deletion) easier to fulfill?
