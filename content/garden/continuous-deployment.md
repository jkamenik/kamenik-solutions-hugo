---
title: "Continuous Deployment"
date: 2026-01-13
lastmod: 2026-06-12
draft: false

keywords:
  - Continuous Deployment

params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: "No Change"
aliases:
  - /radar/techniques/continuous-deployment
---

[Continuous deployment](https://en.wikipedia.org/wiki/Continuous_deployment) extends **[[Continuous Delivery]]**: every change that passes **[[Continuous Integration]]** and downstream tests is **automatically promoted to production** without a manual release button. We rate it **assess**, not default: adopt **[[Continuous Delivery]]** everywhere; use continuous deployment when **[[Software as a Service]]** shape, observability, and release safety nets are in place.

## Blurb

> Continuous deployment is a strategy in which every change that passes automated tests is automatically released to production.

## Summary

**Where it fits:**

| Technique | Production promote |
|-----------|-------------------|
| **[[Continuous Delivery]]** (**adopt**) | Human or scheduled gate |
| **Continuous deployment** (**assess**) | Automatic on green `main` |

**Prerequisites before assess becomes adopt for a product:**

- **[[Feature Flags]]** to ship dark and enable per user/tenant
- Fast automated rollback (redeploy N-1 image, **[[ArgoCD]]** history, or equivalent)
- Metrics, logs, and alerts that detect regressions within minutes
- Staging that exercises integration/system tests meaningfully (not only unit tests)
- Team comfort with trunk-based flow and small batches

**Typical flow (SaaS on K8s):** **[[GitHub Actions]]** builds and pushes an image on merge; **[[ArgoCD]]** auto-syncs the new tag to production (or progressive sync per env). Config and secrets stay out of the image per **[[12 Factor App]]**.

**When to skip:** on-prem deliverables, regulated change windows, multi-customer installs where customers control upgrade timing, or immature test/observability culture.

**Not the same as:** deploying from laptops; **[[Capistrano]]** SSH pushes; or \"CD\" meaning only **[[Continuous Delivery]]** with a manual promote.

## Details

| Topic | Notes |
|-------|--------|
| **Risk** | Production blast radius is the whole pipeline's responsibility |
| **Quality bar** | CI + staging must be trusted; flaky tests block all progress |
| **Compliance** | May still need audit trails and approval *policies* even if deploy is automatic |
| **Canary/blue-green** | Optional layers on top; not a substitute for flags and rollback |

**References**

- [Wikipedia: Continuous deployment](https://en.wikipedia.org/wiki/Continuous_deployment)
