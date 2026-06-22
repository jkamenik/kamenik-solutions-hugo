---
title: "Splunk"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Splunk

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - monitoring
---

[Splunk](https://www.splunk.com/) is an enterprise log analytics and SIEM platform for search, dashboards, and security operations at large event volume. We **assess** it for regulated estates already invested in Splunk; greenfield log stacks favor **[[Loki]]** or **[[Elasticsearch]]** with **[[Grafana]]** or **[[Kibana]]**.

## Blurb

> Splunk helps organizations use data to do more.

## Summary

**What it is:** Indexer/search head architecture (Splunk Enterprise/Cloud) for SPL queries, reports, alerts, and SOAR-adjacent workflows.

**When to use:** Existing Splunk license and skill base; compliance mandates centralized log retention and SIEM.

**When to skip:** Startup-scale cost and ops overhead. Prefer OTel collectors feeding **[[OpenTelemetry]]**-friendly backends.

**Key features:** SPL, apps marketplace, HEC ingest, role-based knowledge objects, ITSI and ES modules (commercial).


## Details

| Topic | Notes |
|-------|--------|
| **Fit** | **[[Monitoring]]** / security analytics; dashboards are a feature, not standalone BI |
| **Contrast** | **[[Elasticsearch]]** + **[[Kibana]]** for OSS/elastic alternative |

**References**

- [Splunk documentation](https://docs.splunk.com/)
