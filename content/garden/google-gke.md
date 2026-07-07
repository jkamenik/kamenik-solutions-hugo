---
title: Google GKE
date: '2023-07-23'
lastmod: '2026-07-07'
draft: false
keywords:
- Google GKE
- GKE
- Google Kubernetes Engine
params:
  aliases:
  - GKE
  - Google Kubernetes Engine
  garden:
    kind: item
    usefulness: trial
    category: platform
    movement: No Change
    subcategories:
    - cloud
    - orchestrator
---

[Google GKE](https://cloud.google.com/kubernetes-engine) is Google's managed **[[Kubernetes]]** control plane on **[[Google Cloud Platform]]**. We **trial** it as the default cluster choice for greenfield K8s when GCP is in scope.

## Blurb

> Google Kubernetes Engine (GKE) is a managed, production-ready environment for deploying containerized applications.

## Summary

**What it is:** Managed K8s from the team that open-sourced **[[Kubernetes]]**. GKE runs the control plane, integrates with GCP IAM and networking, and offers Standard (you manage node pools) or Autopilot (GKE provisions and bills per pod).

**When to use:**

- Greenfield container platforms on **[[Google Cloud Platform]]**
- Teams that want lower day-2 ops than **[[AWS EKS]]**
- Workloads that benefit from Autopilot's nodeless scaling
- Fleets that need Config Sync, Policy Controller, or multi-cluster management without extra SKUs (included on Standard since late 2025)

**When to skip:** Hard **[[AWS]]** or **[[Azure]]** lock-in; on-prem-only mandates without Anthos; tiny footprints where **[[K3d]]** or a single VM is enough; cost models where per-pod Autopilot pricing loses to reserved Standard nodes at steady utilization.

| Mode | Best for | Trade-off |
|------|----------|-----------|
| **Standard** | Predictable baselines, custom node shapes, GPU pools, existing Terraform modules | You own node patching, pool sizing, and add-on compatibility |
| **Autopilot** | Variable traffic, small platform teams, fast scale-out | Pod resource requests drive cost; some DaemonSets and privileged patterns restricted |
| **Autopilot workloads on Standard** (2025+) | Mix managed and self-managed pools in one cluster | Qualifying cluster version and release channel required |

**Pairs with:** **[[Terraform]]** or Google Config Connector for cluster IaC; **[[ArgoCD]]** or **[[GitOps]]** for delivery; **[[Policy as Code]]** via GKE Policy Controller or **[[Gatekeeper]]**-compatible admission.

## Details

### Pricing and Operations (2025)

Google simplified GKE pricing in late 2025:

- **Cluster management fee:** $0.10/hour per cluster (all modes and topologies).
- **Free tier:** $74.40/month in credits per billing account (covers one zonal Standard or Autopilot cluster fee).
- **Standard compute:** pay for underlying Compute Engine nodes in your pools.
- **Autopilot:** pay per pod based on CPU, memory, and ephemeral storage **requests**.
- **Fleet features:** Fleets, Teams, Config Management, Policy Controller, and Fleet dashboard ship on Standard at no extra charge (previously tier-gated).

Check the [GKE pricing page](https://cloud.google.com/kubernetes-engine/pricing) before capacity planning. Extended release channel clusters may incur additional fees during extended support windows.

### Standard vs Autopilot

| Topic | Standard | Autopilot |
|-------|----------|-----------|
| Node management | You define node pools | GKE provisions nodes per scheduled pods |
| Scaling | Cluster autoscaler on pools; HPA/VPA on workloads | Built-in horizontal and vertical pod scaling |
| Security baseline | You harden node images and OS | Hardened, Google-managed node OS by default |
| Flexibility | Full K8s feature surface | Opinionated; some pod specs rejected at admission |

Since September 2025, Autopilot's container-optimized compute platform can run on **qualifying Standard clusters** for selected workloads. You do not need a dedicated Autopilot-only cluster for every use case.

### Comparison to **[[AWS EKS]]**

Parent **[[Google Cloud Platform]]** and sibling **[[AWS EKS]]** (**hold**) share the same garden stance: prefer GKE for new K8s unless AWS coupling is fixed.

| Topic | GKE | EKS |
|-------|-----|-----|
| Control-plane ops | Flat per-cluster fee; strong GCP integration | Per-cluster fee; more IAM/VPC wiring |
| Node lifecycle | Autopilot option or managed node auto-upgrade on Standard | Managed node groups or Fargate; more assembly required |
| Day-2 burden | Lower for Autopilot; Fleet policy tools included | Higher: CNI, add-ons, ingress, and patching often bespoke |
| Garden rating | **trial** (default on GCP) | **hold** (containment on AWS) |

### Related Garden Links

- **[[Google Cloud Platform]]**: parent platform (**adopt**)
- **[[Kubernetes]]**: orchestrator reference (**adopt**)
- **[[Kustomize]]**, **[[Helm]]**: manifest packaging on cluster
- **[[Keda]]**, **[[Karpenter]]**: event-driven and node autoscaling patterns (compare to GKE's built-in autoscaler stack)
