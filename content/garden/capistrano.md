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
  garden:
    usefulness: hold
    category: tool
    movement: "No Change"

aliases:
  - /radar/tools/capistrano

---

[Capistrano](https://capistranorb.com/) is a remote server automation and deployment tool written in Ruby.

While this tool helped to usher in the practice of DevOps using {{% wl "Ruby" %}} as a {{% wl "DSL" %}} it was born before the time of [Declarative IaC]({{< ref "declarative-iac" >}}).  And as with many [Imperative IaC]({{< ref "imperative-iac" >}}) tools the IaC is error prone and becomes unmaintainable long term.  It has long since been replaced better tools and should be abandoned if at possible.

<!--more-->

Things to use instead:
- {{% wl "Ansible" %}}
- {{% wl "Terraform" %}}
- {{% wl Kubernetes %}}
