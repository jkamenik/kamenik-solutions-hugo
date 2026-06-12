---
title: "CDKs"
date: 2025-04-10
lastmod: 2026-05-18
draft: false

keywords:
  - CDKs

params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: "No Change"
---

[CDKs](https://aws.amazon.com/cdk/)

Cloud Development Kits ([AWS CDK](https://aws.amazon.com/cdk/) and similar) generate infrastructure from general-purpose programming languages. They are a form of [[Imperative IaC]]: convenient for prototypes, but they obscure blast radius and often lead to regret at scale. We rate CDKs **hold** for the same reasons as [[Pulumi]]; prefer [[Declarative IaC]] with [[Terraform]] when your team can use it.
