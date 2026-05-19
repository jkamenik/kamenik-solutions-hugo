---
title: "Single Responsibility Principle"
date: 2025-05-13
lastmod: 2026-05-18
draft: false

keywords:
  - Single Responsibility Principle
  - SRP

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/single-responsibility-principle
---

[Single Responsibility Principle](https://en.wikipedia.org/wiki/Single-responsibility_principle)

The Single Responsibility Principle (SRP) is the **S** in [[SOLID]]. A module, class, or function should have one (and only one) reason to change. In practice this means each unit of code owns a single concern: a data transformer shouldn't also handle I/O, a config parser shouldn't also validate business rules.

SRP is not about making things small for its own sake. It is about coupling: when a piece of code changes for two different reasons, those two reasons will eventually conflict, and every change risks breaking the other concern. Keeping responsibilities separate keeps change surfaces small and test boundaries clean.

## Blurb

> A class should have one, and only one, reason to change. , Robert C. Martin

## Summary

SRP is foundational to maintainable, testable code and applies at every level of granularity (functions, classes, services, and microservices. Violations are usually visible as functions with "and" in their name, classes with unrelated method clusters, or modules that import from two completely different domains. The fix is almost always to extract: pull the second concern into its own unit with a clear interface. Adopt unconditionally) this principle pays dividends at every scale.
