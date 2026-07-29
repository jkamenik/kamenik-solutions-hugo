---
title: TestKube
date: '2026-07-24'
lastmod: '2026-07-24'
draft: false
keywords:
- TestKube
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: New
    subcategories:
    - ci-cd-tools
---

[Testkube](https://testkube.io/) is a Kubernetes-native platform that orchestrates existing test tools inside your clusters. We **assess** it under **[[Tool]]** for cluster-local runs decoupled from CI runners.

## Blurb

> The Open Testing Platform for AI-Driven Engineering Teams

## Summary

**What it is:** Control plane plus in-cluster agents. Agents run your existing suites (k6, Playwright, Cypress, and more) as Kubernetes workloads. Results sync to one dashboard.

**When to use:** Tests should run where the app runs, across many clusters, without rewriting suites for each CI system. You want triggers from CI, GitOps, schedules, or Kubernetes events.

**When to skip:** You lack Kubernetes, or a single CI pipeline already covers test execution and result visibility well enough.

**Trade-offs:** Agents are open source and stay in your infra. The full control plane (dashboard, RBAC, SSO) is Pro/Enterprise. Testkube orchestrates tests; it does not author them for you (AI authoring is still emerging).

**See also:** **[[CI-CD Tools]]**, **[[Kubernetes]]**, **[[Grafana k6]]**, **[[Playwright]]**, **[[Cypress]]**.

## Details

| Topic | Notes |
|-------|--------|
| **Model** | Control plane + Agents; Agents can run standalone |
| **Execution** | Test Workflows as Kubernetes-native runs |
| **Integrations** | GitHub Actions, GitLab, Jenkins, Argo CD, webhooks, CDEvents |
| **Deployment** | Cloud or on-prem control plane; air-gapped supported |

**References**

- [Testkube site](https://testkube.io/)
- [Testkube docs](https://docs.testkube.io/)
- [kubeshop/testkube on GitHub](https://github.com/kubeshop/testkube)
