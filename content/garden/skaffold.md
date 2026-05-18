---
title: "Skaffold"
date: 2024-04-25
lastmod: 2026-05-17
draft: false

keywords:
  - Skaffold

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "No Change"

aliases:
  - /radar/tools/skaffold
---

[Skaffold](https://skaffold.dev/) reports itself as "Fast. Repeatable. Simple."  And it is. Skaffold is to Kubernetes what [[Docker Compose]] is to [[Docker]]. However, it provides build, load, watch, rebuild loop directly on K8s clusters. This makes Skaffold an indispensable developer tool for any [[Shift Left]] org using [[Kubernetes]].

As a developer tool for a certain type of org it is clearly categorized as "adopt". However, despite Google's insistence to the contrary, it is not a good [[Continuous Deployment]] tool. It will always need to be replaced eventually, but we find that the same mindset choose skaffold for CD has often taken other shortcuts that make migration harder than one would expect. Thus we are cautious.
