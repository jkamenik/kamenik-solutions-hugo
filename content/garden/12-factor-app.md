---
title: 12 Factor App
date: '2023-07-23'
lastmod: '2026-07-02'
draft: false
keywords:
- 12 Factor App
params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
---

[12 Factor App](https://12factor.net/). The [12-factor](https://12factor.net/) methodology is designed for building SaaS services that are declarative, clean, maximally portable, and minimally divergent.

## Blurb

> A methodology for building modern, scalable, maintainable software-as-a-service apps.

## Summary

**Garden stance:** We **adopt** 12 Factor App for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

The twelve factors are a shared vocabulary for service design. They do not prescribe a single stack. They do constrain how code, config, and ops interleave so teams can swap platforms without rewriting apps.

**Config (III):** A litmus test from the spec is whether the codebase could go open source without leaking credentials. Use environment variables per deploy, not grouped "environment" files checked into the repo.

**Processes (VI) and concurrency (VIII):** Persist data in backing services (Postgres, Redis, object storage), not local disk on the app instance. Scale by adding processes, not by making one process bigger.

**Build, release, run (V):** CI produces an immutable release artifact; config binds at deploy time. Avoid editing running containers by hand.

**Dev/prod parity (X):** Same backing service types in every stage; time gaps between deploys should be hours, not months.

**References**

- [The Twelve-Factor App](https://12factor.net/)
- [Twelve-Factor App methodology (Wikipedia)](https://en.wikipedia.org/wiki/Twelve-Factor_App_methodology)
