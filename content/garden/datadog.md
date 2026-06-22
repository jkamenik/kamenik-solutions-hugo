---
title: "Datadog"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Datadog

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - monitoring
---

[Datadog](https://www.datadoghq.com/) is a SaaS observability platform for metrics, logs, traces, RUM, and security signals in one vendor UI. We **assess** it for teams that want a managed pane without operating **[[Grafana]]** and multiple backends; default greenfield remains OTel plus **[[Grafana]]** to limit lock-in.

## Blurb

> Datadog is the essential monitoring and security platform for cloud applications.

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
