---
title: 'Cloud'
date: 2025-05-11
lastmod: 2025-05-11

aliases:
  - radar/techniques/cloud-computing
  - radar/techniques/infrastructure-as-a-service
  - radar/techniques/platform-as-a-service

# Keywords help in classifying content
keywords:
  - Cloud
  - Cloud Computing
  - IaaS
  - Infrastructure as a Service
  - Platform as a Service
  - PaaS
  # - Software as a Service
  # - SaaS

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

At its most basic, "Cloud" just means someone else's computer. More importantly, it refers to shared infrastructure that is managed and configured programmatically. This infrastructure can be used as a base for customers to build on. It is also known as Infrastructure as a Service (IaaS) or Platform as a Service (PaaS).

Historically, {{% wl "AWS" %}} was the first true cloud provider. Amazon sought to offset the operational costs of infrastructure that was heavily utilized during Black Friday and the lead-up to Christmas but remained largely idle at other times. Their revolutionary approach eliminated the need to consider physical hardware, replacing it with configurable options.

Many years on and all the major cloud offerings have the same set of base offerings, like object storage, network attached storage, VMs.  Then on top of that they also have ubiquitous managed offerings like {{% wl "Postgres" %}}, {{% wl "Kubernetes" %}}, and {{% wl "Serverless" %}}.  Specifics are different, but the concepts are all the same.  And for this reason, if you are a modern DevOps then you must the cloud concepts.
