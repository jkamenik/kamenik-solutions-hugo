---
title: "Continuous Delivery"
date: 2026-01-13
lastmod: 2026-06-12
draft: false

keywords:
  - Continuous Delivery

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"
aliases:
  - /radar/techniques/continuous-delivery
---

[Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery) (CD) means every change that passes **[[Continuous Integration]]** produces a **releasable artifact**; production deploy is a deliberate, low-risk promotion (button, approval, or automated stage), not an emergency rebuild. We **adopt** CD for all products; choose **[[Continuous Deployment]]** (**assess**) only when **[[Software as a Service]]** economics and observability justify shipping every green mainline commit.

## Blurb

> Continuous delivery is a software engineering approach in which teams produce software in short cycles, ensuring that the software can be reliably released at any time.

## Summary

**CI vs CD:**

| Stage | Technique | Outcome |
|-------|-----------|---------|
| Merge to main | **[[Continuous Integration]]** (**adopt**) | Built, tested artifact |
| Releasable always | **Continuous Delivery** (**adopt**) | Artifact in registry/repo; deploy pending |
| Auto to production | **[[Continuous Deployment]]** (**assess**) | No human promote step |

**Typical delivery pipeline (after CI):**

1. **Broader testing** (system/integration in staging)
2. **Artifact signing** and provenance (supply chain)
3. **Artifact publishing** (registry, chart repo, installer blob)
4. **Promotion** to environments (dev → staging → prod) with gates

**When delivery (not deployment):** on-prem or customer-operated installs, regulated industries, multi-tenant SaaS with scheduled releases, or when rollback/feature control needs a human promote.

**When deployment instead:** internal **[[Software as a Service]]** with **[[Feature Flags]]**, strong metrics, and automated rollback; see **[[Continuous Deployment]]**.

**Tooling:** **[[GitHub Actions]]** for build/sign/publish; **[[ArgoCD]]** + **[[GitOps]]** for K8s promote-by-sync; avoid **[[Capistrano]]**-style SSH push for new work.

## Details

| Topic | Notes |
|-------|--------|
| **Definition of done** | Main is green *and* artifact is in the catalog customers could receive |
| **Gates** | Manual approval, change windows, or policy checks on promote |
| **Config** | Environment-specific values outside the image (12-factor) |
| **Rollback** | Redeploy previous artifact tag; keep N-1 ready |

**References**

- [Wikipedia: Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery)
