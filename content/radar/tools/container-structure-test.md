---
title: 'Container Structure Test'
date: 2024-04-25
lastmod: 2025-01-05

# Keywords help in classifying content
keywords:
  - Container Structure Test
  - testing

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: adopt

    # tools, techniques, platforms, languages & frameworks
    quadrant: tools

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

[Container Structure Test](https://github.com/GoogleContainerTools/container-structure-test) provides a powerful framework to validate the structure of a container image. These tests can be used to check the output of commands in an image, as well as verify metadata and contents of the filesystem.

Your code has unit tests, right?  So should your container.  At a minimum you should have existence tests for the important files, like libraries that are needed, and even the main binary itself.  You should have tests that important labels like the commit hash are there, any ports that opened by default and default ENVs exist.

You can even do things like run your binary to make sure it produces expected behaviors.  Since in this day and age Containers are a must, so too is this tool.

<!--more-->

> [!WARNING] Smoke Tests
> The goal with this tool is the basic smoke test and some very light usability testing.  This is not an integration test suite.  You really are just trying to make sure the container will at least run.
