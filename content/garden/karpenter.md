---
title: Karpenter
date: '2026-06-24'
lastmod: '2026-06-24'
draft: false
keywords:
- Karpenter
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: New
    subcategories:
    - orchestrator
---

[Karpenter](https://karpenter.sh/) is an open source Kubernetes node autoscaler that provisions just-in-time compute from pod constraints. It consolidates workloads, replaces underused nodes, and uses declarative `NodePool` resources instead of fixed node groups. We **assess** it for AWS EKS and emerging Azure AKS footprints where faster scale-out and lower idle cost beat classic Cluster Autoscaler node groups.

## Blurb

> Karpenter automatically launches just the right compute resources to handle your cluster's applications.
