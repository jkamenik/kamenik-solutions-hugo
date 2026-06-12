---
title: "Genesis"
date: 2026-04-15
lastmod: 2026-06-12
draft: false

keywords:
  - Genesis
  - Gensis

params:
  aliases:
    - Gensis
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "No Change"
    subcategories:
      - ai-agent
aliases:
  - /radar/tools/genesis
---

[Genesis](https://github.com/xeeva/Genesis) is a **[[Claude Code]]** meta-project: you run Genesis inside Claude, describe a new app (stack + name), and it scaffolds a sibling repo. The scaffold includes `CLAUDE.md`, `.claude/agents/`, `.claude/skills/`, hooks, `.mcp.json`, memory seeds, and starter code. We rate it **assess**: worth a pilot when bootstrapping greenfield Claude-native repos; this vault already hand-rolls the same **[[Agent Skills Framework]]** patterns.

## Blurb

> The Claude that builds Claudes. Bootstrap fully-equipped Claude Code projects in under two minutes.

## Summary

**Problem it solves:** productive Claude Code needs upfront investment (project rules, agents, skills, hooks, MCP, permissions). Most teams ship a thin `CLAUDE.md` and underuse subagents and skills.

**Four-phase workflow:**

| Phase | Output |
|-------|--------|
| **Interview** | 1-4 clarifying questions |
| **Plan** | Agents, skills, MCP list, folder layout for approval |
| **Generate** | Full project tree in one pass |
| **Finalise** | Git init, registry entry, next steps |

**Generated artifacts (typical):**

- `CLAUDE.md` with stack-specific standards
- `.claude/agents/` (test-runner, reviewer, domain agents)
- `.claude/skills/` (`/test`, `/lint`, `/review`, `/commit` + domain skills)
- `.claude/settings.json` (permissions, format hooks)
- `.mcp.json`, memory files, app boilerplate, `.gitignore`

**Supported stacks:** Node/TS, Python, Go, Rust, Ruby, Java/Kotlin (profiles include linters, tests, folder layout).

**When to assess:**

- Starting many similar Claude Code repos and want consistent scaffolding
- Teaching teams the **[[Agent Skills Framework]]** layout by example
- You already **trial** **[[Claude Code]]** and want faster first-session productivity

**When to skip:**

- Primary workflow is **[[Cursor]]** / **[[cursor-agent]]** (Genesis is Claude Code-specific)
- Monorepo with established agent conventions (merge by hand, do not overwrite)
- You only need a single skill file, not a full project factory

## Details

| Topic | Notes |
|-------|--------|
| **Prerequisites** | Claude Code CLI, git, Node 18+; bash/zsh/PowerShell |
| **Install** | Clone to e.g. `~/claude/genesis`, run `claude` in that directory |
| **Skills** | `/genesis`, `/registry`, `/validate`, `/update` inside Genesis |
| **First run** | Writes `personalisation.md` + `environment.md` (gitignored) |
| **Security** | Review generated code and MCP configs; MIT license with disclaimer |

**References**

- [Genesis (GitHub)](https://github.com/xeeva/Genesis)
- [Documentation](https://xeeva.github.io/Genesis/)
