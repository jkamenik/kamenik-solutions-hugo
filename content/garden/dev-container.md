---
title: Dev Container
date: '2025-04-23'
lastmod: '2026-07-02'
draft: false
keywords:
- Dev Container
- devcontainer
- Development Containers
params:
  aliases:
  - devcontainer
  - Development Containers
  garden:
    kind: item
    usefulness: adopt
    category: code
    movement: No Change
---

[Dev Container](https://containers.dev/). (`devcontainer.json` + image) define a **reproducible dev environment** in OCI: toolchain, extensions, and settings live in the repo instead of on each laptop.

## Blurb

> Development containers documentation and specification page.

## Summary

**Garden stance:** We **adopt** Dev Container for our estate.

**Key points:** | Topic | Notes |
|-------|--------|
| **Secrets** | Use env files or secret mounts; never bake credentials into the image |
| **Performance** | Mount workspace with delegated volumes on macOS; cache package dirs |
| **CI** | Build/test inside the same Dockerfile in **[[GitHub Actions]]** |
| **Agents** | **[[Cursor]]** / **[[cursor-agent]]** run inside the container when the editor attaches |
| **IaC link** | Treat the dev image like **[[Declarative IaC]]** for the toolchain |

**References**

- [Development Containers](https://containers.dev/)
- [Specification](https://containers.dev/implementors/spec/)

## Details

| Topic | Notes |
|-------|--------|
| **Secrets** | Use env files or secret mounts; never bake credentials into the image |
| **Performance** | Mount workspace with delegated volumes on macOS; cache package dirs |
| **CI** | Build/test inside the same Dockerfile in **[[GitHub Actions]]** |
| **Agents** | **[[Cursor]]** / **[[cursor-agent]]** run inside the container when the editor attaches |
| **IaC link** | Treat the dev image like **[[Declarative IaC]]** for the toolchain |

**References**

- [Development Containers](https://containers.dev/)
- [Specification](https://containers.dev/implementors/spec/)
