---
title: 'Container Structure Test'
date: 2023-03-03
lastmod: 2023-12-17

# Keywords help in classifying content
keywords:
  - Container Structure Test
  - containers
  - testing

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: adopt

    # tools, techniques, platforms, languages & frameworks
    quadrant: languages

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

[Container Structure Test](https://github.com/GoogleContainerTools/container-structure-test) provides a powerful framework to validate the structure of a container image. These tests can be used to check the output of commands in an image, as well as verify metadata and contents of the filesystem.

If you are building {{% wl "containerization" "containers" %}} then this is a critical tool.

<!--more-->

Tests are defined in a YAML file and then run via

```bash
container-structure-test test --image <image> --config <testfile>
```

There are three types of tests that can be performed:

1. Command Tests - Execute a command and check its output
2. File existence tests - Check a file is or is not present
3. File content tests - Check a file has or does not have certain content
4. Metadata test - Check that the metadata of the container is correct
