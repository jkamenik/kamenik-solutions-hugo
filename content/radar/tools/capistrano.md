---
title: 'Capistrano'
date: 2023-04-05
lastmod: 2025-01-05

# Keywords help in classifying content
keywords:
  - Capistrano
  - IaC
  - Imperative IaC

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: hold

    # tools, techniques, platforms, languages & frameworks
    quadrant: tools

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

[Capistrano](https://capistranorb.com/) is a remote server automation and deployment tool written in Ruby.

While this tool helped to usher in the practice of DevOps using {{% wl "Ruby" %}} as a {{% wl "DSL" %}} it was born before the time of [Declarative IaC]({{< ref "radar/techniques/declarative-iac" >}}).  And as with many [Imperative IaC]({{< ref "radar/techniques/imperative-iac" >}}) tools the IaC is error prone and becomes unmaintainable long term.  It has long since been replaced better tools and should be abandoned if at possible.

<!--more-->

Things to use instead:
- {{% wl "Ansible" %}}
- {{% wl "Terraform" %}}
- {{% wl Kubernetes %}}
