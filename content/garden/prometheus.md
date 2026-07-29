---
title: Prometheus
date: '2026-06-12'
lastmod: '2026-07-29'
draft: false
keywords:
- Prometheus
params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: Moved Out
    subcategories:
    - monitoring
---

[Prometheus](https://prometheus.io/) is the CNCF metrics database and scraper ecosystem for time-series monitoring and alerting. We **hold** it for new work: custom metrics effort belongs in **[[OpenTelemetry]]**, and self-hosted Prom stacks rarely stay correct or used.

## Blurb

> An open-source monitoring system with a dimensional data model, flexible query language, efficient time series database and modern alerting approach.

## Summary

**What it is:** Pull-based scraper, TSDB storage, PromQL, alert rules, and federation patterns for Kubernetes and services. Still fine as a storage/query target behind an OTel pipeline.

**When to use (existing only):**

| Situation | Notes |
|-----------|--------|
| Inherited kube-prometheus-stack | Keep running; do not expand custom Prom client metrics |
| Prom-compatible remote store | Accept remote write from **[[OpenTelemetry]]** Collector |

**When to skip (new work):**

- Greenfield metrics: instrument with **[[OpenTelemetry]]**, not Prometheus client libraries as the primary model
- Multi-cloud / hybrid estates: prefer **[[Datadog]]** (**trial**) over a DIY Prom + **[[Grafana]]** stack
- Long-term log archival: **[[Loki]]** or **[[Elasticsearch]]**, not Prometheus

**Trade-offs:** "Just enough" scrape-and-PromQL is attractive early. Teams usually mis-model metrics and under-use what they collect. Time spent on custom metrics is better spent on OTel conventions and exporters.

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Single binary, Operator on **[[Kubernetes]]**, or managed compatible (Mimir, Cortex, AMP) |
| **Pairing** | Prefer **[[OpenTelemetry]]** for instrumentation; remote-write into Prometheus-compatible stores if needed |
| **Successor path** | New custom metrics → OTel; multi-cloud ops → **[[Datadog]]**; dashboards may still use **[[Grafana]]** |

**References**

- [Prometheus documentation](https://prometheus.io/docs/)
