---
title: Honeycomb
date: '2026-06-12'
lastmod: '2026-07-02'
draft: false
keywords:
- Honeycomb
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - monitoring
---

[Honeycomb](https://www.honeycomb.io/). Is an observability platform optimized for high-cardinality event data and fast iterative debugging.

## Blurb

> Honeycomb is the observability platform built for AI-era software. Fast queries, unified telemetry, and LLM observability. Used by Slack, Intercom, and Dropbox.

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
