---
title: "gog"
date: 2026-05-26
lastmod: 2026-06-12
draft: false

keywords:
  - gog

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - ai-agent
---

[gog](https://gogcli.sh/) is a single-binary CLI for Google Workspace (Gmail, Calendar, Drive, Docs, Sheets, Slides, Contacts, Tasks, Chat, and Workspace Admin). It exposes stable `--json` and `--plain` output for scripts and agents, with human progress on stderr. We rate it **assess** under **[[Tool]]** and **[[AI Agent]]**: strong fit for terminal and agent workflows (safety profiles, command allow/deny lists), but OAuth setup and Workspace org policy still gate multi-account use (see [[gmail-access|Gmail Access]] research).

## Blurb

> Google Workspace in your terminal.

## Summary

`gog` covers Gmail search/read, calendar events, Drive tree and inventory audits, Docs/Sheets/Slides edits, Contacts, Tasks, and Admin SDK operations from one config. Multi-account OAuth, service accounts, and domain-wide delegation are supported. Agent-oriented features include runtime `--enable-commands` / `--disable-commands`, `--gmail-no-send`, and baked safety-profile binaries that cannot be reconfigured at runtime.

Worth evaluating when you want scriptable Google Workspace access without an MCP intermediary, or when pairing a locked-down binary with an [[AI Agent]]. Compare Google's official Gmail MCP (read-focused, hosted) in [[gmail-access|Gmail Access]]; `gog` spans more APIs and mutating operations when explicitly allowed.

## Details

- **Install:** `brew install` per [Quickstart](https://gogcli.sh/) on gogcli.sh; MIT license; active development (steipete/gogcli on GitHub).
- **Output:** `--json` envelope on stdout; `--plain` TSV for `awk`; stderr for prompts and warnings (pipe-safe).
- **Agent safety:** Safety profiles and bundled agent skill documented on site; read-only audit modes (Drive `tree`, `du`, Contacts `dedupe` preview).
- **Fit:** [[Tool]] / [[AI Agent]] - Google Workspace CLI for humans, scripts, and agents.
- **Contrast:** Official Gmail MCP ([[gmail-access|Gmail Access]]); Composio managed MCP; raw `curl` + Google REST APIs.
- **Caveats:** Not affiliated with Google; Workspace accounts may block personal OAuth apps (e.g. `john.kamenik@gomboc.ai` in gmail-access research).
