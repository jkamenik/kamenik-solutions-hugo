---
title: "Docker Swarm"
date: 2024-04-09
lastmod: 2026-05-17
draft: false

keywords:
  - Docker Swarm

params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: "Moved Out"

aliases:
  - /radar/platforms/docker-swarm
---

[Docker Swarm](https://docs.docker.com/engine/swarm/) is Docker Engine's built-in **cluster orchestrator** (swarm mode): managers, workers, overlay networks, and rolling service updates. We rate it **hold** with **Moved Out**: do not start new multi-host estates on Swarm. Use **[[Kubernetes]]** (**adopt**) for orchestration. Existing Swarm clusters backed by **Mirantis** commercial support may run until a planned migration.

## Blurb

> Swarm mode lets you create and manage a cluster of Docker nodes, and deploy application services to the cluster.

## Summary

**History:** Swarm was pitched as a simpler **[[Kubernetes]]** alternative, then repositioned as a path from **[[Docker Compose]]** to multiple machines. The ecosystem standardized on Kubernetes; **[[Docker]]** Inc focuses on Desktop, Hub, and BuildKit, not growing Swarm as a greenfield choice.

**Who still maintains it:** **Mirantis** (Docker Enterprise lineage) offers long-term Swarm support and security updates for paying customers (committed through 2030). That is **not** the same as Docker Inc driving new features in swarm mode for everyone.

**Why hold (new adoption):**

| Concern | Detail |
|---------|--------|
| **Talent & tooling** | Helm, **[[GitOps]]**, operators, and cloud control planes assume Kubernetes |
| **Compose bridge** | `docker stack deploy` from Compose is a dead-end for most teams (**[[Docker Compose]]** is local-only in this garden) |
| **Stateful workloads** | Persistent volumes, failover, and upgrades lag K8s patterns; gaps are unlikely to close for casual users |
| **Strategic fit** | **[[Containerization]]** stays **adopt**; orchestration should be K8s, not Swarm |

**When existing use is OK:** regulated estates with Mirantis contracts, small stable fleets, or brownfield until migration is funded. Plan exit to **[[Kubernetes]]** + **[[ArgoCD]]** (or your GitOps tool), not indefinite Swarm expansion.

## Details

| Topic | Notes |
|-------|--------|
| **vs Kubernetes** | Swarm is simpler API surface; K8s wins on ecosystem, CRDs, and hiring |
| **Engine** | Swarm mode ships in the open-source engine docs; production support is vendor-specific |
| **Migration** | Map Services to Deployments; replace overlay secrets with cluster secret stores |
| **Local dev** | Do not use Swarm on laptops; use Compose locally and K8s (kind/minikube) for cluster parity |

**Garden pattern:** **hold** + **Moved Out** aligns with **[[Docker Compose]]** (no Compose-in-prod-on-Swarm) and **[[Docker]]** (hold vendor stack for new mandates). Net-new orchestration is **[[Kubernetes]]**.

**References**

- [Docker Swarm mode overview](https://docs.docker.com/engine/swarm/)
- [Mirantis Swarm support](https://www.mirantis.com/software/swarm/)
