---
title: Kubernetes Resource Orchestrator (KRO)
date: '2026-06-22'
lastmod: '2026-07-02'
draft: false
keywords:
- Kubernetes Resource Orchestrator (KRO)
- kro
- Kube Resource Orchestrator
params:
  aliases:
  - kro
  - Kube Resource Orchestrator
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - orchestrator
---

[Kubernetes Resource Orchestrator (KRO)](https://kro.run/). We **assess** it under **[[Tool]]** in the garden.

## Blurb

> Build declarative, secure, and verifiable Kubernetes abstractions

## Summary

**What it does:** A ResourceGraphDefinition (RGD) describes multiple Kubernetes resources, dependencies between them, and a SimpleSchema for the instance API. kro validates the RGD, materializes a CRD, and runs dedicated controllers to reconcile instances. Wiring uses [[CEL]] expressions, validated at creation time.

**When to use:** platform teams publishing internal building blocks (app + IAM + networking); compositions that mix core resources with third-party CRDs; EKS shops that want managed kro via EKS Capabilities.

**When to skip:** a single Deployment/Service pair ([[Kustomize]] overlays are enough); packaged third-party charts ([[Helm]]); complex admission or multi-step imperative logic (a full operator or [[Shell Operator]] hooks may fit better).

**Ecosystem notes:** kro lives in kubernetes-sigs/kro and is a SIG Cloud Provider subproject. AWS, Azure, and Google Cloud collaborate on it. EKS documents kro for composing ACK-managed AWS resources into higher-level APIs.

## Details

**Core CRDs:** `ResourceGraphDefinition` defines the graph; instances of the generated CRD create the underlying objects.

**Install:** Helm chart or raw manifests from the kro release artifacts; on EKS, optional EKS Capability for a managed controller.

**Docs:** [kro.run](https://kro.run/), [kubernetes-sigs/kro](https://github.com/kubernetes-sigs/kro), [EKS kro guide](https://docs.aws.amazon.com/eks/latest/userguide/kro.html).
