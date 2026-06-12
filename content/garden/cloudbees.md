---
title: "CloudBees"
date: 2024-04-06
lastmod: 2026-05-18
draft: false

keywords:
  - CloudBees

params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: "Moved Out"
    subcategories:
      - ci-cd-tools
aliases:
  - /radar/platforms/cloudbees
---

[CloudBees](https://www.cloudbees.com/) is the commercial steward of **[[Jenkins]]** and sells managed CI/CD (CloudBees CI, SaaS or self-managed controllers) plus enterprise orchestration (CloudBees CD, formerly ElectricFlow). We rate it **hold** with **Moved Out**: if you are not already on Jenkins, do not start here; if you are, treat CloudBees as containment while you plan exit to **[[GitHub Actions]]**, **[[ArgoCD]]**, or other **[[CI-CD Tools]]** in the garden.

## Blurb

> The Enterprise DevOps Leader. CloudBees powers DevOps with enterprise-grade Jenkins and DevSecOps.

## Summary

**What it is:** a vendor layer on top of the same Jenkins architecture (controllers, agents, plugins, Groovy pipelines) with support contracts, RBAC packaging, and compliance marketing. CloudBees employs many Jenkins maintainers; choosing CloudBees does not fix Jenkins's pet-server and credential-store problems described on **[[Jenkins]]**.

**When it appears:** legacy Java shops, regulated enterprises that standardized on Jenkins a decade ago, or acquisitions inheriting CloudBees CI estates.

**Why hold:** you inherit Jenkins operational risk (upgrade fragility, plugin supply chain, non-cattle controllers) plus commercial lock-in. Managed SaaS reduces toil but does not make Jenkins cloud-native or GitOps-aligned.

**Exit paths:** PR-based CI on **[[GitHub Actions]]**; K8s delivery via **[[ArgoCD]]** (build in Actions, sync in Argo); in-cluster workflows via **[[Argo Workflows]]** instead of **[[Jenkins X]]**.

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
