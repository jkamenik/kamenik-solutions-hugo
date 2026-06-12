---
title: "Containerization"
date: 2025-04-23
lastmod: 2026-06-12
draft: false

keywords:
  - Containerization
  - containers
  - OCI containers

params:
  aliases:
    - containers
    - OCI containers
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"
aliases:
  - /radar/techniques/containerization
---

[Containerization](https://opencontainers.org/)

Containerization packages an application and its dependencies into an immutable **OCI image** that runs the same way on a laptop, in CI, and in production. We **adopt** it for services we build and operate: it enables **[[Cattle Not Pets]]**, pairs with **[[Kubernetes]]** orchestration, and satisfies portability goals from the **[[12 Factor App]]** (processes, config via env, disposability).

## Blurb

> The Open Container Initiative is an open governance structure for the express purpose of creating open industry standards around container formats and runtimes.

## Summary

**What it is:** a **[[Technique]]** (how you ship), not a single vendor product. The **[[Open Container Initiative]]** defines image and runtime specs; builders (`docker build`, `buildah`, `kaniko`) produce images; runtimes (`containerd`, `cri-o`, **[[Podman]]**) execute them.

**Why adopt:** reproducible builds, smaller blast radius than VMs, standard CI artifacts, and a straight path to **[[GitOps]]** (image tag is the deploy unit). **[[Software as a Service]]** and **[[Cloud]]** native designs assume containers.

**Tooling stance in this garden:**

| Concern | Direction |
|---------|-----------|
| **Format / runtime** | **adopt** OCI via **[[Open Container Initiative]]** |
| **Local dev runtime** | Prefer **[[Rancher Desktop]]** (**assess**) or Podman over commercial **[[Docker]]** Desktop (**hold**) |
| **Orchestration** | **adopt** **[[Kubernetes]]** at scale; single-node compose only for local/dev |
| **Image tests** | **adopt** **[[Container Structure Test]]** after build |
| **Dev environments** | **adopt** **[[Dev Container]]** for shared toolchain |

**Not the same as:** VMs with configuration management only; serverless functions without a container artifact (though many FaaS run OCI under the hood).

## Details

| Topic | Notes |
|-------|--------|
| **Images** | Immutable; promote by tag/digest, not mutable servers |
| **Config** | Inject at runtime (env, mounts, secrets stores), not bake secrets into layers |
| **Security** | Non-root users, minimal base images, scan in CI |
| **Lift-and-shift** | Containerizing a VM monolith helps packaging; still refactor for **[[Cattle Not Pets]]** |

**References**

- [Open Container Initiative](https://opencontainers.org/)
