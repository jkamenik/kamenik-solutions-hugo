---
title: "Declarative IaC"
date: 2025-01-05
lastmod: 2026-05-17
draft: false

keywords:
  - Declarative IaC

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/declarative-iac
---

[Declarative IaC](https://en.wikipedia.org/wiki/Infrastructure_as_code)

Infrastructure as Code (IaC) is the idea that all infrastructure can (and should) be described as executable code. This allows machines to continually reconcile the code against reality and eliminate drift before it becomes costly. "Declarative" means that the IaC file has minimal logic and declares the end-state.

Declarative IaC should be adopted and [[CDKs]] and other forms of [[Imperative IaC]] should be avoided.

One of the biggest complaints about Declarative IaC is that it often leads to repetitive code. Additionally, the logic can sometimes be unclear or difficult to follow. However, most IaC tools offer code encapsulation features that address these concerns effectively.
