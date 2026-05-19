---
title: "Auth0"
date: 2024-10-01
lastmod: 2026-05-18
draft: false

keywords:
  - Auth0

params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: "No Change"
    subcategories:
      - identity-provider

aliases:
  - /radar/platforms/auth0
---

[Auth0](https://auth0.com/) is a managed **identity platform** (now part of **Okta**) for embedding sign-up, login, and API access in applications, especially B2B **[[SaaS]]** products. It speaks **OIDC** / OAuth 2.0 and offloads passwords, social login, MFA, and hosted Universal Login. We rate it **assess**: strong for fast product auth, but weigh cost, tenant-model fit, and exit strategy before you bake it in.

## Blurb

> Auth0 is an easy to implement, adaptable authentication and authorization platform.

## Summary

**Positioning:** developer-first IdP below enterprise workforce suites (Okta workforce, Ping, etc.) but overlapping Okta’s own portfolio since the acquisition; clarify sales and contract path if you already standardize on Okta.

**When to assess:** greenfield SaaS needing orgs/tenants, social and enterprise connections (SAML/OIDC), machine-to-machine APIs, and customizable login UX without building auth from scratch.

**When to look elsewhere:** single-tenant apps with simple needs (framework auth or cloud IdP may suffice); strict data residency or air-gap (self-hosted **Keycloak**-class options); deep B2B2B product-led onboarding layers (compare **[[FrontEgg]]** and similar “user management” platforms).

**Ops & security:** treat Auth0 as critical infrastructure; enable MFA for admins, lock down Management API tokens, use **[[DevSecOps]]** review on Rules/Actions code, and pair workforce access patterns with **[[Access on Demand]]** where production elevation matters. **[[Boundary (Hashicorp)]]** and other tools can consume OIDC from Auth0 for human access to infra.

## Details

| Topic | Notes |
|-------|--------|
| **Protocols** | OIDC, OAuth 2.0, SAML for enterprise connections |
| **B2B** | Organizations, roles, invitation flows; map to your **[[RBAC]]** model in the app |
| **Pricing** | MAU and feature tiers bite at scale; model cost before commit |
| **Portability** | Standards help, but Rules/Actions and hosted UX create migration work |
| **Compliance** | Verify region, logging, and audit needs for your sector |

**Garden stance:** **assess** on every new product; prove you need a dedicated embedded IdP vs. cloud-native identity (e.g. Cognito, Entra, Google) or building on a framework.
