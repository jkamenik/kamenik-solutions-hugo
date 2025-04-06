---
title: 'Pulumi'
date: 2025-04-05
lastmod: 2025-04-05

# Keywords help in classifying content
keywords:
  - Pulumi
  - Imperative IaC
  - IaC

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: assess

    # tools, techniques, platforms, languages & frameworks
    quadrant: tools

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

[Pulumi](https://www.pulumi.com/) generates IaC based a programming language of your choice.

As with many [Imperative IaC]({{< ref "radar/techniques/imperative-iac" >}}) it suffers from serious drawbacks.  However, for quick-hack lab environments - where the maintainer has little operational experience - it proves a compelling approach.

While many similar tool are "hold" we leave this "assess" because pulumi uses terraform providers under the hood meaning that the actual actions taken and state maintained is that of Terraform.  So this isn't the worst stepping stone in the world of IaC.

<!--more-->

If you are in a company that cannot or will not use Terraform and you have a mature enough team to actively avoid the pitfalls of Imperative IaC then this is a very competent solution.  Otherwise steer clear because you are going to end up in a worst place than just building by hand.
