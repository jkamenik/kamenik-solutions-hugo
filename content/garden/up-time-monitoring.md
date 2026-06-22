---
title: "Up-time Monitoring"
date: 2024-10-01
lastmod: 2026-06-22
draft: false

keywords:
  - Up-time Monitoring
  - Uptime Monitoring

params:
  aliases:
    - Uptime Monitoring
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"
---

[Up-time Monitoring](https://en.wikipedia.org/wiki/Uptime)

Up-time monitoring measures whether a system is reachable and behaving acceptably from a user's perspective. Raw uptime percentage is a lagging summary; we **adopt** measuring the underlying SLIs (latency, errors, saturation) via **[[OpenTelemetry]]** and **[[Monitoring]]** tools, then derive uptime for **[[SLAs]]** and **[[Incident Management]]**.

## Blurb

> Uptime is a measure of system reliability, expressed as the percentage of time a service is available.

## Summary

**What it is:** Synthetic probes, RUM, and SLO-based alerts that answer "can customers use the product?" rather than "is the host up?"

**When to use:** Public services with **[[SLAs]]**; status pages (**[[Upptime]]**); synthetic checks (**[[Grafana k6]]**, **[[Kuberhealthy]]**) complementing metrics.

**When to skip:** Batch-only internal jobs with no user-facing window (monitor job success instead).

**Practices:** Define SLOs on user journeys; avoid host-only ping alerts in cloud-native estates; page on burn rate, not single blips.


## Details

| Approach | Garden items |
|----------|----------------|
| Public status | **[[Upptime]]** on **[[GitHub Actions]]** |
| Load / synthetics | **[[Grafana k6]]** |
| In-cluster checks | **[[Kuberhealthy]]** |
| Metrics + SLOs | **[[Prometheus]]**, **[[Grafana]]**, **[[OpenTelemetry]]** |
