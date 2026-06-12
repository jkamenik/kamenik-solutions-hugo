---
title: "Redash"
date: 2026-05-28
lastmod: 2026-06-12
draft: false

keywords:
  - Redash

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - dashboarding
aliases:
  - /radar/tools/redash
---

[Redash](https://redash.io/) is an open source data exploration and visualization platform. [[SQL]] and [[NoSQL]] users write queries in a browser editor, build charts, and share dashboards with shareable URLs. We **assess** it for team analytics when a lightweight BI layer is needed without a full enterprise warehouse suite.

## Blurb

> Redash is designed to enable anyone, regardless of the level of technical sophistication, to harness the power of data big and small.

## Summary

**What it is:** Web UI plus workers that connect to databases ([[Postgres]], [[MySQL]], [[BigQuery]], MongoDB, and many others), run scheduled queries, and publish dashboards.

**When to use:** internal ops metrics and ad hoc SQL; democratize read-only access to warehouse or replica data; embed charts via URL for runbooks.

**When to skip:** metrics already live in Grafana with datasources wired; need governed semantic layers or ML features; SaaS-only BI mandate.

**Key features:** schema browser, query snippets, visualization types, alerts on query results, API access.

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Docker Compose or Helm; workers scale query load |
| **Auth** | SSO and row-level access via data source credentials |
| **Queries** | Parameterized SQL with schedule and alert hooks |

**Practices:** read-only DB users; separate prod vs analytics replicas; audit shared dashboard links.

**References**

- [Redash help](https://redash.io/help/)
- [GitHub repository](https://github.com/getredash/redash)
