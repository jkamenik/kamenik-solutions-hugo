---
title: Datadog
date: '2026-06-12'
lastmod: '2026-07-02'
draft: false
keywords:
- Datadog
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - monitoring
---

[Datadog](https://www.datadoghq.com/). Is a SaaS observability platform for metrics, logs, traces, RUM, and security signals in one vendor UI.

## Blurb

> See metrics from all of your apps, tools & services in one place with Datadog’s cloud monitoring as a service solution. Try it for free.

## Summary

**What it is:** Agents and API ingest for infrastructure, APM, logs, synthetics, and dashboards with alerting and incident workflows.

**When to use:** Procurement favors single-vendor observability; SRE team lacks capacity to run Prometheus/Loki stacks.

**When to skip:** Strict data-sovereignty or multi-cloud neutrality goals. Prefer **[[OpenTelemetry]]** export to self-hosted **[[Grafana]]**.

**Key features:** Unified host and container maps, APM service maps, log patterns, monitors, SLO tracking, marketplace integrations.

## Details

| Topic | Notes |
|-------|--------|
| **Fit** | **[[Monitoring]]** SaaS with strong **[[Dashboarding]]** UI; not a warehouse BI tool |
| **Contrast** | **[[Splunk]]** for log-centric SIEM estates; **[[Honeycomb]]** for high-cardinality event analysis |

**References**

- [Datadog documentation](https://docs.datadoghq.com/)
