---
title: "Hermes"
date: 2026-04-20
lastmod: 2026-06-12
draft: false

keywords:
  - Hermes
  - hermes-agent

params:
  aliases:
    - hermes-agent
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: "Moved Out"
    subcategories:
      - ai-agent
---

[Hermes](https://github.com/NousResearch/hermes-agent) is a self-improving [[AI Agent]] platform from Nous Research. It targets personal-assistant use with learning loops, messaging integrations, and [[Agent Skills Framework]] support. We rate it **hold** with **Moved Out**. Always-on agents that message external systems are hard to secure. The hardening effort often negates the convenience versus a bounded agent in an [[IDE]] or scheduled automation you control.

## Blurb

> The self-improving AI agent built by [Nous Research](https://nousresearch.com/). The only agent with a built-in learning loop , it creates skills from experience, improves them during use, nudges itself to persist knowledge, and builds a deepening model of who you are across sessions.

## Summary

Hermes targets the same problem space as [[OpenClaw]]: an always-available assistant across chat surfaces (Telegram, Slack, CLI, etc.) with memory, cron-style scheduling, and skill extensibility. It integrates [[Agent Client Protocol]] so editors like Obsidian can use the agent via plugins (e.g. [obsidian-agent-client](https://github.com/RAIT-09/obsidian-agent-client)). On Apple Silicon, local runs via [[Ollama]] with models such as `deepseek` and `qwen` are practical.

Originally a credible competitor in the personal-agent wave; our position is that broad tool-and-shell access without tight policy boundaries is unsafe for most setups. Prefer IDE-bound agents ([[Claude Code]], Cursor-class tools) or pipelines that emit reviewable scripts on a schedule.

## Details

- **Strengths:** skill learning loop, multi-channel gateway, [[Agent Skills Framework]] portability, ACP for [[IDE]] clients, flexible model routing (cloud or [[Ollama]]).
- **Risks:** persistent credentials, messaging exfiltration, autonomous cron/subagent actions, treat as high-trust workload only with explicit sandboxing.
- **When hold is OK:** isolated experimentation, local-only models, single-user machine with clear data boundaries.
- **When to avoid:** production secrets on the same host, multi-tenant boxes, or "set and forget" automation without human review.
- **Install:** upstream documents quick install via `install.sh` on macOS/Linux; verify signing and update channel before production use.
