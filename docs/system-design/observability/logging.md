# Logging

## What it is
Deliberately recording structured events from the running frontend application — user actions, state transitions, API calls, feature usage — sent to a centralized logging/analytics backend, distinct from error tracking's focus on failures specifically.

## Why it's useful
- Gives visibility into what's actually happening in production, not just what's broken — useful for debugging issues that aren't outright errors (e.g., "why did this user see stale data?").
- Structured logs (consistent event names/fields) can be queried and aggregated to answer questions about usage patterns, not just individual incidents.
- Provides an audit trail for debugging complex, multi-step user flows after the fact.

## Classic use-cases
- Logging key user actions and API request/response metadata for debugging support tickets after the fact.
- Feature usage tracking to inform product decisions (which features are actually used).
- Correlating client-side logs with backend logs (via a shared request/trace ID) to debug an issue across the full stack.

## Pros
- Fills the gap between "nothing broke" and "something the user experienced was wrong but didn't throw an error."
- Structured, queryable logs are far more useful at scale than scattered `console.log` statements.
- Shared trace IDs let you follow a single request/user journey across frontend and backend systems.

## Cons
- Over-logging creates noise and cost (storage/ingestion) without proportional value — needs deliberate curation of what's worth logging.
- Logging user actions/data raises privacy and compliance considerations (PII handling, consent).
- Without structure/consistency, logs become as hard to query as unstructured text, losing much of their value.

## Interview questions
1. How does structured logging differ from scattered `console.log` calls, and why does that distinction matter at scale?
2. How would you correlate a frontend log with the corresponding backend request for debugging a cross-stack issue?
3. What's the difference between what error tracking captures vs. what general logging captures?
4. How do you decide what's worth logging vs. what would just be noise?
5. What privacy/compliance considerations apply to logging user actions or data client-side?
