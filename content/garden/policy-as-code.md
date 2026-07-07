---
title: Policy as Code
date: '2025-06-14'
lastmod: '2026-07-02'
draft: false
keywords:
- Policy as Code
params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
---

[Policy as Code](https://www.openpolicyagent.org/) is the practice of expressing compliance, security, and operational rules as version-controlled, machine-executable code , enforced automatically in the pipeline rather than reviewed manually after the fact. We **adopt** it under **[[Technique]]** in the garden.

## Summary

Policy as Code is a strong adopt in any [[DevSecOps]] or regulated environment. Manual compliance reviews don't scale and introduce human error; codified policies run on every PR, in every environment, consistently. Start with the highest-risk surface (Kubernetes admission, IaC security rules) and expand from there. OPA + [[Conftest]] is the recommended starting point , the learning curve for Rego is real but the payoff in automated governance is significant. Pairs well with [[GitOps]]: policy checks become just another gate in the pull request pipeline.

---
