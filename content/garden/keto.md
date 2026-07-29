---
title: Keto
date: '2024-10-01'
lastmod: '2026-07-28'
draft: false
keywords:
- Keto
- Ory Keto
params:
  aliases:
  - Ory Keto
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[Keto](https://www.ory.com/keto) is Ory's Zanzibar-style authorization server for relationship-based permission checks. We **assess** it under **[[Tool]]** when comparing ReBAC engines, especially if an estate already runs Ory.

## Blurb

> Authorization server based on Google Zanzibar — supporting RBAC and ReBAC patterns at scale.

## Summary

**What it is:** Open-source permission server from Ory. Apps write relation tuples, define permission models (including Ory Permission Language), and call check APIs over HTTP or gRPC.

**When to use:** You need **[[Zanzibar]]**-style ReBAC and already standardize on the Ory stack (identity and OAuth beside permissions). Managed Ory Network or self-hosted OSS/OEL are acceptable deployment paths.

**When to skip:** Simple **[[RBAC]]** matrices or static policy bundles are enough. Prefer **[[Open Policy Agent]]** with **[[Policy as Code]]** for config and admission gates. Prefer **[[SpiceDB]]** when you want a standalone ReBAC datastore with strong consistency tooling and are not tied to Ory.

**Key features:** Relation tuples and graph checks, RBAC and ReBAC from one API, Ory Permission Language, SDKs for major languages, deploy as OSS, Ory Enterprise License, or Ory Network.

## Details

| Topic | Notes |
|-------|--------|
| **Model** | ReBAC tuples and permission checks; complements policy engines rather than replacing them |
| **Ops** | Self-host Apache 2.0 OSS, Ory Enterprise License with support, or managed Ory Network |
| **Ecosystem** | Fits beside Ory Kratos (identity) and Ory Hydra (OAuth2/OIDC); headless API-first |

**Compared to [[SpiceDB]]**

Both implement Google **[[Zanzibar]]**-style relationship authorization. SpiceDB emphasizes schema language, ZedTokens, and AuthZed Cloud. Keto is strongest when the estate already runs Ory components and wants one vendor story for identity plus permissions.

**Compared to [[Open Policy Agent]]**

OPA evaluates Rego against JSON inputs. Keto persists relationships and answers object-level permission queries at runtime. Many estates use both: OPA for infrastructure policy, Keto for application ReBAC.

**References**

- [Ory Keto product page](https://www.ory.com/keto)
- [Ory Keto documentation](https://www.ory.com/docs/keto)
- [ory/keto on GitHub](https://github.com/ory/keto)
