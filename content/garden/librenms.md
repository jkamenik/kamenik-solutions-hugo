---
title: "LibreNMS"
date: 2024-10-01
lastmod: 2026-06-22
draft: false

keywords:
  - LibreNMS

params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: "No Change"
    subcategories:
      - monitoring
---

[LibreNMS](https://www.librenms.org/) is an open source network monitoring system focused on SNMP discovery, device health, and alerting for switches, routers, and firewalls. It ships auto-discovery, billing hooks, and a web dashboard out of the box. We **hold** new deployments: it fits SNMP-heavy network closets, but **[[Grafana]]** with modern exporters is the default for broader observability.

## Blurb

> LibreNMS is an autodiscovering PHP/MySQL/SNMP based network monitoring which includes support for a wide range of network hardware and operating systems.

## Summary

**What it is:** PHP application with MySQL/MariaDB backend, polling via SNMP, and a device-centric UI for ports, sensors, and wireless links.

**When to use:** Existing LibreNMS install with device credentials and port maps already tuned. Dedicated network ops team that lives in SNMP OIDs and needs minimal setup for common vendors.

**When to skip:** Greenfield monitoring where apps and infra share one observability plane. Prefer Prometheus node/snmp exporters plus **[[Grafana]]**, or cloud-native network telemetry when available.

**Key features:** Auto-discovery, alerting rules, API, billing reports, and distributed pollers for large networks.


## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Web server, database, cron/poller workers; optional distributed pollers per site |
| **Data model** | Device and port inventory from SNMP; graphs and alerts per entity |
| **Auth** | Local users, LDAP, and API tokens |

**Practices:** Treat as a niche network tool, not the company-wide monitoring platform. Keep SNMP read-only communities scoped and document vendor MIB gaps before relying on alerts.

**References**

- [LibreNMS documentation](https://docs.librenms.org/)
- [GitHub repository](https://github.com/librenms/librenms)
