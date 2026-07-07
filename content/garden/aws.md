---
title: AWS
date: '2024-10-01'
lastmod: '2026-07-02'
draft: false
keywords:
- AWS
params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: No Change
    subcategories:
    - cloud
aliases:
- /radar/platforms/aws
---

[AWS](https://aws.amazon.com/). Was the first hyperscale **[[Cloud]]** and still has the broadest catalog.

## Blurb

> Amazon Web Services offers reliable, scalable, and inexpensive cloud computing services. Free to join, pay only for what you use.

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
