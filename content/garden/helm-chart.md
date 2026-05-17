---
title: "Helm Chart"
date: 2025-07-13
lastmod: 2026-05-17
draft: false

keywords:
  - Helm Chart

params:
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: "New"
    subcategories:
      - language

aliases:
---

[Helm Chart](https://helm.sh/docs/topics/charts/)

Helm Charts are the artifact that [[Helm]] reads and installs in a Kubernetes cluster. They are written in [[Go Template]] format, and are compiled into OCI compatible images, which means they can be stored in any OCI compliant [[Docker]] registry, of which there are a plenty.

While Helm itself is a MUST if you are in the [[Kubernetes]] ecosystem that doesn't extend to maintaining your own Helm Charts. They are nessessity to understand but there are limited use cases where you should maintain them your selves. The real only reason to do that is if you are providing customers the ability to install on their own clusters. For all other cases [[Kustomize]] is a better choice.
