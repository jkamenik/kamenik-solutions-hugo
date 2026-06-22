---
title: "Elasticsearch"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Elasticsearch

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - monitoring
---

[Elasticsearch](https://www.elastic.co/elasticsearch) is a distributed search and analytics engine used for logs, metrics, and full-text search. In observability it often backs **[[Kibana]]** dashboards or Grafana Elasticsearch datasources. We **assess** it when Elastic is already standard; otherwise prefer **[[Loki]]** plus **[[Prometheus]]** with **[[Grafana]]**.

## Blurb

> Elasticsearch is a distributed, free and open search and analytics engine for all types of data.

## Summary

**What it is:** JSON document store with inverted indexes, aggregations, and cluster scaling via shards and replicas.

**When to use:** Unified search plus observability on Elastic Stack; security analytics with Elastic SIEM modules.

**When to skip:** Greenfield LGTM stack without Elastic licensing. Small teams avoiding JVM cluster ops.

**Key features:** Index lifecycle management, ingest pipelines, cross-cluster search, Elastic Cloud managed option.


## Details

| Topic | Notes |
|-------|--------|
| **UI** | **[[Kibana]]** for native dashboards; **[[Grafana]]** can query Elasticsearch as a datasource |
| **Ops** | Plan shard sizing, hot/warm tiers, and retention ILM policies early |

**References**

- [Elasticsearch documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html)
