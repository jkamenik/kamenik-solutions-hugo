---
title: OrbStack
date: '2026-06-30'
lastmod: '2026-06-30'
draft: false
keywords:
- OrbStack
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[OrbStack](https://orbstack.dev) is a native macOS app for Docker containers, local Kubernetes, and full Linux machines. It is a drop-in replacement for the `docker` CLI and **[[Docker Compose]]**. We **assess** it as a fast macOS option worth researching before standardizing. **[[Rancher Desktop]]** (**trial**) remains the cross-platform open-source default over **[[Docker Desktop]]** (**hold**).

## Blurb

> OrbStack is the fast, light, and easy way to run Docker containers and Linux. Develop at lightspeed with our Docker Desktop alternative.

## Summary

**What you get:** a Swift-native menu bar app with fast startup, low CPU and memory use, Rosetta x86 emulation, automatic container domains, and optional local **[[Kubernetes]]**. Linux machines include SSH, two-way file sharing, and VS Code remote editing. The Docker socket stays compatible with **[[Dev Container]]** and Compose workflows.

**When to evaluate:**

| Situation | Why OrbStack |
|-----------|--------------|
| macOS daily driver | Sub-second startup vs heavy Electron VM stacks |
| Large bind mounts | Faster file sync for `node_modules` and watched dirs |
| Laptop battery | Lower idle CPU and memory than **[[Docker Desktop]]** |
| Linux VM on Mac | Full distros with CLI integration, not just containers |

**When to skip:**

| Situation | Prefer instead |
|-----------|----------------|
| Windows or Linux host | OrbStack is macOS-only |
| Docker Desktop extensions or Scout | Not supported |
| Open-source mandate only | **[[Rancher Desktop]]** (**trial**) |
| Production orchestration | **[[Kubernetes]]** in cloud, not the local cluster |

**Licensing:** free for personal use; commercial and freelance use requires a paid subscription. That cost pushes many teams toward **[[Rancher Desktop]]** first.

## Details

| Topic | Notes |
|-------|--------|
| **Install** | https://orbstack.dev/download or `brew install --cask orbstack` |
| **Migration** | One-click import from **[[Docker Desktop]]** per OrbStack docs |
| **CLI** | `docker`, `docker compose`, `kubectl`, and `orb` commands |
| **Kubernetes** | Optional local cluster; compare feature depth to **[[Rancher Desktop]]** |
| **Networking** | localhost forwarding, IPv6, VPN-friendly DNS |
| **Compare** | [OrbStack vs Docker Desktop](https://docs.orbstack.dev/compare/docker-desktop) |

**References**

- [OrbStack](https://orbstack.dev)
- [Documentation](https://docs.orbstack.dev/)
- [GitHub](https://github.com/orbstack/orbstack)
