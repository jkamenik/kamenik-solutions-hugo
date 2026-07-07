---
title: Zabbix
date: '2023-07-23'
lastmod: '2026-07-02'
draft: false
keywords:
- Zabbix
params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: No Change
    subcategories:
    - monitoring
---

[Zabbix](https://www.zabbix.com/). Is an enterprise-class open source monitoring platform for hosts, networks, applications, and services.

## Blurb

> Zabbix is an enterprise-class, open-source monitoring solution that makes network and application monitoring simple.

## Summary

**What it is:** Server, agents or agentless checks, web frontend, alerting, and reporting over a central metadata database. Strong at SNMP, classic server metrics, and all-in-one ops teams that want one box.

**When to use:** Existing Zabbix estate with templates and on-call runbooks already paid for. Heavy SNMP network and datacenter monitoring where migration cost dominates.

**When to skip:** New SaaS or Kubernetes platforms where hosts are fungible and service-level signals matter more than per-host ping checks. Prefer **[[Grafana]]** with Prometheus, Loki, or cloud APIs, instrumented via **[[OpenTelemetry]]**.

**Key features:** Triggers and escalations, discovery, maps, SLA reporting, distributed proxies, and a large template library.

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Server plus DB (MySQL/Postgres/TimescaleDB), agents on hosts, optional proxies at the edge |
| **Data model** | Host-centric items, triggers, and graphs; service maps added over time but mindset stays host-first |
| **Auth** | Role-based UI access; LDAP and SSO in commercial tiers |

**Practices:** Treat Zabbix as legacy carry-forward, not the default observability stack. If you keep it, isolate read-only monitoring networks and cap alert noise with maintenance windows.

**References**

- [Zabbix documentation](https://www.zabbix.com/documentation/current/en/manual)
- [Zabbix source](https://github.com/zabbix/zabbix)
