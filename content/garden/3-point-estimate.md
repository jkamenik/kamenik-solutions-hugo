---
title: 3 Point Estimate
date: '2023-12-01'
lastmod: '2026-07-02'
draft: false
keywords:
- 3 Point Estimate
params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: No Change
---

[3 Point Estimate](https://en.wikipedia.org/wiki/Three-point_estimation) is a technique we **assess** in the garden.

## Summary

**When to use:**

- Teams stuck in [[Scrum]] story-point debates or long [[Planning Poker]] sessions without better forecasts.
- Stakeholders who need a range (68%, 90%, 95%) rather than one total.
- Engineering projects where limited information still requires a defensible rollup.

**When to skip:**

- The team will not maintain three numbers per task.
- Precision would be theater without tracking actuals against forecast.

| Approach | Tradeoff |
|----------|----------|
| [[Planning Poker]] | Fast consensus on one `m` value; weak on uncertainty |
| Story points | Common in [[Scrum]]; often debated without probabilistic rollup |
| Three-point | More fields per task; project-level confidence from task SD rollup |

If your team struggles with estimating, three-point ranges can reduce over-analysis compared to arguing a single effort number. Many teams can estimate dozens of tasks in the time it took to estimate a few with [[Planning Poker]].

## Details

### Three Points Per Task

For each task, track three values:

- `a` - The best case. This is probably what an expert would say. Or someone outside of engineering would think it should take.
- `m` - The likely case. This is what you would arrive at with [[Planning Poker]] or another consensus technique.
- `b` - The worst case. This is the "it could possibly take more than..." number.

### The Math

For each estimated task, calculate the weighted average and standard deviation:

- $E = \frac{a + 4m + b}6$
- $SD = \frac{b-a}6$

Roll up to the project:

- $E(project) = \sum E(task)$
- $SD(project) = \sqrt{\sum SD(task)^2}$

Confidence intervals:

- 68% = $E(project) \pm SD(project)$
- 90% = $E(project) \pm 1.645 \times SD(project)$
- **95%** = $E(project) \pm 2 \times SD(project)$
- 99.7% = $E(project) \pm 3 \times SD(project)$

95% is usually the target.

With a spreadsheet, rollup and intervals are straightforward.
