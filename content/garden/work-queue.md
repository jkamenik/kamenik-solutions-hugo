---
title: "Work Queues"
date: 2025-05-20
lastmod: 2026-05-18
draft: false

keywords:
  - Work Queues

params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: "No Change"
aliases:
  - /radar/techniques/work-queue
---

[Work queues](https://en.wikipedia.org/wiki/Message_queue) decouple producers and consumers so tasks can be processed asynchronously, retried, and scaled independently. They pair well with the [[Inbox Pattern]] when you need at-least-once delivery without building a full workflow engine. Adopt a mature broker (or managed queue) before inventing your own persistence layer.
