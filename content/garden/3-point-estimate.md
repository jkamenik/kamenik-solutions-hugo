---
title: "3 Point Estimate"
date: 2023-12-01
lastmod: 2026-05-18
draft: false

keywords:
  - 3 Point Estimate

params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: "Moved In"
---

[3 Point Estimate](https://en.wikipedia.org/wiki/Three-point_estimation)

The [three-point estimation](https://en.wikipedia.org/wiki/Three-point_estimation) technique is used in management and information systems applications for the construction of an approximate probability distribution representing the outcome of future events, based on very limited information. It is very useful in estimating the scope of engineering projects as well.

If your team is struggling with estimating, this might be a viable alternative to simple effort points, which are common in [[Scrum]]. By taking a range of estimates, you can avoid unnecessary debates and over-analysis that often arise during estimation. Many teams will find it easier to estimate dozens of tasks in the same time it would have taken to estimate just a few with [[Planning Poker]].

## Estimates

Before we get to the math, the 3 points in 3-point estimation are the following estimates. For each task, these are the values you need to track. As developers, we recommend estimating in whole number days. However, some teams choose 1/2 days or hours, but we strongly recommend against that.

- `a` - The best-case. This is probably what an expert would say it is. Or someone outside of eng would think it should take.
- `m` - The likely case. This is what you'd arrive at with [[Planning Poker]] or some other consensus estimating technique.
- `b` - The worst-case. This is the "it could possibly take more than..." number.

### The Math

For each task that has been estimated calculate the weighted average and standard deviation:

- $E = \frac{a + 4m + b}6$
- $SD = \frac{b-a}6$

Then calculate the confidence of the project by combining the estimates for each task:

- $E(project) = \sum E(task)$
- $SD(project) = \sqrt{\sum SD(task)^2}$

You can then convert this into a confidence interval for the project:

- 68% = $E(project) \pm SD(project)$
- 90% = $E(project) \pm 1.645 \times SD(project)$
- **95%** = $E(project) \pm 2 \times SD(project)$
- 99.7% = $E(project) \pm 3 \times SD(project)$

95% is usually the target.

With a spreadsheet, this is pretty easy to do.
