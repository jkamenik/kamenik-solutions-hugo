---
title: Steampipe
date: '2026-06-12'
lastmod: '2026-07-02'
draft: false
keywords:
- Steampipe
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[Steampipe](https://steampipe.io/). Is an open source engine that queries cloud APIs and SaaS services with SQL via plugins.

## Blurb

> Instantly query your cloud, code, logs & more with SQL. Build on thousands of open-source benchmarks & dashboards for security & insights.

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
