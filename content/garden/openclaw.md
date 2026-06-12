---
title: "OpenClaw"
date: 2026-05-17
lastmod: 2026-06-05
draft: false

keywords:
  - OpenClaw

params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: "New"
    subcategories:
      - ai-agent
---

[OpenClaw](https://openclaw.ai/) is an open-source, self-hosted personal [[AI Agent]] that runs continuously on your hardware and connects to messaging apps (WhatsApp, Telegram, Slack, Discord, and others) with skills, shell access, and persistent memory. We rate it **hold**: powerful on paper, but our experience matches [[hermes-agent|Hermes]], too complex and fragile for multi-machine, sandboxed setups; prefer bounded [[IDE]] agents or per-machine scheduled pipelines.

## Blurb

> OpenClaw is your personal AI assistant that runs on your own hardware.

## Summary

OpenClaw targets always-on assistance: ingest messages from chat surfaces, call cloud or local models ([[Ollama]] via OpenRouter-style routing), execute skills/plugins, and remember context in local files. The GitHub project (`openclaw/openclaw`) gained massive attention for automating real workflows; not just chat.

## Details

- **Strengths:** broad channel support, skill ecosystem, self-hosted narrative, multi-model flexibility.
- **Risks:** broad system/shell access, credential sprawl across chat networks, hard to secure; operational burden rivals the task.
- **vs [[hermes-agent|Hermes]]:** same product category; Hermes adds learning loops and ACP; both are **hold** for greenfield personal automation here.
- **Preferred pattern:** deterministic scripts + [[Dagu]] (or cron) on each machine; LLM only where reasoning is required; agents inside [[IDE]] when interactive help is needed.
