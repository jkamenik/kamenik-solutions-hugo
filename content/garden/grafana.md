---
title: "Grafana"
date: 2026-05-28
lastmod: 2026-06-12
draft: false

keywords:
  - Grafana

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "No Change"
    subcategories:
      - dashboarding
aliases:
  - /radar/tools/grafana
---

[Grafana](https://grafana.com/oss/grafana/) is the open and composable observability platform. It queries, visualizes, and alerts on metrics, logs, and traces from many datasources in one place. We **trial** it as the default pane of glass for SRE and platform teams. Reach for it first when you want open standards and swap-friendly backends instead of a proprietary-only observability stack.

## Blurb

> Grafana allows you to query, visualize, alert on, and understand your metrics no matter where they are stored. Create, explore, and share beautiful dashboards with your team and foster a data-driven culture.

## Summary

**What it is:** Open source dashboard and alerting stack (Grafana [[OSS]]) plus a large plugin ecosystem. Connects to [[Prometheus]], [[Loki]], [[Elasticsearch]], [[InfluxDB]], [[Postgres]], cloud vendor APIs, and hundreds of other backends without forcing a single ingest pipeline.

**When to use:** Default observability UI to limit vendor lock-in: query in place, mix Prometheus, Loki, cloud APIs, and SQL without a mandatory ingest vendor. Unified monitoring for infra and apps; on-call alert routing; Explore workflows for metrics-to-logs drilldown.

**When to skip:** Primary need is governed warehouse BI with semantic layers and self-serve SQL for business users. Prefer **[[Metabase]]**, **[[Apache Superset]]**, or **[[Redash]]** for analyst-centric SQL dashboards. Pair Grafana with those tools rather than stretching it into full BI.

**Key features:** Panel plugins and templated variables, unified alerting, role-based access, correlations across signals, optional Grafana Cloud or enterprise extensions.

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Single binary, Docker, Helm, or Grafana Cloud; separate scale paths for query frontends vs alert workers |
| **Data model** | Metrics-first; SQL and logs via datasource plugins, not a built-in warehouse |
| **Auth** | OAuth, SAML, RBAC; map teams to folder and datasource permissions |

**Practices:** Prefer Grafana OSS or self-hosted deploys when lock-in risk matters; keep dashboard JSON in git; label alert routes by severity. Avoid using Grafana as the only BI layer for finance or product analytics without a semantic layer elsewhere.

**References**

- [Grafana OSS](https://grafana.com/oss/grafana/)
- [GitHub repository](https://github.com/grafana/grafana)
