---
title: Docker Desktop
date: '2025-04-23'
lastmod: '2026-07-02'
draft: false
keywords:
- Docker Desktop
- Docker Desktop for Mac
- Docker Desktop for Windows
params:
  aliases:
  - Docker Desktop for Mac
  - Docker Desktop for Windows
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: Moved Out
aliases:
- /radar/platforms/docker-desktop
---

[Docker Desktop](https://www.docker.com/products/docker-desktop/). Is Docker Inc's **licensed desktop bundle**: GUI, `docker`/`docker compose` CLI, optional local **[[Kubernetes]]**, and extensions on macOS/Windows/Linux.

## Blurb

> Docker Desktop is collaborative containerization software for developers. Get started and download Docker Desktop today on Mac, Windows, or Linux.

## Summary

**Garden stance:** We **hold** Docker Desktop for our estate.

**Key points:** | Topic | Notes |
|-------|--------|
| **Dev Containers** | Often documented with Desktop; other engines work if the socket is compatible |
| **WSL2 / macOS VM** | Desktop wraps a Linux VM; know where disk and CPU go |
| **Extensions** | Optional; treat as supply-chain risk in regulated environments |
| **CI** | Do not require Desktop in pipelines; use rootless builders in **[[GitHub Actions]]** |

**References**

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Subscription overview](https://www.docker.com/pricing/)

## Details

| Topic | Notes |
|-------|--------|
| **Dev Containers** | Often documented with Desktop; other engines work if the socket is compatible |
| **WSL2 / macOS VM** | Desktop wraps a Linux VM; know where disk and CPU go |
| **Extensions** | Optional; treat as supply-chain risk in regulated environments |
| **CI** | Do not require Desktop in pipelines; use rootless builders in **[[GitHub Actions]]** |

**References**

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Subscription overview](https://www.docker.com/pricing/)
