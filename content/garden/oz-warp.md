---
title: Oz
date: '2026-06-30'
lastmod: '2026-06-30'
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
    movement: New
---

[Oz](https://www.warp.dev/oz) is Warp's cloud agent orchestration platform. It runs, governs, and scales coding agents across models and harnesses with triggers, schedules, parallelism, and audit trails. We **assess** it as enterprise agent infrastructure. Our default bounded agents remain [[cursor-agent]] and [[Cursor]] unless a team needs multi-harness fleet orchestration.

## Blurb

> The most flexible way to manage cloud agents at scale.

## Summary

Oz is the control plane behind Warp's local and cloud agents. You can launch [[Warp Agent]], [[Claude Code]], or [[Codex]] in Docker or Kubernetes sandboxes, self-hosted or Warp-managed. Features include Slack, Linear, and GitHub triggers; recurring schedules; parallel agent fleets; and shared Warp Drive context across surfaces.

Evaluate Oz when engineering leaders want harness choice without betting on one vendor CLI. Agent Memory (research preview) adds cross-harness persistent memory. Oz is proprietary even though [[Warp Terminal]]'s desktop client is open source.

## Details

- **Deployment:** Warp-managed cloud or self-hosted Oz on your infrastructure.
- **Harnesses:** Warp Agent, Claude Code, Codex (multi-harness beta); model routing per task.
- **Orchestration:** subagent parallelism, long-running migrations, PR workflows, webhook and cron triggers.
- **Governance:** centralized permissions, usage reporting, credit caps, SOC 2 posture per Warp enterprise docs.
- **Integration:** SDK/CLI launch, native handoff from [[Warp Terminal]], shared MCP and Warp Drive with local agents.
- **Fit:** [[Platform]] for cloud coding-agent orchestration (not a repo-bounded CLI itself).
- **Contrast:** running agents only via [[cursor-agent]] or [[Claude Code]] without a fleet control plane.
