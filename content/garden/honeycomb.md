---
title: "Honeycomb"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Honeycomb

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - monitoring
---

[Honeycomb](https://www.honeycomb.io/) is an observability platform optimized for high-cardinality event data and fast iterative debugging. It ingests OpenTelemetry and structured events for BubbleUp and query-driven investigation. We **assess** it for complex distributed systems debugging; baseline metrics stacks remain **[[Prometheus]]** plus **[[Grafana]]**.

## Blurb

> Honeycomb helps engineers debug production systems with high-cardinality observability data.

## Summary

**What it is:** Event store and UI for wide events, traces, and metrics with fast filters across many dimensions.

**When to use:** Microservices with rich attributes; teams outgrow pre-aggregated metric dashboards for incident triage.

**When to skip:** Small teams with simple RED metrics needs. Cost-sensitive estates without event-volume discipline.

**Key features:** BubbleUp diffs, Service Level Objectives, OpenTelemetry ingest, boards (dashboard-like views).


## Details

| Topic | Notes |
|-------|--------|
| **Fit** | **[[Monitoring]]** with exploratory UI; pairs with **[[OpenTelemetry]]** instrumentation |
| **Contrast** | **[[Datadog]]** for full-suite SaaS; **[[Jaeger]]** for OSS trace-only backends |

**References**

- [Honeycomb documentation](https://docs.honeycomb.io/)
