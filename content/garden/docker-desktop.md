---
title: "Docker Desktop"
date: 2025-04-23
lastmod: 2026-05-18
draft: false

keywords:
  - Docker Desktop
  - Docker Desktop for Mac
  - Docker Desktop for Windows

params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: "Moved Out"

aliases:
  - /radar/platforms/docker-desktop
---

[Docker Desktop](https://www.docker.com/products/docker-desktop/) is Docker Inc's **licensed desktop bundle**: GUI, `docker`/`docker compose` CLI, optional local **[[Kubernetes]]**, and extensions on macOS/Windows/Linux. We rate it **hold** with **Moved Out** from adopt: do not standardize new estates on it; prefer **[[Rancher Desktop]]** (**assess**) or **[[Podman]]** for OCI-compatible local engines. **[[Containerization]]** stays **adopt**.

## Blurb

> Docker Desktop is a one-stop shop for everything you need to build, share, and run containers.

## Summary

**What you get:** integrated container runtime, image builds, **[[Docker Compose]]** for local stacks, and a click-to-enable K8s cluster for laptop demos. Fits tutorials and **[[Dev Container]]** docs that assume a `docker` socket.

**Why hold (new adoption):**

| Concern | Detail |
|---------|--------|
| **Licensing** | Commercial terms for larger companies; audits and true-ups are real |
| **Vendor stack** | Tied to **[[Docker]]** Hub defaults and Docker Inc roadmap |
| **Alternatives** | **[[Rancher Desktop]]** (open-source GUI, containerd/nerdctl, optional k8s) |
| **Policy** | Same garden line as **[[Docker]]**: portable OCI, not Desktop-as-standard |

**When existing use is fine:** teams already licensed and productive; migrate on renewal or new machine policy, not as a fire drill.

**Not a prod platform:** local dev only; production stays **[[Kubernetes]]** + **[[GitOps]]**, not Desktop's embedded cluster.

## Details

| Topic | Notes |
|-------|--------|
| **Dev Containers** | Often documented with Desktop; other engines work if the socket is compatible |
| **WSL2 / macOS VM** | Desktop wraps a Linux VM; know where disk and CPU go |
| **Extensions** | Optional; treat as supply-chain risk in regulated environments |
| **CI** | Do not require Desktop in pipelines; use rootless builders in **[[GitHub Actions]]** |

**Garden pattern:** **hold** for net-new org mandates; **assess** **[[Rancher Desktop]]** on the next laptop refresh. See **[[Docker]]** for CLI vs engine vs Desktop separation.

**References**

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Subscription overview](https://www.docker.com/pricing/)
