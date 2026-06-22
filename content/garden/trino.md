---
title: "Trino"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Trino

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
---

[Trino](https://trino.io/) is the community fork of Presto: a distributed SQL query engine for interactive analytics across lakes, warehouses, and RDBMS sources. **[[Apache Superset]]** and **[[Redash]]** connect for BI. We **assess** Trino for federated SQL when a warehouse alone is not enough; primary EDW may still be **[[Snowflake]]** or **[[BigQuery]]**.

## Blurb

> Trino is a fast distributed SQL query engine for big data analytics.

## Summary

**What it is:** Coordinator plus workers, connector plugins (Iceberg, Delta, Hive, PostgreSQL, etc.), ANSI SQL with MPP execution.

**When to use:** Query data in object storage without copying everything into one warehouse; multi-source joins for analytics teams.

**When to skip:** Simple single-warehouse BI. Ops team cannot run another stateful cluster.

**Key features:** Fault-tolerant execution, dynamic filtering, role-based access via connectors, Kubernetes Helm charts.


## Details

| Topic | Notes |
|-------|--------|
| **Contrast** | **[[Presto]]** (**hold**) for legacy PrestoDB only |
| **BI** | First-class datasource for **[[Apache Superset]]**, **[[Metabase]]**, **[[Redash]]** |

**References**

- [Trino documentation](https://trino.io/docs/current/)
