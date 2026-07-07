---
title: InfluxDB
date: '2026-06-12'
lastmod: '2026-07-02'
draft: false
keywords:
- InfluxDB
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - monitoring
---

[InfluxDB](https://www.influxdata.com/). Is a time-series database platform (InfluxDB 3 / IOx lineage) for metrics, events, and IoT-style telemetry.

## Summary

**What it is:** Columnar TSDB with SQL/InfluxQL/Flux query paths (version-dependent), retention policies, and Telegraf ingest.

**When to use:** Existing Influx estates; IoT or industrial telemetry already on Telegraf; Grafana dashboards over Influx.

**When to skip:** Standard Kubernetes app metrics without legacy Influx investment.

**Key features:** Buckets and retention, downsampling, InfluxDB Cloud Serverless, Telegraf plugin ecosystem.

## Details

| Topic | Notes |
|-------|--------|
| **Versions** | Confirm whether estate runs 1.x, 2.x, or 3.x; APIs differ |
| **Pairing** | Common **[[Grafana]]** datasource; compare with **[[Prometheus]]** for new services |

**References**

- [InfluxDB documentation](https://docs.influxdata.com/)
