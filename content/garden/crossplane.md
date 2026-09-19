---
title: Crossplane
date: '2026-08-14'
lastmod: '2026-08-14'
draft: false
keywords:
- Crossplane
- Upbound
params:
  aliases:
  - Upbound
  garden:
    kind: item
    usefulness: trial
    category: platform
    movement: No Change
    subcategories:
    - orchestrator
---

[Crossplane](https://www.crossplane.io/) is the cloud-native framework for platform engineering. We **trial** it under **[[Platform]]** in the garden because it shows strong fit for internal developer platforms built on [[Kubernetes]].

## Blurb

> Crossplane Is the Cloud-Native Framework for Platform Engineering

## Summary

**What it does:** Crossplane extends [[Kubernetes]] to orchestrate any resource, not just containers. It builds control planes that expose declarative APIs backed by Providers and Configurations, letting platform teams compose infrastructure without bespoke controllers.

**When to use:** platform teams building an internal developer platform (IDP) that needs custom APIs with guardrails. Also cloud-native shops already running Kubernetes who want GitOps-friendly infrastructure. Also teams wanting to expose APIs that humans, automation, and AI agents can self-serve on.

**When to skip:** small footprint workloads where Terraform or direct cloud CLI is enough. Also teams without Kubernetes who do not want the operational cost of running a control plane. Also single-cloud shops needing only classic IaC with no custom API layer.

**Ecosystem notes:** Crossplane is an open source CNCF project built and commercially sponsored by Upbound. It overlaps with [[Kubernetes Resource Orchestrator (KRO)]] for composition of Kubernetes resources into higher-level APIs.

## Details

**Core concepts:** Providers connect Crossplane to external services (cloud, DNS, database); Configurations bundle Providers and Compositions into installable packages; Compositions define how a Composite Resource (XR) maps to managed resources.

**V2:** Crossplane v2 shifts focus from infrastructure-only to control planes for applications, with new APIs for grouping of resources.

**Promotion criteria:** adopt only after a production workload shows real value over Terraform plus scripts. Pair with GitOps ([[ArgoCD]]) when Compositions and Claims live in repo.

**Docs:** [docs.crossplane.io](https://docs.crossplane.io/), [github.com/crossplane/crossplane](https://github.com/crossplane/crossplane), [why control planes](https://www.crossplane.io/why-control-planes).
