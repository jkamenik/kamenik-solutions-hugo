---
title: "Single Sign-on"
date: 2026-05-17
lastmod: 2026-06-12
draft: false

keywords:
  - Single Sign-on
  - SSO

params:
  aliases:
    - SSO
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "New"
aliases:
  - /radar/techniques/single-sign-on
---

[Single Sign-on](https://en.wikipedia.org/wiki/Single_sign-on)

**Single sign-on (SSO)** lets a user authenticate once with an **identity provider (IdP)** and access multiple applications without separate passwords per app. We **adopt** SSO for B2B **[[Software as a Service]]** and internal tools: it is **[[Enterprise Ready]]** table stakes, pairs with **[[RBAC]]**, and reduces password sprawl when implemented with standard protocols.

## Blurb

> Single sign-on (SSO) is an authentication scheme that allows a user to log in with a single ID to any of several related, yet independent, software systems.

## Summary

**Protocols (prefer standards):**

| Protocol | Typical use |
|----------|-------------|
| **OIDC** | Modern SaaS, SPAs, mobile; built on OAuth 2.0 |
| **SAML 2.0** | Enterprise IdP connections (Okta, Entra ID, Google Workspace) |
| **OAuth 2.0** | Delegated API access (not full SSO by itself) |

**When adopt applies:**

- Selling to enterprises that mandate their IdP (**[[Enterprise Ready]]**)
- Workforce apps (dashboards, **[[ArgoCD]]**, **[[Boundary (Hashicorp)]]**) via corporate OIDC
- Customer orgs with "login with your company's SSO" on your product

**Implementation paths:**

| Approach | Garden notes |
|----------|----------------|
| **Embedded IdP** | **[[Auth0]]** / **[[FrontEgg]]** (**assess**) for product login + SAML/OIDC connections |
| **Cloud-native** | Cognito, Entra, Google Identity for simpler estates |
| **Self-hosted** | Keycloak-class when residency or control demands it |

**Security expectations:** MFA at the IdP, short session lifetimes, audit logs, and **[[Access on Demand]]** for privileged production access (SSO is not the same as standing admin).

## Details

| Topic | Notes |
|-------|--------|
| **SP vs IdP** | Your app is the service provider; customer brings the IdP metadata |
| **JIT provisioning** | Map SAML/OIDC claims to users and **[[RBAC]]** roles |
| **SCIM** | Optional next step for directory sync (not required for basic SSO) |
| **Testing** | Staging IdP connection per customer; document clock skew and cert expiry |
| **Break-glass** | Local emergency accounts outside SSO, vaulted and audited |

**References**

- [Wikipedia: Single sign-on](https://en.wikipedia.org/wiki/Single_sign-on)
- [Enterprise Ready](https://www.enterpriseready.io/)
