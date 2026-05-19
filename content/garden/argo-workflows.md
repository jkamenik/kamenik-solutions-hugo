---
title: "Argo Workflows"
date: 2026-05-17
lastmod: 2026-05-18
draft: false

keywords:
  - Argo Workflows

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
    subcategories:
      - ci-cd-tools

aliases:
  - /radar/tools/argo-workflows
---

[Argo Workflows](https://argo-workflows.readthedocs.io/) is a **[[Kubernetes]]**-native workflow engine: DAGs and steps run as pods, with retries, artifacts, parameters, and scheduling. We rate it **trial** for in-cluster CI, data, and ML pipelines; reach for it when workflows must live on the cluster; prefer hosted CI or lighter orchestrators when you do not need K8s execution.

## Blurb

> Argo Workflows is an open source container-native workflow engine for orchestrating parallel jobs on Kubernetes.

## Summary

**Role:** run workflows (build, test, ETL, training, batch jobs); not deploy apps. Pair with **[[ArgoCD]]** for GitOps delivery after images and manifests are ready.

**When to use:** teams already on K8s needing DAG semantics, fan-in/fan-out, artifact passing between steps, or long-running parallel jobs; ML/data platforms that want everything as YAML CRDs on the cluster.

**When to skip:** simple PR pipelines (GitHub Actions / GitLab CI are enough); no Kubernetes; small teams that should not operate a workflow control plane, consider **[[Dagu]]** (assess) for single-binary YAML DAGs off-cluster.

**Vs alternatives:** **[[Tekton]]** (assess) is also K8s-native CI but less mature for complex DAGs and harder to debug. **[[Jenkins]]** (hold) on-cluster is a security and ops liability, **[[Jenkins X]]** explicitly points to Argo Workflows instead. Apache Airflow is the non-K8s incumbent for data DAGs; Argo Workflows fits when pods *are* the unit of work.

## Details

| Topic | Notes |
|-------|--------|
| **Model** | `Workflow` CRDs; steps as containers; templates for reuse |
| **Artifacts** | S3/GCS/Artifactory-style artifact repository recommended at scale |
| **UI** | Argo UI for run history, logs, resubmit |
| **Events** | Often paired with Argo Events for event-driven triggers (separate project) |
| **Ops** | Controller + workflow RBAC; watch etcd load and archived workflows |

**Ecosystem:** Same Argo Proj family as **[[ArgoCD]]** but independent install; do not confuse deploy (CD) with orchestration (workflows).
