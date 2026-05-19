---
title: "Dive"
date: 2023-07-23
lastmod: 2026-05-18
draft: false

keywords:
  - Dive
  - dive

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "No Change"

aliases:
  - /radar/tools/dive
---

[Dive](https://github.com/wagoodman/dive) is a terminal UI for exploring **OCI/Docker image layers**: file tree per layer, layer size, and an **efficiency score** to spot bloat. We rate it **trial** for interactive image slimming during development; pair automated gates with **[[Container Structure Test]]** and registry scanners in CI, not Dive alone.

## Blurb

> A tool for exploring a docker image, layer contents, and discovering ways to shrink the size of your Docker/OCI image.

## Summary

**Role:** developer feedback loop after `docker build` (or Podman): see which layers added weight, which files duplicate across layers, and what to move to multi-stage builds or `.dockerignore`.

**When to use:**

- Debugging fat images before production
- Teaching **[[Containerization]]** (layer caching, multi-stage Dockerfiles)
- Quick review of third-party base images

**When to skip:**

- Headless CI-only pipelines (use `dive ci` only if you accept its efficiency threshold; many teams prefer CST + vulnerability scan)
- Teams on **[[Dev Container]]** only who never inspect host-built images

**Workflow:**

```bash
dive myimage:tag          # interactive TUI
dive ci --ci-config .dive-ci myimage:tag   # optional CI gate
```

Works with the `docker` CLI; often used with **[[Docker]]** / **[[Rancher Desktop]]** local engines. Image must be available locally (`docker load` if from CI artifact).

## Details

| Topic | Notes |
|-------|--------|
| **Efficiency score** | Heuristic; use as a hint, not a policy |
| **Multi-stage** | Dive shines when comparing builder vs runtime stages |
| **Security** | Layer exploration is not vulnerability scanning |
| **Complements** | **[[Container Structure Test]]** asserts image contract; Dive explores *why* the image is large |

**Garden pattern:** **trial** on repos you build; **adopt** CST in CI for every image you ship.

**References**

- [dive on GitHub](https://github.com/wagoodman/dive)
