---
title: Podman
date: '2023-12-17'
lastmod: '2026-07-29'
draft: false
keywords:
- Podman
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
---

[Podman](https://podman.io/). Is a daemonless OCI container engine with a Docker-compatible CLI and rootless-by-default security model.

## Summary

**Garden stance:** We **trial** Podman for our estate.

**Key points:**

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
