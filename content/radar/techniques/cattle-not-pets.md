---
title: 'Cattle Not Pets'
date: 2025-04-07
lastmod: 2025-05-10

# Keywords help in classifying content
keywords:
  - Cattle Not Pets
  - IaC
  - Fungible

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: adopt

    # tools, techniques, platforms, languages & frameworks
    quadrant: techniques

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

Once upon a time we treated servers like pets.  We gave them names, allowed them to become unique, and spend a lot of time caring for them individually.  This didn't scale so we increasing made the pets do more and more and it was catastrophic when they died.

Cattle are numbered, identical, fungible (interchangeable and replaceable without loss of value), follow instructions, and are replaced when they fail.  This facilitates almost all modern software practices.  Things like {{% wl "containerization" "containers" %}}, {{% wl "Kubernetes" %}}, {{% wl "Software as a Service" %}}, or {{% wl Cloud %}} wouldn't exist without this technique.  Therefore it is an absolute must.

<!--more-->

## References

https://cloudscaling.com/blog/cloud-computing/the-history-of-pets-vs-cattle/
