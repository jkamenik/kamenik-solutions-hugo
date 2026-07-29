---
title: Open Container Initiative
date: '2023-12-17'
lastmod: '2026-07-29'
draft: false
keywords:
- Open Container Initiative
- OCI
params:
  aliases:
  - OCI
  garden:
    kind: item
    usefulness: adopt
    category: platform
    movement: No Change
    subcategories:
    - cloud
---

[Open Container Initiative](https://opencontainers.org). We **adopt** it under **[[Platform]]** in the garden.

## Summary

**Key points:**

| Spec / piece | Role |
|--------------|------|
| **OCI Image Spec** | Layered filesystem bundles, manifests, config JSON |
| **OCI Runtime Spec** | `config.json` + rootfs bundle executed by a runtime |
| **runc** | Reference low-level runtime implementing the runtime spec |
| **containerd / CRI-O** | Higher-level runtimes used by **[[Kubernetes]]** nodes |
| **Registries** | Distribution of manifests and layers by digest |

### Garden Tooling Stance

| Concern | Direction |
|---------|-----------|
| **Format** | **adopt** OCI images everywhere |
| **Build** | Dockerfile/BuildKit, buildah, kaniko (all target OCI) |
| **Local run** | **[[Podman]]**, **[[Rancher Desktop]]**, or engine of choice that consumes OCI |
| **Orchestration** | **adopt** **[[Kubernetes]]** at scale; compose-style only for local/dev |## Personal Experience

<!-- User-owned: vault-only; never published or exported. Agents read for /tech-garden update synthesis; proofread spelling/grammar only. -->

## Details

| Spec / piece | Role |
|--------------|------|
| **OCI Image Spec** | Layered filesystem bundles, manifests, config JSON |
| **OCI Runtime Spec** | `config.json` + rootfs bundle executed by a runtime |
| **runc** | Reference low-level runtime implementing the runtime spec |
| **containerd / CRI-O** | Higher-level runtimes used by **[[Kubernetes]]** nodes |
| **Registries** | Distribution of manifests and layers by digest |

### Garden Tooling Stance

| Concern | Direction |
|---------|-----------|
| **Format** | **adopt** OCI images everywhere |
| **Build** | Dockerfile/BuildKit, buildah, kaniko (all target OCI) |
| **Local run** | **[[Podman]]**, **[[Rancher Desktop]]**, or engine of choice that consumes OCI |
| **Orchestration** | **adopt** **[[Kubernetes]]** at scale; compose-style only for local/dev |
