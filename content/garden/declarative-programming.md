---
title: "Declarative Programming"
date: 2026-04-16
lastmod: 2026-05-18
draft: false

keywords:
  - Declarative Programming

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/declarative-programming
---

[Declarative programming](https://en.wikipedia.org/wiki/Declarative_programming) describes *what* outcome you want, not the step-by-step procedure to get there. We **adopt** it in DevSecOps: runtimes and controllers reconcile desired state (config, policy, infrastructure, queries) instead of replaying fragile instruction scripts, especially where drift and blast radius matter.

## Blurb

> In computer science, declarative programming is a programming paradigm that expresses the logic of a computation without describing its control flow.

## Summary

Contrast **declarative** with **imperative** code that sequences mutations (`for`, `if`, imperative loops). Declarative forms include SQL (`SELECT …`), configuration and policy specs, functional pipelines, and desired-state manifests. The trade-off: less control flow in the artifact, more work for the engine to plan and apply changes safely.

In this garden, the headline application is **[[Declarative IaC]]** ([[Terraform]], [[Kubernetes]] manifests, [[Helm Chart]] templates, [[HCL]], much [[YAML]]). **[[Imperative IaC]]** and generator-heavy CDKs ([[CDKs]], [[Pulumi]]) are **hold** here, convenient early, painful to reason about at scale. That is a scope choice for infrastructure, not a claim that imperative languages are wrong everywhere (application code, one-off scripts, and glue still use imperative style freely).

## Details

- **Reconciliation:** desired state + diff/apply beats "run these 47 API calls in order" for production systems.
- **Readability:** reviewers see end-state; fewer hidden side effects than procedural generators.
- **Limits:** repetition without modules/macros; complex conditionals can be harder than a small program. Use tool-native abstraction ([[Terraform]] modules, Helm subcharts) instead of abandoning declarative form.
- **Fit:** [[Technique]] item, general paradigm; see [[Declarative IaC]] for IaC-specific guidance and [[Imperative IaC]] for the anti-pattern we avoid in infra.
