---
title: 'Kubernetes'
date: 2025-04-24
lastmod: 2025-05-10

# Keywords help in classifying content
keywords:
  - Kubernetes

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: trial

    # tools, techniques, platforms, languages & frameworks
    quadrant: platforms

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

[Kubernetes](https://kubernetes.io/docs/concepts/overview/), also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications. Unlike many systems before it, Kubernetes is fully multi-cloud and truly planet-scale. At the time of this writing, there is a theoretical limit of a single cluster having 25 million nodes, with each node having thousands of CPUs and millions of GPUs. In practice, clusters tend to be much smaller than that, but they also tend to be very dynamic and scale as needed.

It uses a {{% wl YAML %}} based {{% wl "Declarative IaC" %}} syntax to orchestrate {{% wl "containerization" Containers %}}.  While there are alternatives like {{% wl Nomad %}}, {{% wl "Docker Swarm" %}}, and {{% wl DCOS %}}, realistically, they each have limitations that Kubernetes does not, making it likely that you will decide to (or be forced to) migrate.

If you want to avoid cloud vendor lock-in or operate in a {{% wl "Hybrid Cloud" %}} environment, Kubernetes is essential.
