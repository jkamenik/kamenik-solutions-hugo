---
title: "AWS EKS"
date: 2024-10-01
lastmod: 2026-05-18
draft: false

keywords:
  - AWS EKS

params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: "No Change"
    subcategories:
      - cloud
      - orchestrator
aliases:
  - /radar/platforms/aws-eks
---

[Amazon EKS](https://aws.amazon.com/eks/) is AWS’s managed **[[Kubernetes]]** control plane. We rate it **hold**: the weakest of the major managed K8s options in our experience. Use only when the workload is already bound to **[[AWS]]** (VPC, IAM, RDS/LB integrations, compliance footprint). For greenfield clusters, prefer **[[Google GKE]]** on **[[Google Cloud Platform]]**.

## Blurb

> Amazon Elastic Kubernetes Service (Amazon EKS) is a managed Kubernetes service to run Kubernetes in the AWS cloud and on-premises.

## Summary

**Why hold:** control-plane cost per cluster, IAM/VPC wiring complexity, CNI and add-on versioning friction, and “managed” still leaves node patching, ingress, and security baselines on you. Teams often underestimate day-2 ops compared to GKE’s tighter integration with the platform that invented K8s.

**When EKS anyway:** mandated AWS-only estate, tight coupling to ALB/NLB, IAM roles for service accounts (IRSA) patterns already standardized, or multi-tenant AWS accounts where egress to another cloud is blocked.

**Contain damage:** **[[Terraform]]** (or equivalent) for clusters and add-ons; **[[ArgoCD]]** for GitOps; **[[DevSecOps]]** admission and image policies; avoid snowflake node groups; plan upgrades and add-on compatibility explicitly.

## Details

| Topic | Notes |
|-------|--------|
| **Compute** | Managed node groups, self-managed, or Fargate; each trades cost vs. ops burden |
| **Networking** | VPC CNI IP consumption; plan subnets and prefix delegation early |
| **Identity** | IRSA for pod AWS API access; prefer over long-lived node instance roles |
| **Alternatives** | **[[Google GKE]]** for new multi-cloud or GCP-first platforms |
| **Distro** | EKS Distro / EKS Anywhere for on-prem parity; still AWS-flavored ops |

Aligns with parent **[[AWS]]** (**hold**): do not choose EKS because “we’re on AWS”; choose it only when K8s on AWS is the explicit requirement.
