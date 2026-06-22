---
title: "Preset"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - Preset

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - dashboarding
---

[Preset](https://preset.io/) is a managed **[[Apache Superset]]** platform from Superset's original creators. It hosts Superset, handles upgrades, and adds workspace collaboration on top of the OSS BI engine. We **assess** it when Superset fits but self-hosting ops do not.

## Blurb

> Preset is Apache Superset as a service. Build and share data dashboards with your team.

## Summary

**What it is:** SaaS control plane and hosting for Superset instances with SSO, permissions, and managed releases.

**When to use:** Superset feature set is the goal; team wants managed uptime and faster onboarding vs DIY Helm.

**When to skip:** Strict data residency that forbids third-party BI SaaS. Self-host **[[Apache Superset]]** or assess **[[Lightdash]]** with **[[dbt-core]]** instead.

**Key features:** Managed Superset, API access, role-based workspaces, changelog parity with upstream Apache releases.


## Details

| Topic | Notes |
|-------|--------|
| **Relationship** | Commercial layer on **[[Apache Superset]]**; same chart and dataset concepts |
| **Contrast** | **[[Metabase]]** Cloud for simpler self-serve; **[[Redash]]** for SQL-first minimal BI |

**References**

- [Preset documentation](https://docs.preset.io/)
