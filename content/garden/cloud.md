---
title: "Cloud"
date: 2026-01-10
lastmod: 2026-05-18
draft: false

keywords:
  - Cloud

params:
  garden:
    kind: subcategory
    parent_category: platform
    subcategory_slug: cloud

aliases:
---

Under **[[Platform]]**, **Cloud** groups hyperscale public clouds and their managed primitives: someone else's computers, exposed through APIs and consoles so you rent capacity instead of racking hardware. The provider runs regions, physical security, and base virtualization; you own identity, configuration, data classification, and most "managed" service hardening under shared responsibility.

**Stack (how items map):**

| Layer | What you get | Examples in the garden |
|-------|----------------|-------------------------|
| **IaaS** | Networks, compute, block/object storage | **[[AWS]]**, **[[Azure]]**, **[[Google Cloud Platform]]** |
| **PaaS / managed runtime** | Less ops on the control plane; still your app and config | **[[Google GKE]]**, **[[AWS EKS]]** (K8s control planes) |
| **SaaS** | Vendor runs the app | See **[[Software as a Service]]** (not duplicated here) |

Tag a **hyperscaler or cloud-native platform service** here when the note is about choosing or operating on AWS/GCP/Azure (or a direct analog). Tag **[[Hybrid Cloud]]** for multi-cloud *strategy*; tag **[[Cloud Lift and Shift]]** when discussing migration anti-patterns.

**Garden stance (hyperscalers in this bucket):**

- **adopt** **[[Google Cloud Platform]]** as the multi-cloud **spearhead** for greenfield: containers, data, AI, and **[[DevSecOps]]**-friendly defaults; do not assume 1:1 feature parity with AWS marketing checklists.
- **hold** **[[AWS]]** and **[[Azure]]** for new platforms: default away unless estate, marketplace, or Microsoft-stack requirements force them; contain legacy with **[[Terraform]]**, policy guardrails, and portable interfaces.
- **hold** **[[AWS EKS]]** when tied to AWS; prefer **[[Google GKE]]** for greenfield Kubernetes on GCP.
- **adopt** **[[Hybrid Cloud]]** as a **technique** when each workload lands on the best cloud for the job, not when teams mirror every service three times.

**Cross-cutting expectations:** **[[Cattle Not Pets]]** for compute; **[[Terraform]]** (or equivalent **[[Declarative IaC]]**) for everything that can be code; secrets outside vendor CI credential stores; treat egress and proprietary APIs as the real lock-in. Bridge accounts with **[[Tailscale]]**, SD-WAN, or zero-trust patterns, not flat VPN spaghetti.
