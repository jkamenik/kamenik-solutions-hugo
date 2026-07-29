---
title: Model Context Protocol
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- Model Context Protocol
- MCP
- Model Context Protocol (MCP)
params:
  aliases:
  - MCP
  - Model Context Protocol (MCP)
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - specification
    - ai-techniques
---

[Model Context Protocol](https://modelcontextprotocol.io/) (MCP) is an open standard that connects AI apps to tools, data sources, and workflows through clients and servers. We **adopt** it as the default tool-connectivity layer for coding agents in this estate.

## Blurb

> MCP (Model Context Protocol) is an open-source standard for connecting AI applications to external systems.

## Summary

**When to use:**

| Situation | Notes |
|-----------|--------|
| Shared tools across hosts | One server; many clients ([[Claude Code]], [[Cursor]], [[Codex]], [[Gemini]]) |
| Vault / local integrations | Obsidian, Reminders, Gmail, and similar via local stdio servers |
| Remote product APIs | Prefer a vendor-hosted server over a locally installed package |

**When to skip:**

- One-off scripts where a CLI or SDK call is enough
- Untrusted third-party servers without review (treat tool surface as code execution)
- Vendor-provided Node.js packages when a maintained hosted endpoint is practical
- Replacing portable behavior that belongs in [[Agent Skills Framework]] (`SKILL.md`)

**Trade-offs:** MCP standardizes *what tools an agent can call*. Skills standardize *how the agent reasons*. Prefer MCP for actions and data access; prefer skills for reusable procedures.

Locally installed MCP packages add a software supply-chain risk to every client machine. Prefer vendor-hosted endpoints when available. Pair local servers with dependency controls, least privilege, and [[Claw Patrol]] or equivalent safeguards.

**Contrast:** [[Agent Client Protocol]] is about treating an agent as a service. MCP is about plugging tools and context into an agent host.

## Details

### Shape

| Role | Responsibility |
|------|----------------|
| Host / client | Agent app that discovers tools, prompts, and resources |
| Server | Exposes tools, resources, and prompts over stdio or HTTP |
| Transport | Local stdio is common for desktop agents; remote HTTP/SSE for hosted servers |

### Estate Notes

- This vault declares MCP servers in `.mcp.json` (Obsidian vault access and related tooling).
- Coding agents in the garden ([[Claude Code]], [[cursor-agent]], [[Codex]], [[Gemini]]) all speak MCP for extensions.
- [[Agent Skills - Sources]] treats MCP servers as the complement to skills: tools vs reasoning.

### Security

- Every connected server expands the agent's blast radius (files, shell, cloud APIs).
- Vendor-distributed Node.js servers create a supply-chain path through package installation and transitive dependencies.
- Prefer vendor-hosted endpoints. Report locally packaged servers to vendors when a hosted service is practical.
- Prefer least privilege, allowlists, and human approval for destructive tools.
- See [[Claw Patrol]] when evaluating egress and protocol-aware interception for agent workloads.
