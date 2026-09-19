---
title: nono.sh
date: '2026-08-14'
lastmod: '2026-08-14'
draft: false
keywords:
- nono.sh
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: New
    subcategories:
    - ai-agent
---

[nono.sh](https://nono.sh) is a platform for ephemeral micro sandboxes for AI agents with kernel-level isolation. We **assess** it for secure tool execution in our agent workflows.

## Blurb

> Ephemeral micro sandboxes for AI agents, with zero setup and zero latency. Kernel isolation for Linux, macOS & Windows with per-tool sandboxing, credential protection, and fully auditable execution.

## Summary

**What it is:** A sandbox platform that provides isolated, scoped execution environments for AI agent tool calls. Each tool invocation runs inside a micro sandbox with only the selected capabilities: read-only workspace, bounded I/O, and proxy-only network access.

**When to use:** You need secure tool execution with credential protection and audit trails for AI agents in production or sensitive environments.

**When to skip:** Single-agent development workflows where direct tool execution without sandboxing suffices. You already have a gateway governance product that meets step-level needs (like [[Agent Control]]).

**Key features:** Kernel-level isolation, per-tool sandboxing with least-privilege capabilities, credential injection at the boundary, cryptographic audit trail (SHA-256 Merkle root), composable JSON profiles, integration with Claude Code, OpenCode, Codex, and other registry agents. MIT licensed.

## Details

**Package:** `nono` CLI  
**Source:** https://nono.sh  
**Registry:** https://registry.nono.sh  

**Sandbox providers:** OS Sandbox (kernel isolation), Python, Node.js, Go sandboxes  
**Integrations:** Claude Code, OpenCode, Codex, Antigravity, GitHub Copilot, and registry agents  

**Architecture:** Supervisor → Resolve → Authorize → Spawn → Execute → Audit → Destroy. Every tool call crosses the supervisor boundary with policy-enforced capabilities.
