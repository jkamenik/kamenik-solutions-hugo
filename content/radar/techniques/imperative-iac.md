---
title: 'Imperative IaC'
date: 2025-01-05
lastmod: 2025-01-05

# Keywords help in classifying content
keywords:
  - Imperative IaC
  - IaC
  - anti-pattern

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: hold

    # tools, techniques, platforms, languages & frameworks
    quadrant: techniques

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

Imperative IaC is using a programming language to generate the IaC code.  This is often seen as a boon since the number one complaint about Declarative IaC is that it is not DRY enough.  And being able to use the suite of programming refactoring tools seems great.

However, the two main goals of IaC are decreased blast radius and security over time, which imperative IaC makes impossible.  Almost all clients we have worked have regretted the choice of Imperative IaC tools like Pulumi and AWS CDK.  While their code is indeed smaller, the side effects of simple changes are vastly more complicated to understand, which makes responding to change risky, and error prone.

<!--more-->

More often then note our first order is to us a tool like `terraformer` to generate raw IaC from the state of the cloud account and then painstakingly refactor the IaC correctly as it should have been originally.  Though use of proper IaC refactoring technique we arrive code that is both clean and maintainable with minimal repetition.
