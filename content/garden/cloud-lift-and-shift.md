---
title: "Cloud Lift and Shift"
date: 2025-07-10
lastmod: 2026-05-18
draft: false

keywords:
  - Cloud Lift and Shift
  - lift and shift
  - lift-and-shift

params:
  garden:
    kind: item
    usefulness: hold
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/cloud-lift-and-shift
---

[Lift and shift](https://en.wikipedia.org/wiki/Lift_and_shift) (rehosting) moves workloads to **[[Cloud]]** with little or no redesign. We rate the pattern **hold**: do not start new migrations this way, and do not chase hyperscaler credits by cloning the same stack on **[[AWS]]**, **[[Azure]]**, and **[[Google Cloud Platform]]**. Prefer **[[Hybrid Cloud]]**: place each workload on the provider that fits, then bridge accounts securely.

## Blurb

> Lift and shift is a migration strategy that moves workloads to the cloud without redesigning the application architecture.

## Summary

**Two failure modes we see:**

1. **Datacenter rehost (classic):** VMs and pets move to cloud IaaS unchanged. Cost savings rarely materialize; you inherit cloud complexity without cloud-native ops (**[[Cattle Not Pets]]**, autoscaling, managed data planes).
2. **Credit-chasing portability theater:** Teams re-create RDS-like, EKS-like, and blob storage on another cloud to burn startup credits, then pay egress and dual-run tax forever.

**Why hold:** lift-and-shift optimizes for short-term migration metrics, not operability. Stateful pets, hand-tuned networking, and proprietary managed-service mappings do not survive provider hops.

**Do instead:** greenfield on **[[Google Cloud Platform]]** where possible; **[[Terraform]]** and portable interfaces for what must move; refactor toward **[[Containerization]]**/**[[Kubernetes]]** and **[[Software as a Service]]** shapes; use **[[Hybrid Cloud]]** when multiple clouds are intentional, not accidental duplication.

## Details

| Anti-pattern | Why it fails | Better direction |
|--------------|--------------|------------------|
| 1:1 service cloning across clouds | Highest cost, weakest differentiation | Pick best-of-breed per workload; document why it lives there |
| Migrating databases by dump/restore monthly | Downtime, drift, data egress bills | Managed replication, eventing, or stay put and strangle |
| "Same architecture everywhere" for compliance | Compliance follows controls, not SKU parity | Shared policy (**[[DevSecOps]]**, **[[Policy as Code]]**), different implementations |
| Lift VMs without autoscaling groups | Pay for peak 24/7 | **[[Cattle Not Pets]]**, instance templates, rightsizing |
| Chasing credits without TCO model | Credits expire; architecture remains | Model 3-year TCO including egress, support, and engineer time |

**When rehost is acceptable:** hard exit deadline from a datacenter, ISV appliance with no cloud-native path yet, or temporary landing zone with a written strangler plan and sunset date. Label it **legacy containment**, not the target architecture.

**References**

- [Wikipedia: lift and shift](https://en.wikipedia.org/wiki/Lift_and_shift)
- Contrast: **[[Hybrid Cloud]]** (adopt) in this garden
