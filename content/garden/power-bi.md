---
title: "Power BI"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Power BI

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - dashboarding
---

[Power BI](https://www.microsoft.com/power-platform/products/power-bi/) is Microsoft's self-service BI suite for reports, dashboards, and semantic models in Microsoft 365 and Azure estates. We **assess** it when Azure AD, Excel culture, or enterprise agreements already anchor analytics on Microsoft; otherwise prefer warehouse-native OSS BI.

## Blurb

> Power BI is a unified, scalable platform for self-service and enterprise business intelligence.

## Summary

**What it is:** Power BI Desktop, Service, and Embedded for DAX models, reports, and sharing in Microsoft tenants.

**When to use:** Organization standardized on Microsoft data stack; finance and ops live in Excel/Power Query patterns.

**When to skip:** Multi-cloud OSS mandate. Engineer-centric SQL BI (**[[Redash]]**, **[[Apache Superset]]**).

**Key features:** DAX semantic models, incremental refresh, row-level security, Microsoft Graph and Teams integration.


## Details

| Topic | Notes |
|-------|--------|
| **Governance** | Premium capacity for large models and paginated reports |
| **Contrast** | **[[Tableau]]** and **[[Looker]]** in competitive enterprise evals |

**References**

- [Power BI documentation](https://learn.microsoft.com/power-bi/)
