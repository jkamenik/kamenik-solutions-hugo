---
title: K3d
date: '2024-10-01'
lastmod: '2026-07-07'
draft: false
keywords:
- K3d
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[K3d](https://k3d.io/) is a CLI that runs k3s clusters inside Docker containers for fast local **[[Kubernetes]]** development. We **assess** it when you need a production-like API on a laptop without provisioning cloud control planes.

## Blurb

> k3d is a lightweight wrapper to run k3s(Rancher Lab's minimal Kubernetes distribution) in docker.

## Summary

**When to use:**

| Use | Notes |
|-----|--------|
| **Local K8s dev** | Spin up single- or multi-node k3s clusters in seconds |
| **CI smoke tests** | Ephemeral clusters in GitHub Actions via k3d-action |
| **Helm and manifest work** | Exercise charts and YAML against a real API before cloud apply |
| **Low resource footprint** | k3s targets edge and dev; lighter than full distro clusters |

**When to skip:**

- Production or shared staging (use managed **[[Kubernetes]]** such as **[[Google GKE]]**)
- Teams standardized on kind or minikube with existing docs and scripts
- Environments without **[[Docker]]** (k3d requires a Docker engine)
- GUI-first Mac/Windows dev where **[[Rancher Desktop]]** k3s mode is already adopted

**Trade-offs:** Community-driven, not an official Rancher/SUSE product. k3s differs slightly from upstream Kubernetes; validate CRDs and APIs you depend on.

## Details

### Quick Start

```bash
k3d cluster create dev
kubectl cluster-info
```

Add agents with `--agents N` or extra servers with `--servers N` for multi-node topology tests.

### Requirements

| Topic | Notes |
|-------|--------|
| **Docker** | Required; k3d v5.x needs Docker 20.10.5+ (runc 1.0.0-rc93+) |
| **kubectl** | Separate install; k3d writes kubeconfig context |
| **Ports** | API exposed on a host port chosen by k3d; load balancer container fronts server nodes |

### Features Worth Knowing

| Feature | Notes |
|---------|--------|
| **Image import** | Load local images into cluster without a registry push |
| **Registry mirror** | Run an embedded registry for fast iteration |
| **Config file** | Reproduce cluster shape from YAML for team sharing |
| **Multi-cluster** | Several k3d clusters on one Docker host |

### Compared to Alternatives

| Option | When k3d wins | When the alternative wins |
|--------|---------------|---------------------------|
| **[[Rancher Desktop]]** | Scriptable CLI, CI, disposable clusters | GUI k3s toggle and integrated engine on Mac/Windows |
| **kind** (not in garden) | k3s footprint, Rancher ecosystem familiarity | Upstream conformance testing against vanilla K8s |
| **minikube** (not in garden) | Faster multi-node in Docker | Built-in drivers for VM-based local clusters |

### CI and Tooling

- [k3d-action](https://github.com/k3d-io/k3d-action) for GitHub Actions
- [vscode-k3d](https://marketplace.visualstudio.com/items?itemName=TimothyGer.k3d) VS Code extension

**References**

- [k3d documentation](https://k3d.io/)
- [k3d-io/k3d on GitHub](https://github.com/k3d-io/k3d)
- [k3s project](https://k3s.io/)
