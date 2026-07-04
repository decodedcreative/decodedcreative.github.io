# OAuth 2.0 & OIDC

## What it is
OAuth 2.0 is an authorization protocol — it lets a user grant a third-party app limited access to their data on another service without sharing their password. OpenID Connect (OIDC) is a thin identity layer built on top of OAuth 2.0, adding a standardized way to actually authenticate the user (who they are), not just authorize access. For public clients (SPAs, mobile apps), the Authorization Code flow with PKCE is the current standard — it avoids exposing tokens in a way that can be intercepted.

## Why it's useful
- Lets an app support "Sign in with Google/GitHub/etc." without ever handling the user's password directly.
- OIDC standardizes identity (an ID token with the user's identity claims) on top of OAuth's access-delegation model, so apps don't need a bespoke identity protocol.
- PKCE closes a real vulnerability in public clients (no client secret can be safely stored in a browser or mobile app) by binding the authorization code to a dynamically generated secret.

## Classic use-cases
- "Sign in with X" social login flows.
- Single sign-on (SSO) across multiple internal applications sharing one identity provider (Auth0, Okta, WorkOS).
- Delegated API access — letting a third-party app access a user's data on your platform with scoped, revocable permission.

## Pros
- Avoids apps ever handling raw user passwords for third-party logins.
- Well-standardized, broadly supported by identity providers, reducing bespoke auth code.
- Scoped, revocable access — a user can revoke a specific app's access without changing their password.

## Cons
- The flow itself (redirects, authorization codes, token exchange) adds real complexity compared to a simple username/password form.
- Misconfiguration (wrong redirect URI validation, missing PKCE on public clients) is a common source of real vulnerabilities.
- Relying on a third-party identity provider introduces an external dependency/outage risk for your login flow.

## Interview questions
1. What's the difference between what OAuth 2.0 provides and what OIDC adds on top of it?
2. Why does PKCE matter specifically for public clients like single-page apps, and what attack does it prevent?
3. Walk through the Authorization Code + PKCE flow end to end.
4. What happens if an app doesn't validate the redirect URI strictly enough?
5. How would you implement "sign out" in a way that actually invalidates the session, not just clears local state?
