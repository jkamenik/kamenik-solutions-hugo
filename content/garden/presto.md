---
title: "Presto"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Presto

params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: "New"
---

[Presto](https://prestodb.io/) (PrestoDB) is a distributed SQL query engine for federated analytics across data lakes and warehouses. It pioneered interactive SQL at scale before the **[[Trino]]** fork. We **hold** new PrestoDB deployments; prefer **[[Trino]]** for active community and release cadence unless legacy Presto is already entrenched.

## Blurb

> Presto is an open source distributed SQL query engine for running interactive analytic queries against data sources of all sizes.

## Summary

**What it is:** Coordinator/worker cluster executing ANSI SQL over connectors (Hive, Iceberg, RDBMS, etc.).

**When to use:** Maintaining existing PrestoDB clusters and connectors tied to that lineage.

**When to skip:** Greenfield federated SQL. Start with **[[Trino]]** or warehouse-native engines (**[[BigQuery]]**, **[[Snowflake]]**).

**Key features:** Connector plugin model, interactive queries, integration with **[[Apache Superset]]** and **[[Metabase]]**.


## Details

| Topic | Notes |
|-------|--------|
| **History** | Trino forked from PrestoDB; names and vendors diverged |
| **BI** | **[[Apache Superset]]** lists Presto/Trino as first-class datasources |

**References**

- [Presto documentation](https://prestodb.io/docs/current/)
