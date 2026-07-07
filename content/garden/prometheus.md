---
title: Prometheus
date: '2026-06-12'
lastmod: '2026-07-02'
draft: false
keywords:
- Prometheus
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
    subcategories:
    - monitoring
---

[Prometheus](https://prometheus.io/). Is the CNCF metrics database and scraper ecosystem for time-series monitoring and alerting.

## Blurb

> An open-source monitoring system with a dimensional data model, flexible query language, efficient time series database and modern alerting approach.

## Summary

**What it is:** Pull-based scraper, TSDB storage, PromQL, alert rules, and federation patterns for Kubernetes and services.

**When to use:** Cloud-native metrics with **[[Grafana]]** dashboards; kube-prometheus-stack style deployments.

**When to skip:** Long-term log archival (use **[[Loki]]** or **[[Elasticsearch]]**). Vendor SaaS mandate (**[[Datadog]]**).

**Key features:** Service discovery, recording rules, Alertmanager routing, remote write/read integrations.

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Single binary, Operator on **[[Kubernetes]]**, or managed compatible (Mimir, Cortex, AMP) |
| **Pairing** | **[[OpenTelemetry]]** metrics pipeline can remote-write into Prometheus-compatible stores |

**References**

- [Prometheus documentation](https://prometheus.io/docs/)
