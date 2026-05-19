---
title: "Imperative IaC"
date: 2025-01-05
lastmod: 2026-05-18
draft: false

keywords:
  - Imperative IaC

params:
  garden:
    kind: item
    usefulness: hold
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/imperative-iac
---

[Imperative IaC](https://en.wikipedia.org/wiki/Infrastructure_as_code)

Imperative IaC is using a programming language to generate the IaC code. This is often seen as a boon since the number one complaint about [[Declarative IaC]] is that it is not DRY enough. And being able to use the suite of programming refactoring tools seems great.

However, the two main goals of IaC are decreased blast radius and security over time, which imperative IaC makes impossible. Almost all clients we have worked with have regretted the choice of Imperative IaC tools like [[Pulumi]] and [[AWS CDK]]. While imperative IaC code might be smaller, the side effects of simple changes are vastly more complicated to understand, which makes responding to change risky, and error prone.

More often than not our first order is to use a tool like [[terraformer|`terraformer`]] to generate raw IaC from the state of the cloud account and then painstakingly refactor the IaC correctly as it should have been originally. Through use of proper [[IaC refactoring]] technique we arrive at code that is both clean and maintainable with minimal repetition, rendering promises of Imperative IaC moot and thus we move this to hold.
