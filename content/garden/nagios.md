---
title: Nagios
date: '2023-07-23'
lastmod: '2026-07-02'
draft: false
keywords:
- Nagios
params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: No Change
    subcategories:
    - monitoring
---

[Nagios](https://www.nagios.org/). Is a long-running open source monitoring system built around host and service checks with plugin scripts.

## Blurb

> Prevent IT downtime before it impacts your systems with Nagios Core - the free, open source monitoring solution trusted by 1M+ users worldwide. Monitor severs, networks & applications with powerful community-driven tools.

## Summary

**What it is:** Core scheduling engine, check plugins, notification commands, and optional Nagios XI commercial UI. The model is periodic synthetic checks from a central poller.

**When to use:** Maintaining an existing Nagios deployment with years of custom plugins and on-call docs. Short-term bridge while migrating checks to Prometheus exporters or OTel.

**When to skip:** Any greenfield monitoring project. Plugin sprawl, config drift, and host-centric alerting do not scale cleanly for ephemeral cloud workloads.

**Key features:** Flexible plugins, escalation chains, downtime scheduling, and a large community check library.

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Central server, NRPE or remote plugins, flat config files or Nagios XI config UI |
| **Data model** | Host and service objects with hard/soft states; not a metrics time-series store |
| **Auth** | Basic UI auth; enterprise features in Nagios XI |

**Practices:** Plan exit early if you inherit Nagios. Export check intent as code, then reimplement as OTel metrics or synthetic probes in **[[Grafana]]** alerting.

**References**

- [Nagios Core documentation](https://www.nagios.org/documentation/)
- [Nagios plugins](https://www.nagios.org/projects/nagios-plugins/)
