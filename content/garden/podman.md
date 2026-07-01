---
title: Podman
date: '2023-12-17'
lastmod: '2026-06-30'
draft: false
keywords:
- Podman
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: New
---

[Podman](https://podman.io/) is a daemonless OCI container engine with a Docker-compatible CLI and rootless-by-default security model. Containers run as user processes; there is no background daemon to attack or babysit. We **trial** it for Linux hosts, CI runners, and rootless workflows without **[[Docker Desktop]]** licensing. It complements **[[Rancher Desktop]]** (**trial**) when you want a lightweight engine instead of a full desktop Kubernetes stack.

## Blurb

> The best free & open source container tools.

## Summary

**What you get:** `podman run`, `podman build` (via Buildah), `podman compose`, pods, and optional remote APIs. Most commands work as a normal user with user namespaces. Images and containers follow **[[Open Container Initiative]]** specs, so they interoperate with **[[Kubernetes]]** and other OCI runtimes.

**When to try:**

| Situation | Why Podman |
|-----------|------------|
| Linux laptop or server | Default on many RHEL/Fedora estates; strong systemd/Quadlet story |
| Rootless security | No setuid daemon; containers map root inside to your host UID |
| CI pipelines | Run builds and tests without Docker Desktop or a shared daemon |
| Docker script migration | `alias docker=podman` covers most day-to-day CLI use |

**When to skip:**

| Situation | Prefer instead |
|-----------|----------------|
| Desktop GUI plus local K8s | **[[Rancher Desktop]]** (**trial**) |
| macOS speed and polish | **[[OrbStack]]** (**assess**) or Rancher Desktop |
| Docker Swarm or plugins | Not supported; use **[[Kubernetes]]** |
| Every Compose edge case | Test `podman compose` first; some stacks assume Moby-only behavior |

**Not a perfect drop-in:** Swarm, plugins, and a few Compose or volume patterns still break. Pilot your repo before mandating Podman org-wide.

## Details

| Topic | Notes |
|-------|--------|
| **Install** | https://podman.io/getting-started/installation (Linux primary; Podman Desktop for macOS/Windows) |
| **Rootless** | Needs `/etc/subuid` and `/etc/subgid`; pasta or slirp4netns for networking |
| **Compose** | `podman compose` for Compose files; verify against **[[Docker Compose]]** features you use |
| **Builds** | Image builds delegate to Buildah; Dockerfile workflow is familiar |
| **Remote** | `podman --remote` and API service for tools that expect a Docker socket |
| **Dev Containers** | Works when the IDE can reach a compatible socket; test with your stack |

**References**

- [Podman](https://podman.io/)
- [Documentation](https://docs.podman.io/)
- [GitHub](https://github.com/containers/podman/)
- [Rootless tutorial](https://github.com/containers/podman/blob/main/docs/tutorials/rootless_tutorial.md)
