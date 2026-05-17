---
title: "Pulumi"
date: 2024-04-05
lastmod: 2026-05-17
draft: false

keywords:
  - Pulumi

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "No Change"

aliases:
  - /radar/tools/pulumi
---

[Pulumi](https://www.pulumi.com/) generates IaC based a programming language of your choice.

As with many [[Imperative IaC]] it suffers from serious drawbacks. However, for quick-hack lab environments - where the maintainer has little operational experience - it proves a compelling approach.

While many similar tools are "hold" we leave this "assess" because Pulumi uses Terraform providers under the hood meaning that the actual actions taken and state maintained is that of Terraform. So this isn't the worst stepping stone in the world of IaC.

If you are in a company that cannot or will not use Terraform and you have a mature enough team to actively avoid the pitfalls of Imperative IaC then this is a very competent solution. Otherwise steer clear because you are going to end up in a worst place than just building by hand.
