---
title: "Upptime"
date: 2023-07-23
lastmod: 2026-06-12
draft: false

keywords:
  - Upptime

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "No Change"
    subcategories:
      - monitoring
---

[Upptime](https://github.com/upptime/upptime) is an open source uptime monitor that runs on **[[GitHub Actions]]** and stores status in the repo itself. It probes public HTTP endpoints on a schedule and publishes a status page from GitHub Pages. We **assess** it for lightweight public uptime checks, not as a replacement for full **[[Grafana]]** or synthetic monitoring at scale.

## Blurb

> Upptime is the open-source uptime monitor and status page, powered entirely by GitHub Actions.

## Summary

**What it is:** Forkable GitHub repo template with workflow YAML, issue-based incident log, and a static status site. No servers to run beyond GitHub-hosted runners.

**When to use:** Open source projects or small sites that need a public status page with minimal cost. Teams already standardized on **[[GitHub Actions]]** who want uptime as code in git.

**When to skip:** Private endpoints, complex auth flows, multi-region SLO tracking, or on-call paging. Prefer **[[Grafana]]** Cloud, Prometheus blackbox exporters, or vendor synthetics for production SRE workflows.

**Key features:** Scheduled pings, response-time graphs in the repo, automatic issues on downtime, and GitHub Pages status UI.

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
