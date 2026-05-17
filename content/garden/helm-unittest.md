---
title: "Helm Unittest"
date: 2023-07-23
lastmod: 2026-05-17
draft: false

keywords:
  - Helm Unittest

params:
  garden:
    kind: item
    usefulness: adopt
    category: code
    movement: "No Change"
    subcategories:
      - framework
      - test-framework

aliases:
---

[Helm unittest](https://github.com/helm-unittest/helm-unittest) is a Helm plugin that unit-tests [[Helm Chart]] templates with YAML-defined suites instead of spinning up a cluster. It renders charts with `helm template`, then asserts on manifests (values, snapshots, document counts, and custom matchers). If you maintain charts in [[Kubernetes]], adopt this alongside [[Unit Testing]] for application code—it catches template regressions before CI deploys.

## Blurb

> Unit tests for Helm charts in YAML to keep your charts consistent and robust.

## Summary

Chart authors encode scenarios as test files under `tests/` (or similar): set values, render templates, and compare output to expected YAML or snapshots. This is far faster and more deterministic than only testing in a live cluster, and it documents expected behavior for reviewers.

## Details

- **Workflow:** install the plugin (`helm plugin install https://github.com/helm-unittest/helm-unittest`); run `helm unittest` in the chart directory in CI.
- **Assertions:** document presence, equals, match regex, snapshot files, and suite-level setup/teardown for values files.
- **Fit:** essential when you ship [[Helm Chart]] artifacts to customers or run many value permutations (dev/stage/prod).
- **Limits:** tests template output, not cluster behavior—pair with integration tests for admission, CRDs, and hooks.
- **Note:** superseded the earlier `quintush/helm-unittest` fork; use the `helm-unittest` org repository.
