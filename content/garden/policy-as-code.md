---
title: "Policy as Code"
date: 2025-06-14
lastmod: 2026-05-18
draft: false

keywords:
  - Policy as Code

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"
---

[Policy as Code](https://www.openpolicyagent.org/)

Policy as Code is the practice of expressing compliance, security, and operational rules as version-controlled, machine-executable code , enforced automatically in the pipeline rather than reviewed manually after the fact. It is a direct application of [[Shift Left]] thinking to governance: if a policy can be checked by a machine, it should be, and it should fire before anything reaches production.

Policies cover a wide surface: Kubernetes admission control, IaC compliance ([[Terraform]], [[Helm]] chart rules), API authorization, network firewall rules, and [[DevSecOps]] audit requirements. The leading engine is Open Policy Agent (OPA), which uses the Rego language and integrates across the stack via [[Conftest]] (for config files) and [[Regula]] (for IaC).

## Blurb

> OPA is an open source, general-purpose policy engine that unifies policy enforcement across the stack. OPA provides a high-level declarative language (Rego) that lets you specify policy as code and exposes simple APIs to offload policy decision-making from your software.

## Summary

Policy as Code is a strong adopt in any [[DevSecOps]] or regulated environment. Manual compliance reviews don't scale and introduce human error; codified policies run on every PR, in every environment, consistently. Start with the highest-risk surface (Kubernetes admission, IaC security rules) and expand from there. OPA + [[Conftest]] is the recommended starting point , the learning curve for Rego is real but the payoff in automated governance is significant. Pairs well with [[GitOps]]: policy checks become just another gate in the pull request pipeline.
