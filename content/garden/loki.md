---
title: "Loki"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Loki

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
    subcategories:
      - monitoring
---

[Loki](https://grafana.com/oss/loki/) is Grafana Labs' horizontally scalable log aggregation system inspired by **[[Prometheus]]** labels. It indexes metadata, not full log text, and pairs with **[[Grafana]]** for log exploration. We **trial** it for Kubernetes and service logs alongside Prometheus metrics.

## Blurb

> Loki is a horizontally-scalable, highly-available, multi-tenant log aggregation system inspired by Prometheus.

## Summary

**What it is:** Log ingest (Promtail, Alloy, or OTel), label-based indexing, LogQL queries in Grafana.

**When to use:** Grafana-centric observability stack; cost-aware log retention with object storage backends.

**When to skip:** Full-text SIEM requirements (**[[Splunk]]**, **[[Elasticsearch]]**). Teams without label discipline on logs.

**Key features:** LogQL, multi-tenancy, boltdb/TSDB schema evolution, Grafana correlations with metrics and traces.


## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Helm on **[[Kubernetes]]**; microservices or simple scalable modes |
| **Pairing** | Default companion to **[[Prometheus]]** and **[[Grafana]]** in LGTM stacks |

**References**

- [Loki documentation](https://grafana.com/docs/loki/latest/)
