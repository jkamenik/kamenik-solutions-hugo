---
title: "Docker Compose"
date: 2024-04-25
lastmod: 2026-06-12
draft: false

keywords:
  - Docker Compose
  - compose
  - docker-compose

params:
  aliases:
    - compose
    - docker-compose
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: "Moved Out"
aliases:
  - /radar/tools/docker-compose
---

[Docker Compose](https://docs.docker.com/compose/) defines multi-container apps in `compose.yaml` and runs them with `docker compose up`. We rate it **hold** with **Moved Out** of the default path: fine for **local** dependency stacks, not for production orchestration. For **[[Kubernetes]]** dev loops use **[[Skaffold]]** (**trial**) instead of growing Compose into a pseudo-prod platform.

## Blurb

> Compose is a tool for defining and running multi-container Docker applications.

## Summary

**What it is:** YAML (or JSON) describing services, networks, volumes, and env for a small stack on one Docker engine. The v2 plugin (`docker compose`) replaced the legacy `docker-compose` Python binary.

**When Compose is still OK:**

| Use | Notes |
|-----|--------|
| **Local integration** | Postgres + Redis + app on a laptop |
| **Demos / spikes** | Fast bring-up without a cluster |
| **CI smoke** | Short-lived `compose up` in a job (tear down after) |

**When to avoid (why hold):**

- Production multi-host orchestration (**[[Kubernetes]]**, **[[ArgoCD]]**, **[[GitOps]]**)
- "Compose in prod" on **[[Docker Swarm]]** (also **hold** in this garden)
- Teams that should invest in cluster-native dev (**[[Skaffold]]**, **[[Dev Container]]** + K8s)

**K8s-shaped alternative:** **[[Skaffold]]** build/deploy/watch against a real cluster or kind/minikube, so dev matches prod networking and manifests.

## Details

| Topic | Notes |
|-------|--------|
| **Files** | `compose.yaml` at repo root or `deploy/compose/`; pin image digests for anything non-throwaway |
| **Secrets** | Use env files gitignored; not for prod secret stores |
| **Parity** | Do not assume Compose service DNS equals K8s Service names |
| **Engine** | Runs on **[[Docker]]** / **[[Rancher Desktop]]** / Podman compose support |

**References**

- [Docker Compose documentation](https://docs.docker.com/compose/)
