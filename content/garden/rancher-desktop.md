---
title: Rancher Desktop
date: '2023-12-17'
lastmod: '2026-06-30'
draft: false
keywords:
- Rancher Desktop
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: New
---

[Rancher Desktop](https://rancherdesktop.io/) is SUSE's open-source desktop app for containers and local Kubernetes on macOS, Windows, and Linux. It bundles k3s, kubectl, Helm, and a choice of containerd or dockerd (Moby). We **trial** it as the default cross-platform local runtime over **[[Docker Desktop]]** (**hold**). It fits under **[[Tool]]** when Apache 2.0 licensing, multi-OS support, and local K8s depth matter more than macOS-only speed.

## Blurb

> An open-source application that provides all the essentials to work with containers and Kubernetes on the desktop.

## Summary

**What you get:** an Electron GUI plus bundled CLIs (`docker`, `nerdctl`, `kubectl`, `helm`, `rdctl`). Pick containerd or Moby, enable k3s, choose a Kubernetes version, and reset the cluster from the UI. Works with **[[Dev Container]]**, Skaffold, and VS Code per upstream docs.

**When to try:**

| Situation | Why Rancher Desktop |
|-----------|---------------------|
| Cross-platform team | Same app on macOS, Windows, and Linux |
| Open-source policy | Apache 2.0; no Docker Inc desktop license |
| Local Kubernetes | k3s with version pinning and cluster dashboard |
| **[[Docker Desktop]]** exit | OCI-compatible `docker` CLI without commercial Desktop terms |

**When to skip:**

| Situation | Prefer instead |
|-----------|----------------|
| macOS-only, speed first | **[[OrbStack]]** (**assess**) for native performance |
| No local K8s needed | Lighter containerd-only CLI stacks |
| Production clusters | Cloud **[[Kubernetes]]**, not the embedded k3s |

**Contrast:** **[[OrbStack]]** (**assess**) wins on macOS startup, battery, and bind mounts but is macOS-only and paid for commercial use. Rancher Desktop is the garden's **trial** default for portable local dev.

## Details

| Topic | Notes |
|-------|--------|
| **Install** | https://rancherdesktop.io/ (macOS, Windows, Linux) |
| **Runtime** | containerd + nerdctl or Moby + `docker` CLI |
| **Kubernetes** | k3s; pick version; reset from GUI |
| **CLI** | `rdctl` for app control; bundled kubectl and Helm |
| **Compare** | [Rancher vs Docker Desktop](https://www.rancher.com/products/rancher-desktop) |

**References**

- [Rancher Desktop](https://rancherdesktop.io/)
- [GitHub](https://github.com/rancher-sandbox/rancher-desktop/)
- [SUSE docs](https://documentation.suse.com/cloudnative/rancher-manager/latest/en/integrations/rancher-desktop.html)
