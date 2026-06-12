---
title: "Backstage"
date: 2026-05-28
lastmod: 2026-06-12
draft: false

keywords:
  - Backstage

params:
  garden:
    kind: item
    usefulness: trial
    category: platform
    movement: "New"
aliases:
  - /radar/platforms/backstage
---

[Backstage](https://backstage.io/) is an open source developer portal framework from the [[CNCF]]. A centralized software catalog (`catalog-info.yaml`), scaffolder templates, and plugin ecosystem give teams one place to discover services, docs, and APIs. We **trial** it when building an **[[Internal Developer Platform]]** and want a self-hosted catalog plus golden-path templates.

## Blurb

> Backstage is an open source framework for building developer portals. Powered by a centralized software catalog, Backstage restores order to your microservices and infrastructure.

## Summary

**What it is:** React app plus backend plugins; entities (Component, System, API, Resource) declared in [[YAML]] and ingested from **[[git]]** repos.

**When to use:** [[microservice]] sprawl needs a service catalog; platform team can run and customize plugins; **Software Templates** for standardized repo bootstrap.

**When to skip:** single [[monorepo]] with no discovery problem; no staff to operate and upgrade the portal; SaaS [[IDP]] (Port, Cortex) fits procurement better.

**catalog-info.yaml:** each service repo carries metadata (owner, lifecycle, links to docs and CI) at repo root or path configured in the catalog importer.

## Details

| Topic | Notes |
|-------|--------|
| **Catalog** | Entity descriptors in YAML; processors merge from GitHub, GitLab, etc. |
| **Scaffolder** | Template `template.yaml` plus actions to create repos and **[[Kubernetes]]** resources |
| **Plugins** | TechDocs, Kubernetes, Argo CD, CI views (community and custom) |

**Practices:** treat Backstage as a product; assign owners; keep `catalog-info.yaml` in the same PR workflow as code changes.

**References**

- [Backstage documentation](https://backstage.io/docs/overview/what-is-backstage/)
- [Software catalog](https://backstage.io/docs/features/software-catalog/)
- [GitHub repository](https://github.com/backstage/backstage)
