---
title: Presto
date: '2026-06-12'
lastmod: '2026-07-02'
draft: false
keywords:
- Presto
params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: No Change
---

[Presto](https://prestodb.io/). (PrestoDB) is a distributed SQL query engine for federated analytics across data lakes and warehouses.

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
