---
title: "Enterprise Ready"
date: 2023-07-23
lastmod: 2026-05-18
draft: false

keywords:
  - Enterprise Ready
  - EnterpriseReady
  - enterprise-ready

params:
  garden:
    kind: item
    usefulness: trial
    category: technique
    movement: "Moved In"

aliases:
  - /radar/techniques/enterprise-ready
---

[EnterpriseReady](https://www.enterpriseready.io/) is a **feature guide and checklist** (from Replicated's study of leading B2B SaaS) for what procurement and security teams expect before they buy. We rate it **trial** with **Moved In**: use it as a **product roadmap lens** when moving upmarket, not as a substitute for **[[12 Factor App]]** engineering discipline or **[[DevSecOps]]** execution.

## Blurb

> Created to help people build software for the enterprise, based on a study of the 50 leading SaaS applications.

## Summary

**Analogy:** **[[12 Factor App]]** for **how you sell and operate** B2B software; **Enterprise Ready** for **what enterprises ask for in the contract and admin console**.

**Twelve feature areas** (each has guides and tear-downs on the site):

| Area | Garden links / notes |
|------|----------------------|
| Product assortment | Plans, entitlements, usage limits |
| **[[Single Sign-on]]** | **adopt** OIDC/SAML for B2B |
| Audit logs | Admin-visible activity trail |
| **[[RBAC]]** | **adopt** role separation in product and ops |
| Change management | Admin comms for rollouts |
| Product security | **[[DevSecOps]]**, pen tests, secure SDLC |
| Deployment options | SaaS vs VPC / self-hosted tradeoffs |
| Team management | Orgs, invites, central directory |
| Integrations | APIs, webhooks, data export |
| Reporting and analytics | Value proof for buyers |
| **[[SLAs]]** | **adopt** measured commitments + SLOs |
| GDPR | Privacy program when EU customers matter |

**When trial fits:**

- First enterprise pipeline or security questionnaire
- Prioritizing backlog before SOC2-heavy sales cycles
- Aligning product, legal, and engineering on the same vocabulary

**When it is not enough:** checklists do not replace pen tests, contracts, or running **[[Policy as Code]]** on your own infra. IdP implementation still means **[[Auth0]]** / **[[FrontEgg]]** (**assess**) or cloud-native identity choices.

## Details

| Topic | Notes |
|-------|--------|
| **Prioritization** | Start SSO + RBAC + audit logs; add SLAs before promising five nines |
| **Questionnaires** | Map each ER section to evidence (architecture diagram, policies, screenshots) |
| **Product vs platform** | Some items are in-app features; others are how *you* run **[[Software as a Service]]** |
| **Podcast / tear-downs** | Use HubSpot/Slack/Google examples as design references, not copy-paste specs |

**Garden pattern:** **trial** the framework when **[[Software as a Service]]** goes enterprise; **adopt** the underlying techniques (**[[Single Sign-on]]**, **[[SLAs]]**, **[[RBAC]]**) as separate garden items mature.

**References**

- [EnterpriseReady](https://www.enterpriseready.io/)
- [Feature guides index](https://www.enterpriseready.io/)
