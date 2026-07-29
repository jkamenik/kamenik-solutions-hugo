---
title: Container Structure Test
date: '2023-03-03'
lastmod: '2026-07-29'
draft: false
keywords:
- Container Structure Test
params:
  garden:
    kind: item
    usefulness: adopt
    category: code
    movement: No Change
    subcategories:
    - test-framework
---

[Container Structure Test](https://github.com/GoogleContainerTools/container-structure-test). (Google Container Tools) validates **built container images** before push or deploy: command output, filesystem paths, file contents, and image metadata.

## Blurb

> validate the structure of your container images. Contribute to GoogleContainerTools/container-structure-test development by creating an account on GitHub.

## Summary

**Garden stance:** We **adopt** Container Structure Test for our estate.

**Key points:**

| Topic | Notes |
|-------|--------|
| **Config** | One or more YAML test files; version schema in project docs |
| **CI** | Fail the job on any test failure; pin the CST binary version |
| **Speed** | Faster than booting a cluster; slower than pure unit tests |
| **Scope** | Image contract only, not runtime policy or network behavior |

**References**

- [container-structure-test](https://github.com/GoogleContainerTools/container-structure-test)

## Details

| Topic | Notes |
|-------|--------|
| **Config** | One or more YAML test files; version schema in project docs |
| **CI** | Fail the job on any test failure; pin the CST binary version |
| **Speed** | Faster than booting a cluster; slower than pure unit tests |
| **Scope** | Image contract only, not runtime policy or network behavior |

**References**

- [container-structure-test](https://github.com/GoogleContainerTools/container-structure-test)
