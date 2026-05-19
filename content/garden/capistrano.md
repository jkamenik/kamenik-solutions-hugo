---
title: "Capistrano"
date: 2023-04-05
lastmod: 2026-05-18
draft: false

keywords:
  - Capistrano

params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: "No Change"
    subcategories:
      - ci-cd-tools

aliases:
  - /radar/tools/capistrano
---

[Capistrano](https://capistranorb.com/) is a **[[Ruby]]** remote-deployment DSL: SSH into servers, run recipes (`cap deploy`), symlink releases; classic 2000s **[[Ruby on Rails]]** ops. We rate it **hold**: it predates **[[Declarative IaC]]** and **[[GitOps]]**; imperative deploy scripts drift, hide blast radius, and fight container-native workflows.

## Blurb

> Capistrano is a framework for building automated deployment scripts.

## Summary

**Why hold:** serial SSH orchestration with mutable servers is the opposite of reconciled desired state. Recipes become tribal knowledge; rollbacks depend on symlink tricks; secrets and host lists rot in repo or `.cap` config.

**Historical credit:** helped teams practice repeatable deploys before modern **[[DevSecOps]]**, but that problem is better solved today without Capistrano.

**Use instead**

| Need | Prefer |
|------|--------|
| Configure existing VMs | **[[Ansible]]** (adopt, last-resort second touch) |
| Provision cloud shape | **[[Terraform]]** + **[[Declarative IaC]]** |
| Run the app | **[[Kubernetes]]** + **[[ArgoCD]]** (GitOps CD) |
| Legacy Rails monolith | Strangle to containers/CI; don’t extend Capistrano |

## Details

- **Imperative IaC:** same failure mode as **[[Imperative IaC]]** generators; hard to review, hard to test, hard to audit.
- **Migration:** freeze Capistrano recipes; mirror deploy steps in pipeline + declarative infra; retire SSH-based deploy users when apps move to K8s or immutable images.
