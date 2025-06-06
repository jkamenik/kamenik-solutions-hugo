---
title: 'DRY'
date: 2025-01-05
lastmod: 2025-01-05

# Keywords help in classifying content
keywords:
  - DRY
  - anti-pattern

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: hold

    # tools, techniques, platforms, languages & frameworks
    quadrant: techniques

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "Moved Out"
---

Don't Repeat Yourself is a technique aimed at reducing repetition of code.

While the assertion that repeated code is harder to maintain and therefore error prone is true, the way that DRY is implemented is often wrong and leads to increasingly complex code with more abstractions than necessary.  It also leads to premature optimization and various other anti-patterns which increase the blast radius of changes.

In the {{% wl IaC %}} world, minimizing blast radius is paramount.  Therefore a little repeated code here and there is a small price to pay for a robust infrastructure.

<!--more-->

## Resources

- https://en.wikipedia.org/wiki/Don%27t_repeat_yourself
- https://dev.to/ralphcone/please-do-repeat-yourself-dry-is-dead-1jbg
- https://dev.to/jeroendedauw/the-fallacy-of-dry
