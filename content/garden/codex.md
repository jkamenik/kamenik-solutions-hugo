---
title: "Codex"
date: 2026-05-17
lastmod: 2026-05-18
draft: false

keywords:
  - Codex
  - OpenAI Codex
  - Codex CLI

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
    subcategories:
      - ai-agent

aliases:
  - /radar/tools/codex
---

[Codex](https://developers.openai.com/codex/cli) is OpenAI's agentic coding agent (terminal CLI (Rust), IDE integrations, and cloud tasks) built to read repos, edit files, run commands, and use MCP tools under approval policies. We rate it **trial**: credible alternative to [[Claude Code]] when you are on ChatGPT Plus/Pro/Business plans and want OpenAI models; [[Claude Code]] is also **trial** here (we usually default to [[Cursor]] + [[cursor-agent]] for daily IDE work).

## Blurb

> Codex is OpenAI's coding agent. It helps you build, debug, and ship faster across terminals, IDEs, web, and mobile.

## Summary

Codex runs an agent loop scoped to your codebase: sandboxed execution, configurable approval modes, subagents for parallel work, and support for the [[Agent Skills]] `SKILL.md` format (skills from [[Agent Skills - Sources]] often port with minimal changes). It is **not** the legacy GPT-3 "Codex" completion API, that model family is historical; this note is the 2025+ **product** (`openai/codex` on GitHub).

Use for interactive coding, reviews, and refactors inside a repo. Like [[Claude Code]], it is a bounded [[AI Agent]] workspace tool; not an always-on messaging bot ([[OpenClaw]], [[hermes-agent|Hermes]] are **hold** for that pattern).

## Details

- **Install:** `npm i -g @openai/codex`, Homebrew cask, or GitHub release binaries; requires a paid ChatGPT plan or API access per OpenAI docs.
- **Models:** GPT-5.x / Codex-tuned models with adjustable reasoning; cloud and local terminal modes per release notes.
- **Safety:** sandboxing, network policies, and human-in-the-loop approvals, see OpenAI's "running Codex safely" guidance for enterprise patterns.
- **Fit:** [[Tool]] / [[AI Agent]], agent-loop coding tool; compare [[Claude Code]] on Anthropic plans.
- **Skills:** cross-compatible SKILL.md ecosystem noted in [[Agent Skills - Sources]].
