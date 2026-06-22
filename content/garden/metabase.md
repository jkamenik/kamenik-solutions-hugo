---
title: "Metabase"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - Metabase

params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: "No Change"
    subcategories:
      - dashboarding
aliases:
  - /radar/tools/metabase
---

[Metabase](https://www.metabase.com/) is open source business intelligence and embedded analytics. For the open source or self-hosted route, we **hold** it: **[[Grafana]]** is the better default to limit vendor lock-in on observability and lighter analytics. Metabase Cloud SaaS can still fit when data is spread across many systems and a managed BI layer beats running another platform yourself. Do not start new OSS Metabase deployments when Grafana already serves the team.

## Blurb

> Metabase is the easy, open-source way for everyone in your company to ask questions and learn from data.

## Summary

**What it is:** Web app plus Metabase Cloud (SaaS). Visual query builder, native SQL editor, dashboards, pulses, and embedding APIs. Open Source (AGPL) and commercial editions share one codebase.

**When to use (SaaS):** Data spread across many databases or clouds; want managed hosting, upgrades, and support without operating BI infra; embedded analytics for customers with a vendor-run control plane.

**When to skip (OSS):** Greenfield self-hosted BI when **[[Grafana]]** (trial) already covers metrics and enough SQL-backed panels. Prefer **[[Apache Superset]]** for large semantic layers or **[[Redash]]** for engineer-first SQL sharing.

**Hold (OSS):** Existing self-hosted Metabase is acceptable. New open source rollouts should default to Grafana unless requirements are explicitly warehouse-centric BI that Grafana cannot cover.

**Key features:** No-code questions, drill-through, collections and permissions, optional AI assistant (Metabot), Docker or JAR deploy in minutes.


## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | **Hold path:** Docker/JAR self-hosted (prefer **[[Grafana]]** OSS instead for new work). **SaaS path:** Metabase Cloud when federated data or ops cost dominates |
| **Data model** | Live queries against connected databases; extracts optional via caching settings |
| **Auth** | Google, LDAP, SAML; row-level sandboxing on supported plans |

**Practices:** Use read-only DB credentials; separate analytics replicas from OLTP; audit public links and embedded iframe origins.

**References**

- [Metabase documentation](https://www.metabase.com/docs/latest/)
- [GitHub repository](https://github.com/metabase/metabase)
