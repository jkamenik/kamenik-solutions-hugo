---
title: "Docker Swarm"
date: 2024-04-09
lastmod: 2026-05-17
draft: false

keywords:
  - Docker Swarm

params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: "Moved Out"

aliases:
  - /radar/platforms/docker-swarm
---

[Docker Swarm](https://docs.docker.com/engine/swarm/)

As of 2025 swarm maintenance has been to a separate company from the one that maintains [[Docker]]. We therefore recommend you avoid this platform.

Originally Docker Swarm was billed as an alternative to [[Kubernetes]]. However, when that didn't get traction it changed course and retooled as way to bridge [[Docker Compose]] to a multi-machine setup. However, there are some issues with stateful data that - due to the lack of on-going support - will likely not be solved.
