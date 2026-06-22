---
title: "Looker"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Looker

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - dashboarding
---

[Looker](https://cloud.google.com/looker) is Google Cloud's enterprise BI platform built around LookML semantic models, governed metrics, and embedded analytics. We **assess** it for GCP-centric enterprises that want a vendor-managed semantic layer; OSS paths remain **[[Apache Superset]]** or **[[Lightdash]]** with **[[dbt-core]]**.

## Blurb

> Looker is an enterprise platform for business intelligence, data applications, and embedded analytics.

## Summary

**What it is:** LookML-defined models, explores, dashboards, and embed SDKs integrated with **[[BigQuery]]** and other warehouses.

**When to use:** GCP enterprise deal includes Looker; strong governance and embedded customer analytics are requirements.

**When to skip:** Multi-cloud OSS BI mandate or small teams without LookML maintainers.

**Key features:** LookML git workflow, row-level access in models, scheduled deliveries, embed and API surfaces.


## Details

| Topic | Notes |
|-------|--------|
| **Fit** | Natural with **[[BigQuery]]** and **[[Google Cloud Platform]]** estates |
| **Contrast** | **[[Power BI]]** and **[[Tableau]]** for Microsoft- or Salesforce-centric buyers |

**References**

- [Looker documentation](https://cloud.google.com/looker/docs)
