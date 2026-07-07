---
title: Helm Unittest
date: '2023-07-23'
lastmod: '2026-07-02'
draft: false
keywords:
- Helm Unittest
params:
  garden:
    kind: item
    usefulness: adopt
    category: code
    movement: No Change
    subcategories:
    - test-framework
---

[Helm Unittest](https://github.com/helm-unittest/helm-unittest) is a code we **adopt** in the garden.

## Blurb

> BDD styled unit test framework for Kubernetes Helm charts as a Helm plugin. - helm-unittest/helm-unittest

## Summary

Chart authors encode scenarios as test files under `tests/` (or similar): set values, render templates, and compare output to expected YAML or snapshots. This is far faster and more deterministic than only testing in a live cluster, and it documents expected behavior for reviewers.

## Details

- **Workflow:** install the plugin (`helm plugin install https://github.com/helm-unittest/helm-unittest`); run `helm unittest` in the chart directory in CI.
- **Assertions:** document presence, equals, match regex, snapshot files, and suite-level setup/teardown for values files.
- **Fit:** essential when you ship [[Helm Chart]] artifacts to customers or run many value permutations (dev/stage/prod).
- **Limits:** tests template output, not cluster behavior, pair with integration tests for admission, CRDs, and hooks.
- **Note:** superseded the earlier `quintush/helm-unittest` fork; use the `helm-unittest` org repository.
