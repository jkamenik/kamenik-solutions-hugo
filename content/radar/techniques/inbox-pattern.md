---
title: 'Inbox Pattern'
date: 2025-05-19
lastmod: 2025-05-19
draft: true

# Keywords help in classifying content
keywords:
  - Inbox Pattern
  - Outbox Pattern
  - Pattern

params:
  # Alternative titles that can be used in the wl shortcode
  aka:
    - Outbox Pattern

  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: adopt

    # tools, techniques, platforms, languages & frameworks
    quadrant: techniques

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

The [inbox pattern](https://en.wikipedia.org/wiki/Inbox_and_outbox_pattern) is an effective means to guarantee delivery of a work item.  You might be familar with it from email.  It is a highly effective way to make sure that work is complete, or retried until it completes.  It is light weight and can be used effectively in much more complex systems like {{% wl "work queue" "work queues" %}}, or {{% wl "workflow" %}}.  It should be adopted before more complex designs.

<!--more-->

```mermaid
sequenceDiagram
  actor User

  box Service
    participant API
    participant TaskExecutor
  end

  participant DB as Database

  User ->> API: request
  API ->> DB: insert job
  API ->> User: accepted

  loop
    DB -->> TaskExecutor: get job
    TaskExecutor ->> TaskExecutor: do work
    TaskExecutor ->> DB: record results
  end
```

> [!NOTE] AKA Outbox Pattern
> The outbox pattern is basically the inbox pattern in reverse.
