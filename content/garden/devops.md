---
title: "DevOps"
date: 2024-04-09
lastmod: 2026-06-12
draft: false

keywords:
  - DevOps
  - Dev Ops

params:
  aliases:
    - Dev Ops
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"
aliases:
  - /radar/techniques/devops
---

[DevOps](https://en.wikipedia.org/wiki/DevOps) is a **culture and practice** that breaks the wall between development and operations: ship small changes often, automate the path to production, and measure outcomes. We **adopt** it as the default delivery philosophy; implement it with **[[Agile Software Development]]**, **[[Shift Left]]**, and the CI/CD techniques in this garden.

## Blurb

> DevOps is a set of practices that combines software development and IT operations to shorten the systems development life cycle and provide continuous delivery with high software quality.

## Summary

**What it means in practice:**

| Theme | Garden expression |
|-------|-------------------|
| **Flow** | **[[Continuous Integration]]** + **[[Continuous Delivery]]** on every merge |
| **Automation** | **[[CI-CD Tools]]** (**[[GitHub Actions]]**, **[[ArgoCD]]**); **[[Declarative IaC]]** |
| **Collaboration** | **[[Pull Request]]** + **[[Code Review]]**; ops in design, dev on-call |
| **Feedback** | Metrics, logs, postmortems; **[[Cattle Not Pets]]** |
| **Improvement** | Blameless retros; shrink batch size |

![Wikipedia DevOps toolchain](https://upload.wikimedia.org/wikipedia/commons/0/05/Devops-toolchain.svg)

**Plan → code → build → test → release → deploy → operate → monitor** maps to concrete gates: lint/tests on the PR, signed artifacts, promoted deploys, observability in prod.

**[[Shift Left]]** is how we describe moving quality, security, and ops checks earlier (same PR, same pipeline).

**[[GitOps]]** is our preferred *apply* model: Git is the source of truth; merge triggers reconcile (infra and cluster).

**Security:** **[[DevSecOps]]** (**trial**) extends DevOps with measurable security work in each stage, not a separate waterfall audit.

**Not the same as:** buying a "DevOps platform" SKU; a dedicated ops team that only runs tickets; or **[[Jenkins]]**/**[[CloudBees]]** (**hold**) as the whole strategy.

## Details

| Topic | Notes |
|-------|--------|
| **Culture** | Shared ownership of running software; no "throw over the wall" |
| **Batch size** | Trunk-based flow; feature flags over long-lived branches |
| **Legacy** | Automate incrementally; do not wait for perfect greenfield |
| **Metrics** | Lead time, deploy frequency, MTTR, change failure rate (DORA) |
| **On-call** | Dev participates in production feedback loops |

**References**

- [Wikipedia: DevOps](https://en.wikipedia.org/wiki/DevOps)
