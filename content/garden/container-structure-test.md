---
title: "Container Structure Test"
date: 2023-03-03
lastmod: 2026-05-17
draft: false

keywords:
  - Container Structure Test

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

[Container Structure Test](https://github.com/GoogleContainerTools/container-structure-test) provides a powerful framework to validate the structure of a container image. These tests can be used to check the output of commands in an image, as well as verify metadata and contents of the filesystem.

If you are building [[containerization|containers]] then this is a critical tool.

Tests are defined in a YAML file and then run via

```bash
container-structure-test test --image <image> --config <testfile>
```

There are three types of tests that can be performed:

1. Command Tests - Execute a command and check its output
2. File existence tests - Check a file is or is not present
3. File content tests - Check a file has or does not have certain content
4. Metadata test - Check that the metadata of the container is correct
