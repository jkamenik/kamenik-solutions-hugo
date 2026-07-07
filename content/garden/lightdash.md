---
title: Lightdash
date: '2026-06-12'
lastmod: '2026-07-02'
draft: false
keywords:
- Lightdash
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - dashboarding
---

[Lightdash](https://www.lightdash.com/). Is an open source BI layer that turns **[[dbt-core]]** models into explorable metrics and dashboards.

## Blurb

> Lightdash is the AI-first, open-source BI platform for modern data teams. Connect to dbt, define metrics once, and get instant, trustworthy insights.

## Summary

**What it is:** Web app plus CLI that syncs dbt `schema.yml` metrics and dimensions into self-serve charts and dashboards.

**When to use:** Warehouse analytics owned by dbt; want OSS BI without rebuilding metrics in **[[Metabase]]** or **[[Apache Superset]]**.

**When to skip:** No dbt discipline in the warehouse. Prefer **[[Redash]]** for ad hoc SQL only.

**Key features:** dbt-native metrics, Git-backed definitions, Slack/email alerts on charts, optional Lightdash Cloud.

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Docker or Lightdash Cloud; connects to warehouse dbt already targets |
| **Fit** | Pairs with **[[dbt-core]]** and **[[BigQuery]]**, **[[Snowflake]]**, or **[[Postgres]]** |

**References**

- [Lightdash documentation](https://docs.lightdash.com/)
