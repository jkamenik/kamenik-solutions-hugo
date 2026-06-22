---
title: "conda"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - conda

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - environment-managers
---

[conda](https://docs.conda.io/) (Anaconda/Miniconda) manages Python and non-Python binary dependencies in isolated environments. We **assess** it for data science stacks with heavy native libs; application services usually prefer **[[Dev Container]]** or **[[pyenv]]** plus normal package managers.

## Blurb

> conda is an open-source package and environment management system.

## Summary

**What it is:** `environment.yml`, channel-based packages, conda-forge ecosystem, cross-platform binaries.

**When to use:** ML/data notebooks needing CUDA, BLAS, or scientific stacks that pip alone struggles with.

**When to skip:** Standard web services on **[[Python]]** with wheels available on PyPI.

**Key features:** `conda create`, exportable env files, mamba faster solver (community).


## Details

| Topic | Notes |
|-------|--------|
| **Fit** | Data science laptops, not typical **[[GitHub Actions]]** service CI |
| **Contrast** | **[[pyenv]]** + venv for app dev; **[[Nix]]** for fully declarative hermetic shells |

**References**

- [conda documentation](https://docs.conda.io/en/latest/)
