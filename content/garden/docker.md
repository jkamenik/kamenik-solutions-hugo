---
title: Docker
date: '2023-03-03'
lastmod: '2026-07-02'
draft: false
keywords:
- Docker
- docker CLI
- Moby
params:
  aliases:
  - docker CLI
  - Moby
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: No Change
aliases:
- /radar/tools/docker
---

[Docker](https://docs.docker.com/). Popularized containers and still owns the de facto **`docker` CLI** and **Dockerfile** workflow.

## Blurb

> Docker Documentation is the official Docker library of resources, manuals, and guides to help you containerize applications.

## Summary

**What to separate:**

| Piece | Garden stance |
|-------|----------------|
| **OCI images / containers** | **adopt** via **[[Containerization]]** |
| **`docker build` / BuildKit in CI** | Common; also available via buildah/kaniko |
| **`docker` CLI on laptop** | OK as a front-end when the engine is Rancher/Podman/containerd |
| **Docker Desktop (paid)** | **hold** for new org-wide adoption |
| **Docker Hub as only registry** | Avoid single-vendor lock-in; use ECR/GCR/ACR + mirrors |

**Why hold (vendor stack):** commercialization of Desktop, license audits at scale, and historical tie-in to Docker-specific paths (`#category/containers` era tooling). The **engine** (containerd, runc) is industry standard; the **Docker Inc desktop bundle** is not.

**When the CLI still makes sense:** tutorials, **[[Dev Container]]** docs, **[[Dive]]**, and CI snippets that call `docker`. Prefer rootless/daemonless options where security policy requires it.

**Alternatives for local dev:** **[[Rancher Desktop]]** (**trial**), **[[Podman]]** (**trial** in garden), or Linux VM with containerd only.

## Details

| Topic | Notes |
|-------|--------|
| **Dockerfile** | Ubiquitous; keep multi-stage, non-root, minimal bases |
| **Compose** | Fine for local stacks; not a prod orchestrator (**[[Kubernetes]]**) |
| **CI** | `docker build` or `buildx`; pin BuildKit; scan images in pipeline |
| **Security** | Do not mount `/var/run/docker.sock` into untrusted CI without isolation |

**References**

- [Docker documentation](https://docs.docker.com/)
