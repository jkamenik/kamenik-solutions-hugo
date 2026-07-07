---
title: Rancher Desktop
date: '2023-12-17'
lastmod: '2026-07-02'
draft: false
keywords:
- Rancher Desktop
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
---

[Rancher Desktop](https://rancherdesktop.io/). Is SUSE's open-source desktop app for containers and local Kubernetes on macOS, Windows, and Linux.

## Blurb

> Open source desktop application that provides Kubernetes, Container Management, bundled utilities on the desktop

## Summary

**Garden stance:** We **trial** Rancher Desktop for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

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
