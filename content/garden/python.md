---
title: "Python"
date: 2025-12-08
lastmod: 2026-05-18
draft: false

keywords:
  - Python

params:
  garden:
    kind: item
    usefulness: trial
    category: code
    movement: "No Change"
    subcategories:
      - language

aliases:
  - /radar/languages/python
---

[Python](https://www.python.org/) is a general-purpose language with dominant libraries in automation, data, and ML. We rate it **trial**: expect to read and maintain Python when your stack already depends on it ([[Ansible]], notebooks, data pipelines), but prefer faster or stricter languages for latency-sensitive services unless the team standardizes on Python end-to-end.

## Blurb

> Python is a programming language that lets you work quickly and integrate systems more effectively.

## Summary

Python grew out of academia and scripting culture: batteries-included stdlib, readable syntax, and a huge PyPI ecosystem made it the default glue for DevOps ([[Ansible]] controllers), scientific computing (NumPy, pandas), and ML tooling. That ubiquity is both strength and trap, teams often reach for Python because a library exists, then inherit GIL limits, packaging drift, and runtime cost at scale.

Treat Python as a **toolchain language**: adopt it where the framework or community is Python-first; for new backend services, compare [[GoLang]] (ops and concurrency), [[Ruby]] (legacy web), or typed stacks before defaulting to Python for convenience alone.

## Details

- **Where it wins:** config management controllers, data/ML notebooks, quick automation, teaching and prototypes, AWS CDK / [[Pulumi]] when you already committed to imperative IaC (see [[CDKs]] and garden notes on [[Imperative IaC]]).
- **Where it hurts:** CPU-bound APIs, tight tail latency, and large multi-process deployments without careful architecture (async, workers, native extensions).
- **Operations:** virtualenv/uv/poetry discipline matters; pin dependencies in CI; avoid sprawling monoliths without type hints or tests.
- **Pair with:** [[Ansible]] (adopt tool, Python on control node); contrast [[GoLang]] for infra CLIs and long-running services.
