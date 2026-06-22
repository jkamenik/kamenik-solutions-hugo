---
title: "Steampipe"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Steampipe

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
---

[Steampipe](https://steampipe.io/) is an open source engine that queries cloud APIs and SaaS services with SQL via plugins. It builds live inventories and compliance checks without maintaining custom scrapers. We **assess** it next to **[[CloudGraph]]** for multi-cloud visibility and ad hoc CSPM-style questions.

## Blurb

> Steampipe is the zero-ETL way to query APIs with SQL.

## Summary

**What it is:** Postgres interface over steampipe plugins (AWS, Azure, GCP, GitHub, etc.) plus mod benchmarks.

**When to use:** Engineers want SQL over cloud inventory; quick compliance mods before buying a CSPM suite.

**When to skip:** Need persistent graph API and packaged posture product (**[[CloudGraph]]**, **[[Kubescape]]**). No SQL-friendly operators.

**Key features:** `steampipe query`, mods pack, dashboard snapshots, CI-friendly JSON output.


## Details

| Topic | Notes |
|-------|--------|
| **Contrast** | **[[CloudGraph]]** for GraphQL posture graph; Steampipe for SQL-first exploration |
| **Ops** | Runs locally or in CI; not a long-lived multi-tenant SaaS |

**References**

- [Steampipe documentation](https://steampipe.io/docs)
