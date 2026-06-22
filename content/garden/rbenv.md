---
title: "rbenv"
date: 2026-06-12
lastmod: 2026-06-22
draft: false

keywords:
  - rbenv

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - environment-managers
---

[rbenv](https://github.com/rbenv/rbenv) manages **[[Ruby]]** versions per project with `.ruby-version` and lightweight shims. We **assess** it for Ruby maintenance work on **[[Ruby on Rails]]** estates; greenfield polyglot laptops prefer **[[mise]]**.

## Blurb

> rbenv is a version manager for Ruby.

## Summary

**What it is:** Installs Rubies via ruby-build plugin; selects version per directory.

**When to use:** Rails repos with committed `.ruby-version`; developers prefer rbenv over system Ruby.

**When to skip:** Team uses **[[Dev Container]]** or **[[mise]]** for all language pins.

**Key features:** Shim dispatch, `rbenv local/global`, plugin ecosystem.


## Details

| Topic | Notes |
|-------|--------|
| **Fit** | Common in legacy **[[Ruby on Rails]]** shops |
| **Contrast** | **[[mise]]** when Ruby is one of many pinned runtimes |

**References**

- [rbenv documentation](https://github.com/rbenv/rbenv#readme)
