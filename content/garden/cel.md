---
title: "CEL"
date: 2025-06-15
lastmod: 2026-05-18
draft: false

keywords:
  - CEL

params:
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: "No Change"
    subcategories:
      - language
---

[CEL](https://github.com/google/cel-spec)

Common Expression Language (CEL) is Google's sandboxed, non-Turing-complete expression language designed for high-frequency evaluation in security and policy contexts. It intentionally has no side effects, no I/O, and no loops , just deterministic expression evaluation over structured data. This makes it safe to embed directly in control planes without the overhead of a full policy engine.

CEL is gaining traction in the [[Kubernetes]] ecosystem: as of k8s 1.26, `ValidatingAdmissionPolicy` uses CEL natively, reducing the need for external webhook-based admission controllers. It is also used in Firebase security rules, Google IAM conditions, and Envoy RBAC. Worth assessing if you are managing [[Kubernetes]] clusters or building systems that need embeddable, user-defined policy expressions.

## Blurb

> CEL is a non-Turing complete language designed for simplicity, speed, safety, and portability. CEL evaluates expressions and is intended to be embedded in applications for use cases from config validation to policy enforcement.

## Summary

CEL sits between a simple expression evaluator and a full policy language like Rego ([[Policy as Code]] / OPA). For [[Kubernetes]] specifically, the native `ValidatingAdmissionPolicy` integration in 1.26+ is a compelling reason to learn it , it removes the operational burden of running a separate admission webhook. For more complex, cross-cutting policy logic, OPA/Rego via [[Conftest]] remains more capable. Assess CEL if you are already invested in the Kubernetes control plane; it will likely become unavoidable there.
