---
title: YAML
date: '2025-04-09'
lastmod: '2026-07-02'
draft: false
keywords:
- YAML
params:
  garden:
    kind: item
    usefulness: adopt
    category: code
    movement: No Change
    subcategories:
    - language
---

[YAML](https://yaml.org/). Is a more human readable format which is fully API compatible with [[JSON]].

## Summary

**Garden stance:** We **adopt** YAML for our estate.

**Overview:** There are some syntactic sugar like anchors and aliases and deep merging of maps which makes it easier to for humans to read. Additionally, many systems (like [[Helm]]) add a templating language on-top to make generating large amounts of YAML easier. And since Yaml is a subset of [[JSON]], [[JSON Schema]] that can be used to validate complex YAML. Because of this ubiquity you should adopt it.

**Detail 1:** The creators of YAML also created [[YAMLScript]] as a templating language, but it is not wide spread yet.
