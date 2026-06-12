---
title: "ArgoCD"
date: 2023-07-23
lastmod: 2026-05-18
draft: false

keywords:
  - ArgoCD

params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "No Change"
    subcategories:
      - ci-cd-tools
aliases:
  - /radar/tools/argocd
---

[Argo CD](https://argo-cd.readthedocs.io/) is a declarative **[[GitOps]]** controller for **[[Kubernetes]]**: it watches Git (or Helm chart repos), compares desired state to the live cluster, and reconciles drift. We **adopt** it as the default continuous-delivery plane when workloads run on K8s (especially multi-cluster) instead of pushing deploy keys through **[[Jenkins]]**-style imperative CD.

## Blurb

> Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes.

## Summary

**Role:** deploy and sync, not build. CI (image build, tests) stays in your pipeline; Argo CD applies manifests after merge. It understands plain YAML, **[[Helm]]**, Kustomize, Jsonnet, and plugins; each tracked as an `Application` (and optionally grouped via app-of-apps).

**When to use:** any team practicing Git-as-source-of-truth for cluster config; hub-and-spoke or many clusters from one control plane; need UI for diff, sync, rollback, and health.

**When to skip:** no Kubernetes; single-cluster experiments where a simpler pipeline suffices; orgs not ready to secure Git repo permissions and secrets outside Git (see **[[GitOps]]** challenges).

**Pairs with:** **[[Policy as Code]]** and admission checks on the PR path; **[[Shift Left]]** review before merge; **[[Continuous Deployment]]** as the outcome Argo CD enforces.

**Not the same as:** **[[Argo Workflows]]** (CI/data/ML pipelines on K8s). For legacy VM deploys, **[[Ansible]]** may still bootstrap nodes; Argo CD owns the cluster layer.

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
