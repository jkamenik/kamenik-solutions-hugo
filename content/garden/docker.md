---
title: "Docker"
date: 2023-03-03
lastmod: 2026-06-12
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
    movement: "No Change"
aliases:
  - /radar/tools/docker
---

[Docker](https://docs.docker.com/) popularized containers and still owns the de facto **`docker` CLI** and **Dockerfile** workflow. We rate the **Docker Inc product stack** (**hold**), especially **[[Docker Desktop]]** licensing and hub-centric defaults: prefer **[[Open Container Initiative]]**-compatible engines (**[[Rancher Desktop]]**, **[[Podman]]**) for new local dev. **[[Containerization]]** as a technique remains **adopt**.

## Blurb

> Docker helps developers bring their ideas to life by conquering the complexity of app development.

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

**Alternatives for local dev:** **[[Rancher Desktop]]** (**assess**), **[[Podman]]** (**trial** in garden), or Linux VM with containerd only.

## Details

| Topic | Notes |
|-------|--------|
| **Dockerfile** | Ubiquitous; keep multi-stage, non-root, minimal bases |
| **Compose** | Fine for local stacks; not a prod orchestrator (**[[Kubernetes]]**) |
| **CI** | `docker build` or `buildx`; pin BuildKit; scan images in pipeline |
| **Security** | Do not mount `/var/run/docker.sock` into untrusted CI without isolation |

**References**

- [Docker documentation](https://docs.docker.com/)
