---
title: OpenClaw
date: '2026-05-17'
lastmod: '2026-07-02'
draft: false
keywords:
- OpenClaw
params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: No Change
    subcategories:
    - ai-agent
---

[OpenClaw](https://openclaw.ai/). Is an open-source, self-hosted personal [[AI Agent]] that runs continuously on your hardware and connects to messaging apps (WhatsApp, Telegram, Slack, Discord, and others) with skills, shell access, and persistent memory.

## Blurb

> OpenClaw - The AI that actually does things. Your personal assistant on any platform.

## Summary

OpenClaw targets always-on assistance: ingest messages from chat surfaces, call cloud or local models ([[Ollama]] via OpenRouter-style routing), execute skills/plugins, and remember context in local files. The GitHub project (`openclaw/openclaw`) gained massive attention for automating real workflows; not just chat.

## Details

- **Strengths:** broad channel support, skill ecosystem, self-hosted narrative, multi-model flexibility.
- **Risks:** broad system/shell access, credential sprawl across chat networks, hard to secure; operational burden rivals the task.
- **vs [[hermes-agent|Hermes]]:** same product category; Hermes adds learning loops and ACP; both are **hold** for greenfield personal automation here.
- **Preferred pattern:** deterministic scripts + [[Dagu]] (or cron) on each machine; LLM only where reasoning is required; agents inside [[IDE]] when interactive help is needed.
