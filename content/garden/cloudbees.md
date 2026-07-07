---
title: CloudBees
date: '2024-04-06'
lastmod: '2026-07-02'
draft: false
keywords:
- CloudBees
params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: Moved Out
    subcategories:
    - ci-cd-tools
aliases:
- /radar/platforms/cloudbees
---

[CloudBees](https://www.cloudbees.com/). Is the commercial steward of **[[Jenkins]]** and sells managed CI/CD (CloudBees CI, SaaS or self-managed controllers) plus enterprise orchestration (CloudBees CD, formerly ElectricFlow).

## Blurb

> CloudBees Unify is the enterprise control and context plane for your entire AI-powered software delivery lifecycle: open, multi-agentic, and continuously secure.

## Summary

**Garden stance:** We **hold** CloudBees for our estate.

**Key points:** | Topic | Notes |
|-------|--------|
| **CloudBees CI** | Managed or self-hosted Jenkins; same pipeline model as OSS |
| **CloudBees CD** | Release orchestration product; separate from Jenkins but same "hold unless sunk" rule |
| **Secrets** | Do not rely on Jenkins credential stores; use **[[HashiCorp Vault]]** or cloud secret managers |
| **Security** | Align with **[[DevSecOps]]** gates on the PR path; do not treat the controller as trusted for production deploy keys |
| **Greenfield** | Default to **adopt** tools in **[[CI-CD Tools]]** (Actions + Argo CD pattern), not CloudBees net-new |

**If you must stay:** single controller strategy, pinned plugins, infrastructure as code for controller config, no production deploy credentials on Jenkins, DR drills that assume rebuild-not-restore.

**References**

- [CloudBees](https://www.cloudbees.com/)
- See **[[Jenkins]]** for OSS-specific warnings

## Details

| Topic | Notes |
|-------|--------|
| **CloudBees CI** | Managed or self-hosted Jenkins; same pipeline model as OSS |
| **CloudBees CD** | Release orchestration product; separate from Jenkins but same "hold unless sunk" rule |
| **Secrets** | Do not rely on Jenkins credential stores; use **[[HashiCorp Vault]]** or cloud secret managers |
| **Security** | Align with **[[DevSecOps]]** gates on the PR path; do not treat the controller as trusted for production deploy keys |
| **Greenfield** | Default to **adopt** tools in **[[CI-CD Tools]]** (Actions + Argo CD pattern), not CloudBees net-new |

**If you must stay:** single controller strategy, pinned plugins, infrastructure as code for controller config, no production deploy credentials on Jenkins, DR drills that assume rebuild-not-restore.

**References**

- [CloudBees](https://www.cloudbees.com/)
- See **[[Jenkins]]** for OSS-specific warnings
