---
title: "Feature Flags"
date: 2026-05-05
lastmod: 2026-05-18
draft: false

keywords:
  - Feature Flags
  - feature toggles
  - feature switches

params:
  garden:
    kind: item
    usefulness: trial
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/feature-flags
---

[Feature flags](https://martinfowler.com/articles/feature-toggles.html) (feature toggles) decouple **deploying code** from **exposing behavior**: ship to production dark, then enable per user, tenant, or percentage. We promote to **trial** for **[[Software as a Service]]** products pursuing **[[Continuous Deployment]]**; stay **assess** for simple or on-prem services where homegrown toggles may not pay back.

## Blurb

> Feature Toggles (often also referred to as Feature Flags) are a powerful technique, allowing teams to modify system behavior without changing code.

## Summary

**Flag types (Fowler):**

| Type | Purpose |
|------|---------|
| **Release** | Hide incomplete work on `main`; enable when ready |
| **Experiment** | A/B tests and gradual exposure |
| **Ops** | Kill switch under load without redeploy |
| **Permission** | Entitlements / plan tiers (often overlaps **[[RBAC]]**) |

**Why trial (SaaS + CD):**

- Prerequisite in our **[[Continuous Deployment]]** model: deploy every green merge safely
- Per-tenant enablement for B2B without hotfix releases
- Instant rollback by flipping a flag, not rebuilding images

**Why still assess elsewhere:**

- Roll-your-own adds branching and cleanup debt
- Long-lived flags become dead code; need expiry discipline
- On-prem or single-tenant deliverables may prefer **[[Continuous Delivery]]** with manual promote only

**Implementation options:**

| Approach | Notes |
|----------|--------|
| **Managed** | LaunchDarkly, Unleash, Flagsmith, ConfigCat (SaaS or self-hosted) |
| **OpenFeature** | Vendor-neutral SDK surface; pick a provider backend |
| **Config + DB** | Simple boolean table; fine for one product, watch ops burden |
| **Env/config only** | Not flags; redeploy to change (avoid for user-facing toggles) |

## Details

| Topic | Notes |
|-------|--------|
| **Naming** | `feature_flags`, `toggles`; consistent prefix in code |
| **Defaults** | Safe default off for new features; document in runbooks |
| **Lifecycle** | Ticket to remove flag and dead branches after full rollout |
| **Testing** | CI matrix: flag on/off; avoid tests that only pass one state |
| **Security** | Admin flags are authorization; audit changes like **[[RBAC]]** |
| **Observability** | Log evaluation or exposure events for experiment analysis |

**Garden pattern:** **trial** when **[[Software as a Service]]** + **[[Continuous Deployment]]**; **assess** for internal tools until CD maturity is proven. Pair with metrics and rollback, not as a substitute for tests.

**Not the same as:** **[[Policy as Code]]** (infra compliance); **[[GitOps]]** sync (delivery mechanism); environment-specific config files without runtime evaluation.

**References**

- [Feature Toggles (Martin Fowler)](https://martinfowler.com/articles/feature-toggles.html)
- [OpenFeature](https://openfeature.dev/)
