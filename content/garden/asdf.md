---
title: "asdf"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - asdf

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - environment-managers
---

[asdf](https://asdf-vm.com/) is a plugin-based version manager for multiple languages and CLIs via a single `.tool-versions` file. We **assess** it on estates with existing asdf plugins; new polyglot setups may prefer **[[mise]]**.

## Blurb

> asdf is a CLI tool that can manage multiple language runtime versions on a per-project basis.

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
