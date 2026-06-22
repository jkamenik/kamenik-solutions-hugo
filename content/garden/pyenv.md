---
title: "pyenv"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - pyenv

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - environment-managers
---

[pyenv](https://github.com/pyenv/pyenv) installs and selects **[[Python]]** versions per project via `.python-version`. We **assess** it for Python-only host workflows; polyglot pins belong in **[[mise]]** or **[[asdf]]**.

## Blurb

> pyenv lets you easily switch between multiple versions of Python.

## Summary

**What it is:** Shim-based Python version manager, often paired with pyenv-virtualenv.

**When to use:** Python-heavy local dev without containers; legacy repos with `.python-version` committed.

**When to skip:** **[[Dev Container]]** defines Python for the team. Use **[[mise]]** when Node and Terraform share the same repo pins.

**Key features:** `pyenv install`, global/local version files, plugin ecosystem.


## Details

| Topic | Notes |
|-------|--------|
| **Pairing** | **[[direnv]]** + `layout python` patterns in `.envrc` |
| **CI** | Pin Python explicitly in **[[GitHub Actions]]** |

**References**

- [pyenv documentation](https://github.com/pyenv/pyenv#readme)
