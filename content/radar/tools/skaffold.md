---
title: 'Skaffold'
date: 2024-04-25
lastmod: 2025-01-05

# Keywords help in classifying content
keywords:
  - Skaffold
  - Kubernetes
  - Dev Tool

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: trial

    # tools, techniques, platforms, languages & frameworks
    quadrant: tools

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

[Skaffold](https://skaffold.dev/) reports itself as "Fast. Repeatable. Simple."  And it is.  Skaffold is to Kubernetes what {{% wl "Docker Compose" %}} is to {{% wl "Docker" %}}.  However, it provides build, load, watch, rebuild loop directly on K8s clusters.  This makes Skaffold an indispensable developer tool for any {{% wl "Shift Left" %}} org using {{% wl "Kubernetes" %}}.

<!--more-->

As a developer tool for a certain type of org it is clearly categorized as "adopt".  However, despite Google's insistence to the contrary, it is not a good {{% wl "Continuous Deployment" %}} tool.  It will always need to be replaced eventually, but we find that the same mindset choose skaffold for CD has often taken other shortcuts that make migration harder than one would expect.  Thus we are cautious.
