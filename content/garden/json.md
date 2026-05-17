---
title: "JSON"
date: 2025-04-24
lastmod: 2026-05-17
draft: false

keywords:
  - JSON

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

[JSON](https://www.json.org/)

JSON is the de facto standard for data interchange on the web and in configuration files. If you are building an API, serialising config, or passing structured data between services, JSON is the default choice unless you have a specific reason to use something else (e.g. [[Protobuf]] for high-throughput binary payloads, [[YAML]] for human-authored config).

## Blurb

> JSON (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate. It is based on a subset of the JavaScript Programming Language Standard ECMA-262 3rd Edition.

## Summary

JSON is universally supported — every language has a parser, every HTTP client speaks it, and every developer knows it. The only reasons to consider alternatives are size/performance ([[Protobuf]], [[MessagePack]]) or richer type systems ([[JSON Schema]] for validation). Adopt without hesitation for any API or config surface.
