---
title: "mise"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - mise

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - environment-managers
---

[mise](https://mise.jdx.dev/) (formerly rtx) is a polyglot runtime manager: one CLI installs and pins Node, Python, Terraform, Go, and many other tools from `.mise.toml` or `.tool-versions`. We **assess** it as the successor-style alternative to **[[asdf]]** for host-native dev laptops.

## Blurb

> mise is a dev tool for managing your development environment.

## Summary

**What it is:** Fast shim-based version switching with task runner hooks and env var support.

**When to use:** Many repos with different runtime pins; want one entrypoint instead of nvm plus pyenv plus tfenv.

**When to skip:** Team already standardized on **[[Dev Container]]** only.

**Key features:** `mise install`, global and local config, CI-friendly, compatible with asdf plugin ecosystem patterns.


## Details

| Topic | Notes |
|-------|--------|
| **Pairing** | Works with **[[direnv]]** to activate env on `cd` |
| **Contrast** | **[[asdf]]** where legacy plugin investment dominates |

**References**

- [mise documentation](https://mise.jdx.dev/)
