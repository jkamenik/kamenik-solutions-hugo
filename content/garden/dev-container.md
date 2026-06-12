---
title: "Dev Container"
date: 2025-04-23
lastmod: 2026-06-12
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
    movement: "No Change"
---

[Development Containers](https://containers.dev/) (`devcontainer.json` + image) define a **reproducible dev environment** in OCI: toolchain, extensions, and settings live in the repo instead of on each laptop. We **adopt** them for team projects so dev, **[[Continuous Integration]]**, and onboarding share the same container definition.

## Blurb

> Development containers are a great way to simplify and standardize the setup of your development environment.

## Summary

**What it is:** an open spec (not a single product). The IDE or host attaches to a container built from your repo's `.devcontainer/devcontainer.json` (and Dockerfile or prebuilt image). Born in VS Code; **[[Cursor]]** and other VS Code–compatible editors support the same flow.

**Why adopt:**

| Problem | Dev Container answer |
|---------|-------------------|
| "Works on my machine" | One image definition in Git |
| Onboarding | `Reopen in Container` instead of a wiki install guide |
| Dev vs CI drift | Same base image or Dockerfile path in CI |
| Toolchain pins | OS packages, language versions, CLIs in the image |

**Repo artifacts:**

- `.devcontainer/devcontainer.json` — features, mounts, ports, post-create commands
- `Dockerfile` or `image:` — how the environment is built
- Optional **dev container features** (composable apt/npm layers)

**Local runtime:** needs a container engine. Prefer **[[Rancher Desktop]]** (**assess**) or Podman; **[[Docker]]** Desktop is **hold** for licensing but still common. See **[[Containerization]]** for the wider OCI stance.

**Not the same as:** production **[[Kubernetes]]** manifests (deploy shape); **[[Ansible]]** on pets (mutable hosts); or **[[DevSecOps]]** policy alone without a defined dev image.

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
