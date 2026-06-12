---
title: "Gemini"
date: 2026-05-17
lastmod: 2026-06-12
draft: false

keywords:
  - Gemini
  - Gemini CLI
  - Google Gemini CLI

params:
  aliases:
    - Gemini CLI
    - Google Gemini CLI
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
    subcategories:
      - ai-agent
---

[Gemini CLI](https://developers.google.com/gemini-code-assist/docs/gemini-cli) is Google's open-source agentic coding agent for the terminal, ReAct loop, built-in tools (files, shell, search), MCP servers, and large-context Gemini models. We rate it **trial** under [[AI Agent]]: a solid choice on Google accounts or Gemini API when you want Google's stack and [[Agent Skills Framework]] portability; we usually default to [[Cursor]] + [[cursor-agent]] for daily editor work and [[Claude Code]] / [[Codex]] for other vendor stacks.

## Blurb

> Gemini CLI is an open-source AI agent that brings Gemini directly into your terminal. It helps you build, debug, and automate development workflows with built-in tools and MCP support.

## Summary

Gemini CLI (`google-gemini/gemini-cli`) runs an agent loop in your repo: reason, call tools, checkpoint conversations, and load project context via `GEMINI.md`. It shares quota with Gemini Code Assist agent mode on free and paid Google tiers.

Use for interactive coding, refactors, and skill-driven workflows when Gemini models or Google Cloud billing are the constraint. It is a **repo-bounded** [[AI Agent]]; not an omnichannel personal bot ([[OpenClaw]], [[hermes-agent|Hermes]] are **hold**). For scheduled automation, prefer deterministic scripts and [[Dagu]] with LLM steps only where reasoning is required.

Compare [[Claude Code]] (Anthropic) and [[Codex]] (OpenAI) for the same agent-loop-in-repo pattern.

## Details

- **Install:** `npm install -g @google/gemini-cli`, Homebrew (`brew install gemini-cli`), or `npx` from GitHub; Node.js 20+.
- **Auth:** Google account (free tier quotas) or Gemini API key for pay-as-you-go.
- **Models:** Gemini 2.5 Pro and successors; very large context windows per Google docs.
- **Skills:** SKILL.md / [[Agent Skills Framework]] ecosystem, see [[Agent Skills - Sources]] for cross-agent collections.
- **Fit:** [[Tool]] / [[AI Agent]], agent-loop coding tool (also branded Gemini Code Assist in IDE surfaces).
- **Contrast:** [[Cursor]] + [[cursor-agent]] for default IDE workflow; [[Claude Code]] / [[Codex]] on other vendors.
