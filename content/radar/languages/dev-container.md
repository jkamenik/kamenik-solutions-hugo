---
title: 'Dev Container'
date: 2025-04-23
lastmod: 2025-04-23

# Keywords help in classifying content
keywords:
  - Dev Container
  - Container
  - DevEx
  - IaC

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: adopt

    # tools, techniques, platforms, languages & frameworks
    quadrant: languages

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

[Dev Container](https://containers.dev/) was a system born in {{% wl "VS Code" %}} that allowed the IDE to boot a container and use it as its development runtime.  The benefits of this are huge: no longer does each developer need to set up a development machine, no longer does one developer's effort have to be manually replicated by all others, no longer is there a skew between dev, CI, and production.  There simply is shared {{% wl "Declarative IaC" "Infrastructure as Code" %}} (IaC) which is used to build all of those.  And because of these benefits, Dev Container is very much in the adopt ring.

<!--more-->
