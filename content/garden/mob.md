---
title: Mob
date: '2024-10-01'
lastmod: '2026-07-28'
draft: false
keywords:
- Mob
- mob.sh
- Mob CLI
params:
  aliases:
  - mob.sh
  - Mob CLI
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[Mob](https://mob.sh/) is a command-line tool that coordinates **[[Git]]** handovers for remote mob programming. We **assess** it for distributed teams that rotate the active driver and need clean, repeatable handoffs.

## Blurb

> Tool for smooth git handover.

## Summary

**When to use:** A remote mob rotates drivers through Git rather than shared-screen control. Mob automates temporary WIP branches, commits, pushes, pulls, timers, and the final squash back to the working branch.

**When to skip:** The team is co-located, uses live collaborative editing, or rarely rotates drivers. Plain Git commands are enough when handoffs are infrequent and everyone understands the branch protocol.

**Trade-offs:** It standardizes handoffs and keeps WIP commits off the main branch. It also adds a team-specific CLI and remote-branch convention that every participant must learn.

## Details

| Topic | Notes |
|-------|--------|
| **Workflow** | `mob start`, edit, `mob next`, then `mob done` to return work to the base branch |
| **Coordination** | Temporary remote WIP branches, optional shared timer and goal room |
| **Implementation** | MIT-licensed Go CLI with macOS, Linux, and Windows releases |
| **Status** | Actively maintained; version 5.4.2 released in January 2026 |

**References**

- [Mob website](https://mob.sh/)
- [Remote mob programming guide](https://www.remotemobprogramming.org/)
- [remotemobprogramming/mob on GitHub](https://github.com/remotemobprogramming/mob)
