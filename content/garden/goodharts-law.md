---
title: Goodhart's Law
date: '2026-08-11'
lastmod: '2026-08-11'
draft: false
keywords:
- Goodhart's Law
- Goodhart's principle
params:
  aliases:
  - Goodhart's principle
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
---

[Goodhart's Law](https://en.wikipedia.org/wiki/Goodhart%27s_law) is the principle that once a metric becomes a target it stops measuring what it was meant to measure. We **adopt** it because experience shows it explains why dashboards and incentives quietly drift from real goals.

## Blurb

> "When a measure becomes a target, it ceases to be a good measure."

## Summary

Use Goodhart's Law as a check when picking KPIs, SLAs, post-incident metrics, or any number that people get rewarded for. The risk is that teams optimize to the number, not the outcome, and the number goes up while the goal goes sideways.

The insight can be freeing: do not stress over finding the perfect metric, because it does not exist. So rather than chasing one ideal number, pick several metrics and read them together. How the metrics behave relative to each other matters more than any raw number alone.

Key trade-offs:

- Numbers are easy to observe but easy to game. Blunt proxies invite Goodhart drift.
- Collecting perfect measures is impossible. The trick is not to turn imperfect measures into fiat targets.
- Correlate metrics against each other instead of reading each one alone.

Example: rising Error rate with nothing else changed points to bad requests. Rising Error rate and Latency together points to a resource problem somewhere. The signal comes from the relationship, not the numbers.

Related garden notes: [[DORA Metrics]], [[SLAs]], [[Continuous Delivery]], [[Incident Management]].

## Details

Goodhart's Law is attributed to economist Charles Goodhart, first stated in a 1975 paper on monetary policy. It is closely related to the observer effect and to game theory ideas about incentives and perverse outcomes. In software it is cited most often around delivery metrics, on-call metrics, and any metric tied to a reward.

Common mitigating practices:

- Review chosen targets with the "does this still measure the outcome" question each quarter.
- Prefer scorecards with several measures over one headline number.
- Keep an eye on metric whores: numbers that rise without outcome improving are a signal of Goodhart drift.
