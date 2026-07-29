---
title: Datadog
date: '2026-06-12'
lastmod: '2026-07-29'
draft: false
keywords:
- Datadog
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
    subcategories:
    - monitoring
---

[Datadog](https://www.datadoghq.com/) is a SaaS observability and security platform for metrics, logs, traces, RUM, and security signals in one vendor UI. We **trial** it for multi-cloud and hybrid estates when native **[[AWS]]** or **[[Azure]]** monitoring falls short.

## Blurb

> Datadog is the leading observability and security platform for the AI era, providing businesses with unified visibility across the technology stack to manage complexity at scale.

## Summary

**What it is:** Agents and API ingest for infrastructure, APM, logs, synthetics, GPU monitoring, and dashboards with alerting and incident workflows. Bits AI agents investigate and remediate inside the same console.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Multi-cloud or hybrid | One pane across clouds beats stitching native consoles |
| **[[AWS]]** or **[[Azure]]** estates | Native monitoring is often too thin for serious ops |
| Forced vendor consolidation | Marketplace integrations and FedRAMP-ready SaaS |

**When to skip:**

- Fully on **[[Google Cloud Platform|GCP]]**, where the native stack is usually good enough
- Hard data-sovereignty rules that block SaaS ingest

**Trade-offs:** Fast time-to-value and broad product surface; pricing expands with products and volume. Homegrown **[[Grafana]]** + **[[Loki]]** + **[[Prometheus]]** + **[[OpenTelemetry]]** stacks rarely stay cheaper. Budget pressure often strips them until they stop working.

## Details

| Topic | Notes |
|-------|--------|
| **Fit** | **[[Monitoring]]** SaaS with strong **[[Dashboarding]]** UI; not a warehouse BI tool |
| **Cloud natives** | Prefer GCP native when GCP-only; choose Datadog for AWS, Azure, multi-cloud, or hybrid |
| **DIY OSS** | **[[Grafana]]** / **[[Loki]]** / **[[Prometheus]]** / **[[OpenTelemetry]]** look cheaper on paper; underfunded builds usually fail |
| **Contrast** | **[[Splunk]]** for log-centric SIEM; **[[Honeycomb]]** for high-cardinality events |
| **AI surface** | Bits AI agents, MCP Server for IDE/agent access, GPU Monitoring |

**References**

- [Datadog documentation](https://docs.datadoghq.com/)
- [Investor relations](https://investors.datadoghq.com/)
