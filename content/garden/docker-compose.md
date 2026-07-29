---
title: Docker Compose
date: '2024-04-25'
lastmod: '2026-07-29'
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
    movement: Moved Out
aliases:
- /radar/tools/docker-compose
---

[Docker Compose](https://docs.docker.com/compose/). Defines multi-container apps in `compose.yaml` and runs them with `docker compose up`.

## Blurb

> Learn how to use Docker Compose to define and run multi-container applications with this detailed introduction to the tool.

## Summary

**Garden stance:** We **hold** Docker Compose for our estate.

**Key points:**

| Topic | Notes |
|-------|--------|
| **Files** | `compose.yaml` at repo root or `deploy/compose/`; pin image digests for anything non-throwaway |
| **Secrets** | Use env files gitignored; not for prod secret stores |
| **Parity** | Do not assume Compose service DNS equals K8s Service names |
| **Engine** | Runs on **[[Docker]]** / **[[Rancher Desktop]]** / Podman compose support |

**References**

- [Docker Compose documentation](https://docs.docker.com/compose/)

## Details

| Topic | Notes |
|-------|--------|
| **Files** | `compose.yaml` at repo root or `deploy/compose/`; pin image digests for anything non-throwaway |
| **Secrets** | Use env files gitignored; not for prod secret stores |
| **Parity** | Do not assume Compose service DNS equals K8s Service names |
| **Engine** | Runs on **[[Docker]]** / **[[Rancher Desktop]]** / Podman compose support |

**References**

- [Docker Compose documentation](https://docs.docker.com/compose/)
