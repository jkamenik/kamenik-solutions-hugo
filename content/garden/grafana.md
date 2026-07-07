---
title: Grafana
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- Grafana
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
    subcategories:
    - dashboarding
aliases:
- /radar/tools/grafana
---

[Grafana](https://grafana.com/oss/grafana/). Is the open and composable observability platform.

## Summary

**Garden stance:** We **trial** Grafana for our estate.

**Key points:** | Topic | Notes |
|-------|--------|
| **Deploy** | Single binary, Docker, Helm, or Grafana Cloud; separate scale paths for query frontends vs alert workers |
| **Data model** | Metrics-first; SQL and logs via datasource plugins, not a built-in warehouse |
| **Auth** | OAuth, SAML, RBAC; map teams to folder and datasource permissions |

**Practices:** Prefer Grafana OSS or self-hosted deploys when lock-in risk matters; keep dashboard JSON in git; label alert routes by severity. Avoid using Grafana as the only BI layer for finance or product analytics without a semantic layer elsewhere.

**References**

- [Grafana OSS](https://grafana.com/oss/grafana/)
- [GitHub repository](https://github.com/grafana/grafana)

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Single binary, Docker, Helm, or Grafana Cloud; separate scale paths for query frontends vs alert workers |
| **Data model** | Metrics-first; SQL and logs via datasource plugins, not a built-in warehouse |
| **Auth** | OAuth, SAML, RBAC; map teams to folder and datasource permissions |

**Practices:** Prefer Grafana OSS or self-hosted deploys when lock-in risk matters; keep dashboard JSON in git; label alert routes by severity. Avoid using Grafana as the only BI layer for finance or product analytics without a semantic layer elsewhere.

**References**

- [Grafana OSS](https://grafana.com/oss/grafana/)
- [GitHub repository](https://github.com/grafana/grafana)
