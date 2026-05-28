---
title: "Shell Operator"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - Shell Operator

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"

aliases:
  - /radar/tools/shell-operator
---

[Shell Operator](https://github.com/flant/shell-operator) is a **[[Kubernetes]]** operator framework that runs shell or bash hooks when cluster objects change. It watches CRDs or built-in resources and executes scripts you package in the image. We **assess** it for quick glue automation before committing to a full Go operator.

## Blurb

> Shell-operator is a tool for running event-driven scripts in a Kubernetes cluster.

## Summary

**When to use:** small integrations (notify, label, trigger jobs) where a compiled operator is overkill; teams comfortable maintaining hook scripts and images.

**When to skip:** complex reconciliation loops, admission webhooks, or production controllers that need strong typing and tests in Go.

**Ops note:** treat hook scripts like production code: pin images, limit RBAC, and log hook failures to **[[OpenTelemetry]]** or cluster logging.
