---
title: Agent Control
date: '2026-08-11'
lastmod: '2026-08-14'
draft: false
keywords:
- Agent Control
params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: New
---

[Agent Control](https://agentcontrol.dev) is an open-source control plane for AI agents. It enforces centralized policies at runtime, block, deny, steer, warn on each LLM output and tool call. We **assess** it for governance and guardrails across OpenAI, Move, Bedrock, and a growing set of agent frameworks.

## Blurb

> Control all AI agent behaviors at runtime with centralized policies. Write once and deploy everywhere.

## Summary

**What it is:** A policy-driven step-level guardrail server for agent fleets. A `@control` decorator wraps LLM calls and tool execution, checking outputs against policies cached on the agent client, then responding with allow, deny, steer, or warn.

**When to use:** You need runtime governance, safety, and compliance across many agents. You want "write once, deploy everywhere" policy enforcement without redeploying agents.

**When to skip:** Single-agent apps with simple guardrails, where hard-coded checks suffice. You already run a gateway-side governance product that meets step-level needs.

**Key features:** Centralized Policy Enforcement, Control Store (mix guardrails from AWS Bedrock, Cisco AI Defense, NeMo, Galileo Luna), Audit Logs, Live policy updates without downtime, agent framework integrations (LangChain/LangGraph, Strands, Google ADK, OpenAI Agents SDK, AutoGen, CrewAI). Apache 2.0 licensed.

## Details

**Maintained by:** Galileo (currently Galileo Technologies).

**Guardrail ecosystem:** Amazon Bedrock Guardrails, NVIDIA NeMo Guardrails, Galileo Luna-2, Azure AI Content Safety, Cisco AI Defense.

**Docs:** [https://docs.agentcontrol.dev](https://docs.agentcontrol.dev)

**Source:** [https://github.com/agentcontrol/agent-control](https://github.com/agentcontrol/agent-control)
