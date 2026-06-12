---
title: "Jaeger"
date: 2026-06-12
lastmod: 2026-06-12
draft: false

keywords:
  - Jaeger

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - monitoring
---

[Jaeger](https://www.jaegertracing.io/) is an open source distributed tracing backend and UI, originally from Uber and now a CNCF graduated project. It accepts **[[OpenTelemetry]]** trace exports for request-flow debugging. We **assess** it for OSS trace storage; many teams also view traces in **[[Grafana]]** Tempo instead.

## Blurb

> Jaeger is an open-source end-to-end distributed tracing platform.

## Summary

**What it is:** Collectors, storage (Cassandra, Elasticsearch, Badger, etc.), query service, and Jaeger UI for trace search.

**When to use:** Need self-hosted tracing without Tempo; existing Jaeger instrumentation or OTel pipelines.

**When to skip:** Grafana-all-in-one stack already standardized on Tempo. SaaS trace analytics (**[[Honeycomb]]**, **[[Datadog]]**).

**Key features:** Service dependency graphs, adaptive sampling, OTLP ingest, operator deployment on **[[Kubernetes]]**.

## Details

| Topic | Notes |
|-------|--------|
| **Pairing** | Instrument with **[[OpenTelemetry]]** SDKs; export OTLP to Jaeger collectors |
| **Storage** | Plan retention and index backend cost for high-QPS services |

**References**

- [Jaeger documentation](https://www.jaegertracing.io/docs/)
