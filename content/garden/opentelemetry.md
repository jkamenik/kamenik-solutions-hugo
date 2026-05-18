---
title: "OpenTelemetry"
date: 2025-12-08
lastmod: 2026-05-17
draft: false

keywords:
  - OpenTelemetry

params:
  garden:
    kind: item
    usefulness: adopt
    category: code
    movement: "No Change"
    subcategories:
      - library

aliases:
  - /radar/code/opentelemetry
---

[OpenTelemetry](https://opentelemetry.io/) (OTel) is the CNCF-standard way to collect **traces**, **metrics**, and **logs** with vendor-neutral APIs and SDKs. Instrument once, export to your backend of choice (Prometheus, Jaeger, vendor SaaS, etc.) instead of locking into a proprietary agent. For new services and platforms we treat OTel as the default observability foundation, it is what makes [[Incident Management]] detection and [[Up-time Monitoring]] actually work in modern, ephemeral infrastructure.

## Blurb

> High-quality, ubiquitous, and portable telemetry to enable effective observability.

## Summary

OTel defines semantic conventions, context propagation, and collectors so telemetry is consistent across languages and runtimes. Most teams start with auto-instrumentation or lightweight SDK hooks, run the OpenTelemetry Collector for routing and redaction, then wire exporters to existing analysis tools.

## Details

- **Signals:** traces (distributed requests), metrics (aggregates), logs (events), often correlated via shared trace context.
- **Neutrality:** avoids the "three proprietary agents" problem; switching vendors should not require re-instrumenting applications.
- **Collector:** optional pipeline for batching, sampling, PII scrubbing, and fan-out to multiple backends.
- **Maturity:** widely supported in [[Kubernetes]] workloads, [[GoLang]], Java, .NET, Python, and major cloud APM products.
