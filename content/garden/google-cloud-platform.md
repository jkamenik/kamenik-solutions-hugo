---
title: Google Cloud Platform
date: '2026-05-05'
lastmod: '2026-07-01'
draft: false
keywords:
- Google Cloud Platform
- GCP
params:
  aliases:
  - GCP
  garden:
    kind: item
    usefulness: adopt
    category: platform
    movement: No Change
    subcategories:
    - cloud
---

[Google Cloud Platform](https://cloud.google.com/) (GCP) is Google's hyperscale **[[Cloud]]** offering. We **adopt** it as the multi-cloud spearhead for container workloads, data, AI, and **[[DevSecOps]]**-aligned platforms. It is not a wholesale replacement for **[[AWS]]** or **[[Azure]]** where those estates already exist. GCP's service catalog reflects Google's internal scale problems more than a feature checklist against other hyperscalers.

## Blurb

> The new way to cloud.

## Summary

**Garden stance:** Use GCP as the preferred greenfield cloud for **[[Kubernetes]]** (**[[Google GKE]]**), big data, ML/AI services, and security-first platform engineering. Keep **[[Hybrid Cloud]]** in play: run each workload where the fit is strongest rather than mirroring every service across vendors.

**Strengths:** Independent CPU, memory, and GPU billing for right-sized compute. Global networking and storage foundations exposed as managed services. First-class observability through Cloud Operations (formerly Stackdriver). Strong **[[IaC]]** and policy guardrail story across the control plane.

**Caveats:** Smaller third-party marketplace than **[[AWS]]**. Not every **[[AWS]]** or **[[Azure]]** service has a direct peer. Teams need explicit multi-cloud boundaries and **[[Terraform]]** discipline so GCP stays the spearhead, not another silo.

## Details

| Topic | Notes |
|-------|--------|
| **Position** | Third-largest hyperscaler by market share; strongest fit for K8s-native and data/AI greenfield |
| **Compute** | Decoupled vCPU, RAM, and GPU pricing vs fixed instance families on **[[AWS]]** |
| **K8s** | **[[Google GKE]]** is the default managed cluster choice; Anthos for multi-cloud fleet ops |
| **Observability** | Cloud Operations integrates metrics, logging, and tracing; GCP metrics included |
| **Security** | BeyondCorp lineage; org/folder/project IAM; policy and **[[IaC]]**-first setup patterns |
| **Data** | BigQuery, Spanner, and shared storage layer for analytics and global consistency |
| **Multi-cloud** | **[[Hybrid Cloud]]** pattern: GCP spearhead, not full migration from **[[AWS]]**/**[[Azure]]** |
| **Tooling** | **[[Terraform]]** and Google-native deployment tools; **[[GoLang]]** ecosystem alignment |
