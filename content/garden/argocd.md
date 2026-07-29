---
title: ArgoCD
date: '2023-07-23'
lastmod: '2026-07-29'
draft: false
keywords:
- ArgoCD
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
    subcategories:
    - ci-cd-tools
aliases:
- /radar/tools/argocd
---

[ArgoCD](https://argo-cd.readthedocs.io/). Is a declarative **[[GitOps]]** controller for **[[Kubernetes]]**: it watches Git (or Helm chart repos), compares desired state to the live cluster, and reconciles drift.

## Summary

**Garden stance:** We **adopt** ArgoCD for our estate.

**Key points:**

| Topic | Notes |
|-------|--------|
| **Sync** | Manual, automatic, or selective; prune and self-heal options |
| **Health** | Built-in resource health; custom health via Lua |
| **Multi-cluster** | Register clusters; one Argo CD instance can manage many |
| **Secrets** | Never commit plaintext. Use sealed secrets, external secrets operators, or SSM/Vault integrations |
| **RBAC** | Project-scoped apps; integrate SSO (OIDC) for the UI |

**Alternatives:** Flux CD is the other common GitOps engine (similar model, different UX). Prefer one per estate; mixing controllers on the same apps causes pain.

**References**

- [Documentation](https://argo-cd.readthedocs.io/)
- [CNCF webinar , Argo at enterprise scale](https://www.cncf.io/webinars/argo-real-enterprise-scale-with-k8s/)

## Details

| Topic | Notes |
|-------|--------|
| **Sync** | Manual, automatic, or selective; prune and self-heal options |
| **Health** | Built-in resource health; custom health via Lua |
| **Multi-cluster** | Register clusters; one Argo CD instance can manage many |
| **Secrets** | Never commit plaintext. Use sealed secrets, external secrets operators, or SSM/Vault integrations |
| **RBAC** | Project-scoped apps; integrate SSO (OIDC) for the UI |

**Alternatives:** Flux CD is the other common GitOps engine (similar model, different UX). Prefer one per estate; mixing controllers on the same apps causes pain.

**References**

- [Documentation](https://argo-cd.readthedocs.io/)
- [CNCF webinar , Argo at enterprise scale](https://www.cncf.io/webinars/argo-real-enterprise-scale-with-k8s/)
