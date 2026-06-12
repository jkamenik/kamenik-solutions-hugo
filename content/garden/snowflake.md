---
title: "Snowflake"
date: 2026-06-12
lastmod: 2026-06-12
draft: false

keywords:
  - Snowflake

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
---

[Snowflake](https://www.snowflake.com/) is a cloud-native analytics data platform with separated storage and compute, standard SQL, and multi-cloud deployment. We **assess** it for enterprise EDW workloads when buyers want Snowflake's sharing and marketplace model; **[[BigQuery]]** competes on **[[Google Cloud Platform]]**.

## Blurb

> Snowflake is a single, global platform that powers the Data Cloud.

## Summary

**What it is:** Virtual warehouses, micro-partition storage, role-based access, data sharing, and Snowpark for app logic.

**When to use:** Enterprise analytics standardizing on Snowflake; cross-org data sharing; **[[dbt-core]]** models targeting Snowflake.

**When to skip:** GCP-only strategy (**[[BigQuery]]**). Small datasets on **[[Postgres]]** replicas.

**Key features:** Time travel, clones, streams/tasks, marketplace listings, native **[[Apache Superset]]** / **[[Metabase]]** connectors.

## Details

| Topic | Notes |
|-------|--------|
| **Cost** | Monitor warehouse idle time and query patterns |
| **BI** | Pairs with **[[Looker]]**, **[[Tableau]]**, **[[Power BI]]**, and OSS BI tools |

**References**

- [Snowflake documentation](https://docs.snowflake.com/)
