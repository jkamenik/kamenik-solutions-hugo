---
title: "System Initiative"
date: 2025-04-23
lastmod: 2026-05-17
draft: false

keywords:
  - System Initiative

params:
  garden:
    kind: item
    usefulness: hold
    category: platform
    movement: "Moved Out"

aliases:
  - /radar/platforms/system-initiative
---

[System Initiative](https://www.systeminit.com/) is a visual DevOps tool. Think wysiwyg [[terraform]].

When it started in 2019, we were optimistic about its novel approach of using a hypergraph to perform all the work on a digital twin before applying it to the underlying infrastructure. We appreciate that it is an open source project, but the source reveals that the hypergraph is essentially JSON objects, and the digital twin is just JSON transformers that are applied to the in-memory version of that objects.

We are 5 years on, and novelty of that approach has waned as it struggles to implement useful features like support for anything but AWS, templates of reusable code, basic linting, or 3rd party integrations. Unless you are already invested in this solution we recommend avoiding this platform.
