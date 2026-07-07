---
title: Kibana
date: '2026-06-12'
lastmod: '2026-07-02'
draft: false
keywords:
- Kibana
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - dashboarding
---

[Kibana](https://www.elastic.co/kibana). We **assess** it under **[[Tool]]** in the garden.

## Blurb

> Explore and visualize data stored in Elasticsearch with Kibana. Build dashboards, run queries, set alerts, and manage your deployment - all in one UI....

## Summary

**What it is:** Web UI for search, visualizations, dashboards, and Elastic-specific features (APM, SIEM modules in commercial tiers).

**When to use:** Committed Elastic Cloud or self-hosted Elasticsearch; security analytics on Elastic data; teams standardized on KQL and Elastic dashboards.

**When to skip:** New stacks without Elastic lock-in. Prefer **[[Grafana]]** plus Prometheus, Loki, or vendor-neutral stores.

**Key features:** Lens visualizations, saved objects, role-based spaces, alerting tied to Elastic indices.

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Bundled with Elastic Stack or Elastic Cloud |
| **Pairing** | Requires **[[Elasticsearch]]** (or serverless Elastic) as the data layer |
| **Auth** | Elastic native, SAML, OIDC in commercial tiers |

**References**

- [Kibana documentation](https://www.elastic.co/guide/en/kibana/current/index.html)
