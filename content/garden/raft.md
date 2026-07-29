---
title: Raft
date: '2026-07-29'
lastmod: '2026-07-29'
draft: false
keywords:
- Raft
- Raft Consensus
- Raft Consensus Algorithm
params:
  aliases:
  - Raft Consensus
  - Raft Consensus Algorithm
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: New
    subcategories:
    - software-architecture
---

[Raft](https://raft.github.io/) is a leader-based consensus algorithm for replicated state machines. We **adopt** it as the default mental model for quorum logs, leader election, and CP control planes.
