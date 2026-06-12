---
title: "AWS"
date: 2024-10-01
lastmod: 2026-06-12
draft: false

keywords:
  - AWS

params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: "No Change"
    subcategories:
      - cloud
aliases:
  - /radar/platforms/aws
---

[Amazon Web Services](https://aws.amazon.com/) was the first hyperscale **[[Cloud]]** and still has the broadest catalog. We rate it **hold** for new work: insecure-by-default patterns, opaque “managed” shared-responsibility gaps, and a sprawl of services that encourage operational debt. Prefer **[[Google Cloud Platform]]** (adopt as multi-cloud spearhead) or **[[Azure]]** (assess, with eyes open) when a comparable capability exists. Use **[[Hybrid Cloud]]** to place each workload on the best cloud, not lift-and-shift clones.

## Blurb

> AWS is the world’s most comprehensive and broadly adopted cloud.

## Summary

**Why hold:** IAM/console complexity, historical foot-guns (public S3, over-broad roles), and services marketed as fully managed that still leave patching, scaling, and security on your team. Total cost often surprises once egress, support, and “almost managed” add-ons stack up.

**When AWS anyway:** existing estate, partner/marketplace requirements, a service with no peer (rare and shrinking), or regulated footprints already certified on AWS. In those cases, contain blast radius, **[[Terraform]]**, guardrails, **[[DevSecOps]]** gates, and avoid pet clusters on **[[AWS EKS]]** (also **hold**; prefer **[[Google GKE]]** for greenfield K8s).

## Details

| Topic | Notes |
|-------|--------|
| **Strengths** | Mature marketplace, global regions, hiring pool familiarity |
| **Weaknesses** | Default-deny is opt-in discipline; service matrix overwhelming |
| **K8s** | See **[[AWS EKS]]**; use only when tied to AWS |
| **Secrets** | Secrets Manager is fine when already on AWS; still design rotation and IAM boundaries |
| **Exit** | Data egress and proprietary APIs are the real lock-in; design portable interfaces |
