---
title: "OpenCode"
date: 2026-05-17
lastmod: 2026-06-12
draft: false

keywords:
  - OpenCode
  - opencode-ai

params:
  aliases:
    - opencode-ai
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
    subcategories:
      - ai-agent
---

[OpenCode](https://opencode.ai) is an open-source AI coding agent (terminal TUI, desktop app, and IDE extension) that connects to 75+ LLM providers (Claude, GPT, Gemini, local models, GitHub Copilot, ChatGPT accounts) with LSP-aware context and multi-session parallelism. We rate it **trial** under [[AI Agent]]: strong when you want vendor-neutral agents and privacy-sensitive workflows; we usually default to [[Cursor]] + [[cursor-agent]] for daily editor work and vendor-specific CLIs ([[Claude Code]], [[Codex]], [[Gemini]]) when billing is already tied to one stack.

## Blurb

> The open source AI coding agent. Free models included or connect any model from any provider, including Claude, GPT, Gemini and more.

## Summary

OpenCode (`anomalyco/opencode`) runs a plan/build agent loop in your repo: `/init` generates `AGENTS.md`, sessions support share links and undo/redo, and MCP extends tool use. OpenCode Zen offers curated models benchmarked for coding agents. The project does not store your code or context on OpenCode servers, suited to privacy-sensitive environments per their docs.

Use for interactive coding when model choice and open-source auditability matter more than a single-vendor CLI. It is a **repo-bounded** [[AI Agent]]; not an omnichannel personal bot ([[OpenClaw]], [[hermes-agent|Hermes]] are **hold**). For scheduled automation, prefer deterministic scripts and [[Dagu]] (which can invoke `opencode` as a harness) with LLM steps only where reasoning is required.

Compare [[Claude Code]], [[Codex]], and [[Gemini]] for single-vendor agent loops; OpenCode is the multi-provider hub.

## Details

- **Install:** `curl -fsSL https://opencode.ai/install | bash`, `npm install -g opencode-ai`, Homebrew (`anomalyco/tap/opencode`), Docker image `ghcr.io/anomalyco/opencode`.
- **Auth:** Provider API keys via `/connect`, OpenCode Zen billing, or reuse ChatGPT Plus / GitHub Copilot logins where supported.
- **Models:** Any provider in the Models.dev directory; Zen subset for validated coding-agent performance.
- **Surfaces:** terminal (primary), desktop beta (macOS/Windows/Linux), IDE extension.
- **Fit:** [[Tool]] / [[AI Agent]], open, multi-model coding agent.
- **Contrast:** [[Cursor]] + [[cursor-agent]] for default IDE workflow; vendor CLIs when you stay in one ecosystem.
