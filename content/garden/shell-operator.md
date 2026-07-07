---
title: Shell Operator
date: '2026-05-27'
lastmod: '2026-07-02'
draft: false
keywords:
- Shell Operator
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
aliases:
- /radar/tools/shell-operator
---

[Shell Operator](https://github.com/flant/shell-operator) is a tool we **assess** in the garden.

## Blurb

> Shell-operator is a tool for running event-driven scripts in a Kubernetes cluster - flant/shell-operator

## Summary

**When to use:** small integrations (notify, label, trigger jobs) where a compiled operator is overkill; teams comfortable maintaining hook scripts and images.

**When to skip:** complex reconciliation loops, admission webhooks, or production controllers that need strong typing and tests in Go.

**Ops note:** treat hook scripts like production code: pin images, limit RBAC, and log hook failures to **[[OpenTelemetry]]** or cluster logging.
