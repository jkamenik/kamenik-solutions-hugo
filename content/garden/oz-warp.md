---
title: Oz
date: '2026-06-30'
lastmod: '2026-07-02'
draft: false
keywords:
- Oz
- Warp Oz
- Oz Agent Platform
params:
  aliases:
  - Warp Oz
  - Oz Agent Platform
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: No Change
---

[Oz](https://www.warp.dev/oz). Is Warp's cloud agent orchestration platform.

## Summary

**Garden stance:** We **assess** Oz for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

- **Deployment:** Warp-managed cloud or self-hosted Oz on your infrastructure.
- **Harnesses:** Warp Agent, Claude Code, Codex (multi-harness beta); model routing per task.
- **Orchestration:** subagent parallelism, long-running migrations, PR workflows, webhook and cron triggers.
- **Governance:** centralized permissions, usage reporting, credit caps, SOC 2 posture per Warp enterprise docs.
- **Integration:** SDK/CLI launch, native handoff from [[Warp Terminal]], shared MCP and Warp Drive with local agents.
- **Fit:** [[Platform]] for cloud coding-agent orchestration (not a repo-bounded CLI itself).
- **Contrast:** running agents only via [[cursor-agent]] or [[Claude Code]] without a fleet control plane.
