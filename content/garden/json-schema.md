---
title: "JSON Schema"
date: 2025-04-24
lastmod: 2026-05-17
draft: false

keywords:
  - JSON Schema

params:
  garden:
    kind: item
    usefulness: adopt
    category: code
    movement: "No Change"
    subcategories:
      - language

aliases:
---

[JSON Schema](https://json-schema.org/)

JSON Schema is the standard vocabulary for describing and validating the structure of [[JSON]] documents. It is embedded in [[OpenAPI]] specs, Kubernetes CRDs, IDE autocompletion, and nearly every modern config validation pipeline. If you are exposing or consuming structured JSON at a system boundary, JSON Schema is the correct tool for documenting and enforcing that contract.

## Blurb

> JSON Schema is the vocabulary that enables JSON data consistency, validity, and interoperability at scale.

## Summary

JSON Schema is effectively required knowledge in any DevSecOps or API-first context — [[OpenAPI]] 3.x uses it natively, Kubernetes uses it for CRD validation, and most linting/validation tools in the CI pipeline speak it. The spec is stable (Draft 2020-12) and tooling support is broad across all major languages. Adopt without reservation anywhere you need to validate or document a JSON structure.
