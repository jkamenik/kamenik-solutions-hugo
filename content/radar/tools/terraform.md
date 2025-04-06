---
title: 'Terraform'
date: 2024-04-05
lastmod: 2025-01-05

# Keywords help in classifying content
keywords:
  - Terraform
  - Declarative IaC
  - IaC

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: trial

    # tools, techniques, platforms, languages & frameworks
    quadrant: tools

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "Moved Out"
---

[Terraform](https://www.terraform.io/) has been the defacto standard for {{% wl "Declarative IaC" "IaC" %}}.  However, it was knocked out of its "Adopt" classification in the Tech Radar due to the commercial license change.  This means that it has become too cost-prohibitive for some companies, which have invested in other solutions.

At the time of this writing {{% wl "OpenTofu" %}} -- an open-source fork of Terraform created before the license change to maintain a free and community-driven alternative -- is a compelling option.  However, it will diverge eventually; making choice confounding.  If you can use Terraform, do so.  Otherwise, there are plenty of good alternatives.

<!--more-->

A later announcement by IBM on the purchase of Hashicorp made the license change understandable.  IBM does have a long history of supporting the open source community, but they are a commercial entity. Therefore, we remain cautious about Terraform's future as the de facto standard.
