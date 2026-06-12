---
title: "CI-CD Tools"
date: 2024-10-01
lastmod: 2026-06-12
draft: false

keywords:
  - CI-CD Tools
  - CI/CD
  - CI-CD

params:
  aliases:
    - CI/CD
    - CI-CD
  garden:
    kind: subcategory
    parent_category: tool
    subcategory_slug: ci-cd-tools
---

Under [[Tool]], **CI-CD Tools** groups products that run or orchestrate build, test, and deploy pipelines. The label **CI/CD** is overloaded: in practice it spans three **technique** notes we keep separate from this subcategory:

- **[[Continuous Integration]]** (**adopt**): merge often, automated build and [[Integration Testing]] on every change.
- **[[Continuous Delivery]]** (**adopt**): artifacts are always releasable; promotion and gates are explicit (on-prem, regulated, or multi-stage SaaS).
- **[[Continuous Deployment]]** (**assess**): every green mainline commit reaches production automatically; right mainly for [[Software as a Service]] with strong observability and rollback (often paired with **[[Feature Flags]]**).

**Pipeline shapes (how tools map):**

| Pattern | What happens after CI | Typical fit |
|---------|------------------------|-------------|
| CI + **deployment** | Artifact ships to production (or equivalent) after tests | SaaS, K8s GitOps (**[[ArgoCD]]**), managed runners (**[[GitHub Actions]]**) |
| CI + **delivery** | Artifact is built, signed, and handed off; deploy is manual or downstream | On-prem, air-gapped, or customer-operated installs |

Tag a **product** here when the note is about a runner, controller, or deploy server (Actions, Argo CD, Jenkins). Tag the **technique** notes above when the note is about the practice, not a vendor.

**Garden stance (products in this bucket):**

- **adopt** **[[GitHub Actions]]** for repos on GitHub (CI and light CD in-repo).
- **adopt** **[[ArgoCD]]** for **[[Kubernetes]]** continuous delivery via **[[GitOps]]** (reconcile from Git; do not conflate with **[[Argo Workflows]]**, which is workflow/CI on-cluster).
- **trial** **[[Argo Workflows]]** when you need DAG-style jobs on K8s without bolting Jenkins onto the cluster.
- **assess** **[[Tekton]]** only if you must standardize on Kubernetes-native pipeline CRDs and accept operational complexity.
- **hold** **[[Jenkins]]** (security and pet-server risk; migrate off where possible) and **[[Capistrano]]** (SSH push deploy; superseded by GitOps or image-based CD for new work).

**Cross-cutting:** wire **[[DevSecOps]]**, **[[Policy as Code]]**, and secret stores (**[[HashiCorp Vault]]**, cloud secret managers) on the PR path, not inside a pipeline server's internal credential UI.
