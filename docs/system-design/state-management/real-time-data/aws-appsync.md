# AWS AppSync

## What it is
A managed GraphQL service from AWS that provides a hosted GraphQL API with built-in real-time subscriptions, offline sync, and direct integration with AWS data sources (DynamoDB, Lambda, RDS, Elasticsearch) via resolvers, without needing to run your own GraphQL server.

## Why it's useful
- Removes the operational burden of running and scaling a GraphQL server — AWS manages the infrastructure.
- Built-in GraphQL subscriptions give real-time updates (over WebSockets under the hood) without building that infrastructure yourself.
- Resolvers connect directly to AWS services (DynamoDB, Lambda, HTTP APIs), reducing the need for a separate backend layer for simple CRUD.

## Classic use-cases
- Mobile/web apps needing real-time data sync (e.g., collaborative apps, live dashboards) built on AWS infrastructure.
- Apps wanting offline-first support with automatic conflict resolution and sync when connectivity returns.
- Teams already on AWS wanting a managed GraphQL layer over DynamoDB/Lambda without standing up Apollo Server themselves.

## Pros
- Fully managed — no GraphQL server to deploy, patch, or scale yourself.
- Native real-time subscriptions and offline sync built into the service.
- Tight integration with the rest of the AWS ecosystem (IAM auth, Cognito, DynamoDB, Lambda).
- Automatic scaling handled by AWS.

## Cons
- Vendor lock-in to AWS — migrating off AppSync later means rebuilding the resolver/subscription layer elsewhere.
- Resolver logic (VTL templates or JS resolvers) has its own learning curve distinct from writing a typical GraphQL server.
- Less flexible than a self-hosted Apollo Server for complex custom business logic that doesn't map cleanly to AWS data sources.
- Cost model (per-request/data-transfer pricing) needs to be modeled for high-traffic real-time use cases.

## Interview questions
1. How does AppSync implement GraphQL subscriptions under the hood, and what transport does it use?
2. What are AppSync resolvers, and how do they connect a GraphQL field to a DynamoDB table or Lambda function?
3. How does AppSync's offline sync and conflict resolution work for mobile clients?
4. What are the tradeoffs of using a managed service like AppSync vs. self-hosting Apollo Server?
5. How would you handle authorization (per-field or per-type) in an AppSync API?
6. When would AppSync not be a good fit compared to a custom GraphQL server?
