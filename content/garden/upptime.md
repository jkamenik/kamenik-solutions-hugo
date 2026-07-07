---
title: Upptime
date: '2023-07-23'
lastmod: '2026-07-02'
draft: false
keywords:
- Upptime
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - monitoring
---

[Upptime](https://github.com/upptime/upptime). Is an open source uptime monitor that runs on **[[GitHub Actions]]** and stores status in the repo itself.

## Summary

**Garden stance:** We **assess** Upptime for our estate.

**Key points:** | Topic | Notes |
|-------|--------|
| **Deploy** | Fork template repo, enable Actions and Pages, configure targets in config YAML |
| **Data model** | Commit history and issues as the incident record; graphs generated in-repo |
| **Auth** | Public probes only; secrets limited to GitHub token scopes for Actions |

**Practices:** Useful as a reference pattern for "monitoring as code" on GitHub. Pair with real **[[Grafana]]** alerting when downtime must wake an on-call rotation.

**References**

- [Upptime repository](https://github.com/upptime/upptime)
- [Upptime documentation](https://upptime.js.org/docs/)

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Fork template repo, enable Actions and Pages, configure targets in config YAML |
| **Data model** | Commit history and issues as the incident record; graphs generated in-repo |
| **Auth** | Public probes only; secrets limited to GitHub token scopes for Actions |

**Practices:** Useful as a reference pattern for "monitoring as code" on GitHub. Pair with real **[[Grafana]]** alerting when downtime must wake an on-call rotation.

**References**

- [Upptime repository](https://github.com/upptime/upptime)
- [Upptime documentation](https://upptime.js.org/docs/)
