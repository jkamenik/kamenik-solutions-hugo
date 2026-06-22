---
title: "Tilt"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - Tilt

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
aliases:
  - /radar/tools/tilt
---

[Tilt](https://tilt.dev/) is a local development tool for teams running services on **[[Kubernetes]]**. A `Tiltfile` (Starlark) declares how to build images, apply manifests, and watch files for fast rebuild and redeploy loops. We **trial** it for microservice dev clusters where `kubectl apply` and manual image builds are too slow.

## Blurb

> Kubernetes for Prod, Tilt for Dev

## Summary

**What it is:** CLI plus local UI that orchestrates Docker builds, live sync, port forwards, and resource status for a dev namespace.

**When to use:** many interdependent services on kind, minikube, or remote dev clusters; need one command (`tilt up`) for the whole stack; pair with **[[Dev Container]]** or local Docker.

**When to skip:** single-service apps with plain `docker compose`; team standardized on Skaffold or cloud dev environments only; no Kubernetes in the inner loop.

**Key features:** live update (sync files into running containers), resource grouping, log aggregation in the Tilt UI, extensions ecosystem.


## Details

| Topic | Notes |
|-------|--------|
| **Config** | `Tiltfile` at repo root; `docker_build`, `k8s_yaml`, `local_resource` |
| **Run** | `tilt up` starts UI at localhost; `tilt down` cleans up |
| **CI** | Tilt Cloud (optional) for shared dev env telemetry |

**Practices:** keep Tiltfiles in **[[git]]** next to manifests; limit live-update to interpreted languages; document memory/CPU for local clusters.

**References**

- [Tilt documentation](https://docs.tilt.dev/)
- [GitHub repository](https://github.com/tilt-dev/tilt)
