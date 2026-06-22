---
title: "KustomizeGoat"
date: 2026-06-15
lastmod: 2026-06-22
draft: false

keywords:
  - KustomizeGoat

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
---

[KustomizeGoat](https://github.com/bridgecrewio/kustomizegoat) is Bridgecrew's "Vulnerable by Design" **[[Kustomize]]** manifest repository. It ships NGINX deployment overlays from insecure base through a compliant `prod` layer. We **trial** it to calibrate **[[Checkov]]** `--framework kustomize` scans and **[[Shift Left]]** gates on rendered manifests. Do not apply lab overlays to production clusters.

## Blurb

> Demonstrating secure and non secure kubernetes IaC manifests using Kustomize.io (`kubectl -k`) overlays.

## Summary

KustomizeGoat completes Bridgecrew's IaC Goat family alongside **[[TerraGoat]]**, **[[BicepGoat]]**, **[[CdkGoat]]**, and **[[CfnGoat]]**. It targets **[[Kubernetes]]** manifest composition, not cloud provider templates or live cluster exploitation (**[[Kubernetes Goat]]**).

**When to use:** teaching **[[Checkov]]** Kustomize support; showing how base vs overlay inheritance affects CIS/K8s policy results; calibrating per-environment CI scans (`base`, `test`, `dev`, `prod` overlays).

**When to skip:** you need live cluster attack scenarios (use **[[Kubernetes Goat]]**); you scan flat YAML only with no **[[Kustomize]]** overlays; you need Terraform or CloudFormation goats instead.

**Repo layout:** `kustomize/base` (insecure), `kustomize/overlays/test` (partial fixes), `kustomize/overlays/dev` (empty overlay), `kustomize/overlays/prod` (passes built-in K8s policies when rendered).


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
