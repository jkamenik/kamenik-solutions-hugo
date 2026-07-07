---
title: Continuous Deployment
date: '2026-01-13'
lastmod: '2026-07-02'
draft: false
keywords:
- Continuous Deployment
params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: No Change
aliases:
- /radar/techniques/continuous-deployment
---

[Continuous Deployment](https://en.wikipedia.org/wiki/Continuous_deployment) is a technique we **assess** in the garden.

## Summary

**Overview:** extends **[[Continuous Delivery]]**: every change that passes **[[Continuous Integration]]** and downstream tests is **automatically promoted to production** without a manual release button. We rate it **assess**, not default: adopt **[[Continuous Delivery]]** everywhere; use continuous deployment when **[[Software as a Service]]** shape, observability, and release safety nets are in place.

| Topic | Notes |
|-------|--------|
| **Risk** | Production blast radius is the whole pipeline's responsibility |
| **Quality bar** | CI + staging must be trusted; flaky tests block all progress |
| **Compliance** | May still need audit trails and approval *policies* even if deploy is automatic |
| **Canary/blue-green** | Optional layers on top; not a substitute for flags and rollback |

**References**

- [Wikipedia: Continuous deployment](https://en.wikipedia.org/wiki/Continuous_deployment)## Personal Experience

<!-- User-owned: vault-only; never published or exported. Agents read for /tech-garden update synthesis; proofread spelling/grammar only. -->

## Details

| Topic | Notes |
|-------|--------|
| **Risk** | Production blast radius is the whole pipeline's responsibility |
| **Quality bar** | CI + staging must be trusted; flaky tests block all progress |
| **Compliance** | May still need audit trails and approval *policies* even if deploy is automatic |
| **Canary/blue-green** | Optional layers on top; not a substitute for flags and rollback |

**References**

- [Wikipedia: Continuous deployment](https://en.wikipedia.org/wiki/Continuous_deployment)
