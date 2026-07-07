---
title: gog
date: '2026-05-26'
lastmod: '2026-07-02'
draft: false
keywords:
- gog
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - ai-agent
---

[gog](https://gogcli.sh/). Is a single-binary CLI for Google Workspace (Gmail, Calendar, Drive, Docs, Sheets, Slides, Contacts, Tasks, Chat, and Workspace Admin).

## Summary

**Garden stance:** We **assess** gog for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

- **Install:** `brew install` per [Quickstart](https://gogcli.sh/). On gogcli.sh; MIT license; active development (steipete/gogcli on GitHub).
- **Output:** `--json` envelope on stdout; `--plain` TSV for `awk`; stderr for prompts and warnings (pipe-safe).
- **Agent safety:** Safety profiles and bundled agent skill documented on site; read-only audit modes (Drive `tree`, `du`, Contacts `dedupe` preview).
- **Fit:** [[Tool]] / [[AI Agent]] - Google Workspace CLI for humans, scripts, and agents.
- **Contrast:** Official Gmail MCP ([[gmail-access|Gmail Access]]); Composio managed MCP; raw `curl` + Google REST APIs.
- **Caveats:** Not affiliated with Google; Workspace accounts may block personal OAuth apps (e.g. `john.kamenik@gomboc.ai` in gmail-access research).

### History
