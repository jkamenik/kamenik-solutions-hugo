---
title: Cloud Lift and Shift
date: '2025-07-10'
lastmod: '2026-07-02'
draft: false
keywords:
- Cloud Lift and Shift
- lift and shift
- lift-and-shift
params:
  aliases:
  - lift and shift
  - lift-and-shift
  garden:
    kind: item
    usefulness: hold
    category: technique
    movement: No Change
aliases:
- /radar/techniques/cloud-lift-and-shift
---

[Cloud Lift and Shift](https://en.wikipedia.org/wiki/Lift_and_shift). (rehosting) moves workloads to **[[Cloud]]** with little or no redesign.

## Summary

**Garden stance:** We **hold** Cloud Lift and Shift for our estate.

**Key points:** | Anti-pattern | Why it fails | Better direction |
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
