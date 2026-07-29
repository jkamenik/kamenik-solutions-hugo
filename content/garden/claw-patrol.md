---
title: Claw Patrol
date: '2026-07-09'
lastmod: '2026-07-09'
draft: false
keywords:
- Claw Patrol
- ClawPatrol
params:
  aliases:
  - ClawPatrol
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: New
    subcategories:
    - ai-agent
---

[Claw Patrol](https://clawpatrol.dev/) is an open-source agent proxy from Deno. It holds credentials, inspects wire traffic, and enforces [[HCL]] rules before outbound calls complete. We **assess** it for self-hosted agent workloads that need audit logs and human or LLM approval gates.

## Blurb

> The security firewall for any agent

## Summary

**What it is:** Self-hosted gateway (single Go binary) plus enrolled devices on WireGuard or Tailscale. Agents run under `clawpatrol run`; the gateway injects credentials, evaluates protocol-aware rules, and logs every request.

**When to use:** You run coding or ops agents with broad API, database, or k8s access. You want secrets off the agent, per-request policy, a dashboard audit trail, and optional human or LLM judge for risky actions.

**When to skip:** Perimeter controls already cover the same blast radius. You cannot operate a gateway host and HCL policy lifecycle. The project is early (v0.2.x) and may not meet a production bar yet.

| Topic       | Notes                                                                         |
| ----------- | ----------------------------------------------------------------------------- |
| **Gateway** | Self-hosted SQLite state; no cloud required                                   |
| **Rules**   | [[HCL]] config; match HTTP, SQL, k8s verbs, not just URLs                     |
| **Testing** | `clawpatrol test` with recorded fixtures in CI                                |
| **License** | MIT; [github.com/denoland/clawpatrol](https://github.com/denoland/clawpatrol) |

**Related garden notes:** [[Open Policy Agent]] and [[Policy as Code]] for policy-as-code patterns; [[Tailscale]] for device join; [[AI Agent]] for the workloads this gates.

## Details

**Install**

```bash
curl -fsSL https://clawpatrol.dev/install.sh | sh
```

**Workflow**

1. Run a gateway on a host you control with an HCL policy file.
2. Join agent machines with `clawpatrol join`.
3. Prefix agent commands with `clawpatrol run` (or route the whole machine with `--whole-machine`).

**Protocol-aware gating:** Rules can match HTTP methods and headers, SQL verbs and statements, Kubernetes resource actions, and more. Credentials stay on the gateway; the agent never sees raw secrets.

**Approval flows:** Risky actions can require a human or an LLM judge before the gateway stamps credentials onto the wire.

**Regression tests:** Record real actions from the dashboard, store JSON fixtures, and run `clawpatrol test` in CI. Policy changes that flip a verdict fail the build with a diff.

**References**

- [Claw Patrol docs](https://clawpatrol.dev/docs/introduction/)
- [Getting started](https://clawpatrol.dev/docs/getting-started/)
- [GitHub repository](https://github.com/denoland/clawpatrol)
