---
title: "Kustomize"
date: 2025-06-14
lastmod: 2026-05-17
draft: false

keywords:
  - Kustomize

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "No Change"

aliases:
  - /radar/tools/kustomize
---

[Kustomize](https://kustomize.io/)

Kustomize is a [[Kubernetes]]-native configuration management tool built directly into `kubectl` (`kubectl apply -k`). Rather than templating YAML like [[Helm]], it works through **overlays** — you define a base set of manifests and layer environment-specific patches (dev, staging, prod) on top without modifying the originals. The result is always pure, valid YAML with no rendering step.

Worth trialling if your team finds [[Helm]] chart authoring heavyweight or if you want to avoid a templating language entirely. That said, Helm still wins for complex deployments with external dependencies, versioned releases, and rollback support. Evaluate whether your use case fits the overlay model before committing.

## Blurb

> Kustomize introduces a template-free way to customize application configuration that simplifies the use of off-the-shelf applications. Now, built into `kubectl` as `apply -k`.

## Summary

Kustomize shines for teams managing a small number of Kubernetes environments with predictable variance (namespace, replica count, image tag). The overlay model keeps base manifests clean and diffs readable. However, it lacks [[Helm]]'s packaging, dependency management, and release lifecycle — for anything that needs to be distributed or versioned as a unit, Helm is still the stronger choice. Trial it on a new service before adopting broadly.
