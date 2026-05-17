---
title: "DRY"
date: 2025-01-05
lastmod: 2026-05-17
draft: false

keywords:
  - DRY

params:
  garden:
    kind: item
    usefulness: hold
    category: technique
    movement: "Moved Out"

aliases:
  - /radar/techniques/dry
  - /radar/techniques/dry
---

[DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)

Don't Repeat Yourself is a technique aimed at reducing repetition of code.

While the assertion that repeated code is harder to maintain and therefore error prone is true, the way that DRY is implemented is often wrong and leads to increasingly complex code with more abstractions than necessary. It also leads to premature optimization and various other anti-patterns which increase the blast radius of changes.

In the [[IaC]] world, minimizing blast radius is paramount. Therefore a little repeated code here and there is a small price to pay for a robust infrastructure.

## Resources

- https://en.wikipedia.org/wiki/Don%27t_repeat_yourself
- https://dev.to/ralphcone/please-do-repeat-yourself-dry-is-dead-1jbg
- https://dev.to/jeroendedauw/the-fallacy-of-dry
