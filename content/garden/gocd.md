---
title: GoCD
date: '2026-05-27'
lastmod: '2026-07-02'
draft: false
keywords:
- GoCD
params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: No Change
    subcategories:
    - ci-cd-tools
aliases:
- /radar/platforms/gocd
---

[GoCD](https://www.gocd.org/). Is an open source continuous delivery server from ThoughtWorks.

## Blurb

> GoCD is an open source build and release tool originally conceived and built by Thoughtworks. GoCD supports modern infrastructure and helps enterprise businesses get software delivered faster, safer, and more reliably.

## Summary

**When to use:** maintaining an existing GoCD server; need visual pipeline DAG and artifact promotion semantics teams already understand.

**When to skip:** greenfield repos; preference for pipeline-as-code in git without a central CD server; **[[GitOps]]** models where cluster state is the source of truth.

**Note:** operational burden similar to other pet CD servers; treat the server as infrastructure with backups and upgrades planned.
