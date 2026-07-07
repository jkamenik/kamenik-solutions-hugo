---
title: Argo Workflows
date: '2026-05-17'
lastmod: '2026-07-02'
draft: false
keywords:
- Argo Workflows
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
    subcategories:
    - ci-cd-tools
aliases:
- /radar/tools/argo-workflows
---

[Argo Workflows](https://argo-workflows.readthedocs.io/). Is a **[[Kubernetes]]**-native workflow engine: DAGs and steps run as pods, with retries, artifacts, parameters, and scheduling.

## Summary

**Garden stance:** We **trial** Argo Workflows for our estate.

**Key points:** | Topic | Notes |
|-------|--------|
| **Model** | `Workflow` CRDs; steps as containers; templates for reuse |
| **Artifacts** | S3/GCS/Artifactory-style artifact repository recommended at scale |
| **UI** | Argo UI for run history, logs, resubmit |
| **Events** | Often paired with Argo Events for event-driven triggers (separate project) |
| **Ops** | Controller + workflow RBAC; watch etcd load and archived workflows |

**Ecosystem:** Same Argo Proj family as **[[ArgoCD]]** but independent install; do not confuse deploy (CD) with orchestration (workflows).

## Details

| Topic | Notes |
|-------|--------|
| **Model** | `Workflow` CRDs; steps as containers; templates for reuse |
| **Artifacts** | S3/GCS/Artifactory-style artifact repository recommended at scale |
| **UI** | Argo UI for run history, logs, resubmit |
| **Events** | Often paired with Argo Events for event-driven triggers (separate project) |
| **Ops** | Controller + workflow RBAC; watch etcd load and archived workflows |

**Ecosystem:** Same Argo Proj family as **[[ArgoCD]]** but independent install; do not confuse deploy (CD) with orchestration (workflows).
