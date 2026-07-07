---
title: Apache Superset
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- Apache Superset
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - dashboarding
aliases:
- /radar/tools/apache-superset
---

[Apache Superset](https://superset.apache.org/). Is a modern, enterprise-ready business intelligence web application from the [[Apache Software Foundation]].

## Summary

**What it is:** Python/Flask app with React frontend, Celery workers, and configurable cache. Ships with 40+ chart types, custom viz plugins, [[REST]] [[API]], and integration with warehouses, lakes, and query engines ([[Presto]], [[Trino]], [[Snowflake]], [[BigQuery]], [[Postgres]], and more).

**When to use:** Central BI platform with curated datasets and metrics; advanced SQL analysts; geospatial and plugin-heavy dashboards; multi-tenant security roles in regulated environments.

**When to skip:** Small teams that want the fastest path to shareable SQL dashboards (**[[Redash]]** or **[[Metabase]]**). Primary workload is time-series monitoring and alerting (**[[Grafana]]**). Ops overhead of Redis, metadata DB, and workers is not justified for a handful of charts.

**Key features:** Explore and SQL Lab, semantic layer for dimensions and metrics, async queries, caching layer, OAuth and RBAC, cloud-native [[Helm]] charts.

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Docker Compose, Kubernetes/Helm, or managed offerings; requires metadata database, cache, and message broker for production scale |
| **Data model** | Datasets point at physical tables or SQL; metrics and dimensions defined in UI or YAML |
| **Auth** | FAB security manager, LDAP/OAuth, row-level security filters on datasets |

**Practices:** Version dataset definitions where possible; cap async query timeouts; separate read-only warehouse roles; test upgrades in staging because the release cadence is active.

**References**

- [Apache Superset documentation](https://superset.apache.org/docs/intro)
- [GitHub repository](https://github.com/apache/superset)
