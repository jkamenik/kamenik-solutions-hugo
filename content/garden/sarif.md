---
title: "SARIF"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - SARIF

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "New"
    subcategories:
      - specification

aliases:
  - /radar/techniques/sarif
---

[SARIF](https://sarifweb.azurewebsites.net/) (Static Analysis Results Interchange Format) is an OASIS JSON schema for exchanging output from **[[Code Scanner]]** tools in CI and IDEs. We **adopt** it as the default interchange format when wiring SAST, IaC scanners, and **[[GitHub Actions]]** annotations on [[Pull Request]]s.

## Blurb

> SARIF defines a JSON-based format for the output of static analysis tools.

## Summary

**Why it matters:** one schema lets CodeQL, Semgrep, **[[Conftest]]**, and vendor scanners feed the same PR comment bots, dashboards, and policy gates.

**When to use:** any pipeline that aggregates multiple scanners; GitHub Advanced Security code scanning; internal security portals that ingest findings.

**When to skip:** a single proprietary scanner with no export and no plan to unify findings (still prefer SARIF export if available).

**Pairs with:** `sarif` artifacts uploaded as workflow artifacts; GitHub `upload-sarif` action; **[[Policy as Code]]** rules that count severities per run.
