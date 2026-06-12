---
title: "GoCD"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - GoCD

params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: "New"
    subcategories:
      - ci-cd-tools
aliases:
  - /radar/platforms/gocd
---

[GoCD](https://www.gocd.org/) is an open source continuous delivery server from ThoughtWorks. It models pipelines, stages, and artifacts with explicit promotion between environments. We **assess** it alongside **[[Jenkins]]** for legacy CD installs; new pipelines should not start here unless migration cost dominates.

## Blurb

> GoCD is an open-source tool which is used in software development to help teams and organizations automate the continuous delivery of software.

## Summary

**When to use:** maintaining an existing GoCD server; need visual pipeline DAG and artifact promotion semantics teams already understand.

**When to skip:** greenfield repos; preference for pipeline-as-code in git without a central CD server; **[[GitOps]]** models where cluster state is the source of truth.

**Note:** operational burden similar to other pet CD servers; treat the server as infrastructure with backups and upgrades planned.
