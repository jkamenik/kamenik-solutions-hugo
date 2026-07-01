---
title: Open Container Initiative
date: '2023-12-17'
lastmod: '2026-07-01'
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

[Open Container Initiative](https://opencontainers.org)

The [Open Container Initiative](https://opencontainers.org) (OCI) is the open governance body that defines industry standards for container images and runtimes. We **adopt** OCI-compatible artifacts and runtimes for any workload that ships as a container. **[[Kubernetes]]** ecosystems assume OCI images; portable packaging is effectively required for cloud-native delivery.

## Blurb

> The Open Container Initiative is an open governance structure for the express purpose of creating open industry standards around container formats and runtimes.

## Summary

**What it is:** a **[[Platform]]** standards layer under the Linux Foundation, not a single vendor product. Core specs include the **Image Spec** (how layers and manifests are packaged), the **Runtime Spec** (how a bundle executes on a host), and distribution-related guidance for registries.

**Why adopt:** one build artifact runs on a laptop, in CI, and in production across **[[Docker]]**, **[[Podman]]**, containerd, CRI-O, and **[[Kubernetes]]** runtimes. **[[Containerization]]** as a **[[Technique]]** depends on this shared format.

**How we use it:** produce OCI images in CI, scan and test them (**[[Container Structure Test]]**), promote by digest, and avoid proprietary-only image formats. Prefer OCI-compatible local engines over commercial desktop bundles tied to one vendor.

**Not the same as:** the **[[Docker]]** Inc product stack (**hold** for new org-wide Desktop adoption). OCI is the standard; Docker popularized tooling around it.

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
