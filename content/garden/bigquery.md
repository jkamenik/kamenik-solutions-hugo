---
title: "BigQuery"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - BigQuery

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
aliases:
  - /radar/tools/bigquery
---

[BigQuery](https://cloud.google.com/bigquery) is Google Cloud's fully managed, serverless data platform for [[SQL]] analytics, ML, and BI at petabyte scale. Storage and compute scale independently with no cluster sizing. We **assess** it when [[Google Cloud Platform|GCP]] is in play or a columnar EDW beats stretching **[[Postgres]]** for analytics volume.

## Blurb

> BigQuery is a fully managed, AI-ready data platform that helps you manage and analyze your data with built-in features like machine learning, search, geospatial analysis, and business intelligence.

## Summary

**What it is:** Columnar warehouse with standard SQL, partitioned tables, streaming inserts, BigQuery ML, and native ties to Looker, Vertex AI, and GCP IAM. Pay per query and storage; slot reservations for steady workloads.

**When to use:** Large analytics on GCP; federated queries over GCS objects; marketing and product event pipelines landing in tables; teams already standardized on **[[dbt-core]]** against BigQuery.

**When to skip:** Primary OLTP (use **[[Postgres]]**). Multi-cloud strategy that forbids GCP-only warehouses. Small datasets where Postgres replicas plus **[[Grafana]]** or **[[Metabase]]** suffice.

**Key features:** Serverless scaling, nested and repeated fields, sharing and authorized views, scheduled queries, cost controls via quotas and reservations.


## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | GCP project and dataset IAM; no VMs to patch |
| **Cost** | Monitor bytes scanned; partition and cluster tables; use cached results |
| **BI** | First-class in **[[Metabase]]**, **[[Redash]]**, **[[Apache Superset]]** |

**Practices:** Separate dev and prod projects; avoid `SELECT *` on wide tables; load via batch or streaming with clear retention; pair with **[[Postgres]]** for transactional source of truth.

**References**

- [BigQuery documentation](https://cloud.google.com/bigquery/docs)
- [BigQuery pricing](https://cloud.google.com/bigquery/pricing)
