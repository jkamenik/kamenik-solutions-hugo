---
title: "cursor-agent"
date: 2026-05-17
lastmod: 2026-05-17
draft: false

keywords:
  - cursor-agent
  - Cursor CLI
  - Cursor Agent CLI

params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "New"
    subcategories:
      - ai-agent

aliases:
  - /radar/tools/cursor-agent
---

[cursor-agent](https://cursor.com/cli) is Cursor's terminal agent—TUI/CLI for running the same Cursor Agent in your shell, scripts, GitHub Actions, and headless automations, with frontier models and MCP. We **adopt** it under [[AI Agent]] as our default bounded coding agent alongside the [[Cursor]] editor: one vendor for interactive IDE work and terminal/CI agents, with skills and rules wired through `.cursor/` and this vault's research conventions (`agent: cursor-agent` in frontmatter).

## Blurb

> Ship code with agents. Right from your terminal.

## Summary

The `cursor-agent` binary (install via Cursor's install script) drives an agent loop in a repo: model selection (`/model`), shell mode, resume via `cursor-agent --resume <chatId>`, and `cursor-agent create-chat` / `ls` for session management. `CURSOR_AGENT=1` in the environment marks agent invocations for logging and gbrain session metadata.

Use for day-to-day coding in the terminal, headless pipelines, and GitHub Actions when you already use Cursor billing. It is a **repo-bounded** [[AI Agent]]—not an omnichannel personal bot ([[OpenClaw]], [[hermes-agent|Hermes]] are **hold**). Pair with [[Cursor]] under [[IDE]] when you want GUI + CLI in one stack.

Compare [[Claude Code]], [[Codex]], [[Gemini]], and [[OpenCode]] when a different vendor or open-source hub is required.

## Details

- **Install:** `curl https://cursor.com/install -fsS | bash` (see Cursor CLI docs for npm and platform packages).
- **Auth:** Cursor subscription / team plan; CLI shares model access with the Cursor product.
- **Models:** Composer, Claude, GPT, Gemini, Grok, and other frontier models exposed in the CLI picker.
- **Automation:** headless mode and GitHub Actions integrations for doc updates, reviews, and custom agents.
- **Skills:** `.cursor/skills/` and rules; cross-reference [[Agent Skills - Sources]] for portable SKILL.md repos.
- **Fit:** [[Tool]] / [[AI Agent]]—Cursor's agent runtime in the terminal ([[Cursor]] is the editor under [[IDE]]).
- **Contrast:** vendor-specific CLIs when not on Cursor; [[OpenCode]] for multi-provider open source.
