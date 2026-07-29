---
title: Metabase
date: '2026-05-28'
lastmod: '2026-07-29'
draft: false
keywords:
- Metabase
params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: No Change
    subcategories:
    - dashboarding
aliases:
- /radar/tools/metabase
---

[Metabase](https://www.metabase.com/). Is open source business intelligence and embedded analytics.

## Blurb

> Query in natural language and give your team AI-powered analytics built on your metrics and permissions. Deploy in minutes.

## Summary

**Garden stance:** We **hold** Metabase for our estate.

**Key points:**

| Topic | Notes |
|-------|--------|
| **Deploy** | **Hold path:** Docker/JAR self-hosted (prefer **[[Grafana]]** OSS instead for new work). **SaaS path:** Metabase Cloud when federated data or ops cost dominates |
| **Data model** | Live queries against connected databases; extracts optional via caching settings |
| **Auth** | Google, LDAP, SAML; row-level sandboxing on supported plans |

**Practices:** Use read-only DB credentials; separate analytics replicas from OLTP; audit public links and embedded iframe origins.

**References**

- [Metabase documentation](https://www.metabase.com/docs/latest/)
- [GitHub repository](https://github.com/metabase/metabase)

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | **Hold path:** Docker/JAR self-hosted (prefer **[[Grafana]]** OSS instead for new work). **SaaS path:** Metabase Cloud when federated data or ops cost dominates |
| **Data model** | Live queries against connected databases; extracts optional via caching settings |
| **Auth** | Google, LDAP, SAML; row-level sandboxing on supported plans |

**Practices:** Use read-only DB credentials; separate analytics replicas from OLTP; audit public links and embedded iframe origins.

**References**

- [Metabase documentation](https://www.metabase.com/docs/latest/)
- [GitHub repository](https://github.com/metabase/metabase)
