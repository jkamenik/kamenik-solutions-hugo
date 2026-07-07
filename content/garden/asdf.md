---
title: asdf
date: '2026-06-12'
lastmod: '2026-07-02'
draft: false
keywords:
- asdf
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - environment-managers
---

[asdf](https://asdf-vm.com/) is a tool we **assess** in the garden.

## Blurb

> Manage multiple runtime versions with a single CLI tool

## Summary

**What it is:** Core plus community plugins (Node, Ruby, Python, Terraform, etc.) with shim dispatch.

**When to use:** Teams already committed to asdf plugins and `.tool-versions` in repos.

**When to skip:** Greenfield laptops where **[[mise]]** performance and UX win evals.

**Key features:** `.tool-versions`, plugin add/update, legacy breadth of plugins.

## Details

| Topic | Notes |
|-------|--------|
| **Practice** | Commit `.tool-versions`; document required plugins in README |
| **CI** | Mirror versions in **[[GitHub Actions]]** setup actions |

**References**

- [asdf documentation](https://asdf-vm.com/guide/getting-started.html)
