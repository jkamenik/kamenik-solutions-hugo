---
title: 'Docker Swarm'
date: 2024-04-09
lastmod: 2025-05-10

# Keywords help in classifying content
keywords:
  - Docker Swarm
  - Docker
  - Containers
  - Orchestration

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: hold

    # tools, techniques, platforms, languages & frameworks
    quadrant: platforms

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "Moved Out"
---

As of 2025 swarm maintenance has been to a separate company from the one that maintains {{% wl Docker %}}.  We therefore recommend you avoid this platform.

Originally Docker Swarm was billed as an alternative to {{% wl Kubernetes %}}.  However, when that didn't get traction it changed course and retooled as way to bridge {{% wl "Docker Compose" %}} to a multi-machine setup.  However, there are some issues with stateful data that - due to the lack of on-going support - will likely not be solved.
