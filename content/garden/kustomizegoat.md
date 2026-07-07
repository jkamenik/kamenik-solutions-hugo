---
title: KustomizeGoat
date: '2026-06-15'
lastmod: '2026-07-02'
draft: false
keywords:
- KustomizeGoat
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
---

[KustomizeGoat](https://github.com/bridgecrewio/kustomizegoat). Is Bridgecrew's "Vulnerable by Design" **[[Kustomize]]** manifest repository.

## Blurb

> Vulnerable Kustomize Kubernetes templates for training and education - bridgecrewio/kustomizegoat

## Summary

**Garden stance:** We **trial** KustomizeGoat for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

### Compared to [[Kubernetes Goat]]

| Lens | KustomizeGoat | [[Kubernetes Goat]] |
|------|---------------|---------------------|
| Format | **[[Kustomize]]** bases and overlays | Full vulnerable cluster lab |
| Primary use | **[[Checkov]]** scan calibration | Hands-on cluster exploitation |
| Deploy risk | Manifest apply to a lab cluster only | Intentionally vulnerable running workloads |
| Best fit | Overlay-aware static scanning drills | Runtime K8s security training |

### Overlay Scan Results (Typical)

| Overlay | Posture |
|---------|---------|
| `base` | Insecure NGINX deployment (many policy failures) |
| `test` | Partial hardening; still fails most checks |
| `dev` | Same as `base` (empty overlay merge) |
| `prod` | Compliant additions; clean **[[Checkov]]** scan |

### Lab Guardrails

- Treat rendered manifests as lab artifacts; apply only in disposable namespaces or clusters.
- Prefer scan-only workflows unless the exercise requires a live deploy.
- Compare overlay results to explain inherited vs environment-specific misconfigurations.

### Scan-First Lab Sketch
```bash
git clone https://github.com/bridgecrewio/kustomizegoat.git
cd kustomizegoat
checkov --framework kustomize -d .
# Optional: checkov --framework kustomize -d . --check CKV_K8S_11 --compact
```
