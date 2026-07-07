---
title: CEL
date: '2025-06-15'
lastmod: '2026-07-02'
draft: false
keywords:
- CEL
params:
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: No Change
    subcategories:
    - language
---

[CEL](https://github.com/google/cel-spec). Common Expression Language (CEL) is Google's sandboxed, non-Turing-complete expression language designed for high-frequency evaluation in security and policy contexts.

## Blurb

> Common Expression Language -- specification and binary representation - cel-expr/cel-spec

## Summary

CEL sits between a simple expression evaluator and a full policy language like Rego ([[Policy as Code]] / OPA). For [[Kubernetes]] specifically, the native `ValidatingAdmissionPolicy` integration in 1.26+ is a compelling reason to learn it , it removes the operational burden of running a separate admission webhook. For more complex, cross-cutting policy logic, OPA/Rego via [[Conftest]] remains more capable. Assess CEL if you are already invested in the Kubernetes control plane; it will likely become unavoidable there.

---
