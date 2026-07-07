---
title: Google Cloud Platform
date: '2026-05-05'
lastmod: '2026-07-02'
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

[Google Cloud Platform](https://cloud.google.com/). (GCP) is Google's hyperscale **[[Cloud]]** offering.

## Blurb

> Meet your business challenges head on with AI and cloud computing services from Google, including security, data management, and hybrid & multi-cloud.

## Summary

**Garden stance:** We **adopt** Google Cloud Platform for our estate.

**Key points:** | Topic | Notes |
|-------|--------|
| **Position** | Third-largest hyperscaler by market share; strongest fit for K8s-native and data/AI greenfield |
| **Compute** | Decoupled vCPU, RAM, and GPU pricing vs fixed instance families on **[[AWS]]** |
| **K8s** | **[[Google GKE]]** is the default managed cluster choice; Anthos for multi-cloud fleet ops |
| **Observability** | Cloud Operations integrates metrics, logging, and tracing; GCP metrics included |
| **Security** | BeyondCorp lineage; org/folder/project IAM; policy and **[[IaC]]**-first setup patterns |
| **Data** | BigQuery, Spanner, and shared storage layer for analytics and global consistency |
| **Multi-cloud** | **[[Hybrid Cloud]]** pattern: GCP spearhead, not full migration from **[[AWS]]**/**[[Azure]]** |
| **Tooling** | **[[Terraform]]** and Google-native deployment tools; **[[GoLang]]** ecosystem alignment |

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
