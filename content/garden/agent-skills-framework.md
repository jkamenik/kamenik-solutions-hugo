---
title: Agent Skills Framework
date: '2026-04-20'
lastmod: '2026-07-07'
draft: false
keywords:
- Agent Skills Framework
- Agent Skills
params:
  aliases:
  - Agent Skills
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
    subcategories:
    - ai-techniques
aliases:
- /radar/techniques/agent-skills-framework
---

[Agent Skills Framework](https://agentskills.io/specification) packages repeatable agent know-how as a folder with a required `SKILL.md` (YAML frontmatter plus markdown instructions). We **adopt** it as the only realistic way to make agent behavior portable across models and providers.

## Summary

| When | Action |
|------|--------|
| Building portable ops for coding agents | Use the layout: one folder per skill, `SKILL.md` with strong `name` and `description` |
| One-off prompts in a single tool | Skip; inline rules or tool-native config may be enough |
| Importing community skills | Vet each repo; use [[Agent Skills - Sources]]; run in sandbox first |

**Portability:** Tool-native rules, system prompts, and vendor config do not travel. A `SKILL.md` folder ports across [[Claude Code]], [[Cursor]], [[Codex]], [[Gemini]], and other runtimes with path changes at most. That is the practical baseline for shared agent behavior in a multi-model estate.

**Layout:** `skills/<skill-name>/SKILL.md` plus optional `scripts/`, `references/`, `assets/`. The `description` field is the primary trigger signal. Keep the body under ~500 lines. Push detail into reference files.

**In this vault:** `agent-skills/skills/` mirrors the pattern. [[gbrain]] two-layer pages and identity files in `AGENTS.md` / `CLAUDE.md` sit alongside skills.

## Details

### Required Frontmatter
```yaml
---
name: my-skill          # lowercase, hyphens; matches folder name
description: "What it does and when to use it (trigger keywords live here)."
---
```
### Skill Types (Informal)

| Type       | Purpose                        | Example                                |
| ---------- | ------------------------------ | -------------------------------------- |
| Capability | Teach a concrete tool or API   | `apple-reminders`, `proofread`         |
| Behavioral | Layer policy on other skills   | `reminders-gtd`, `proofread-blog`      |
| Domain     | Your outcome-specific workflow | `morning-briefing`, `company-research` |

### Runtimes in the Garden

- [[Claude Code]]: `.claude/skills/` or shared `agent-skills/`
- [[Cursor]] / [[cursor-agent]]: `.cursor/skills/`
- [[Gemini]] CLI, [[Codex]], [[Cline]], [[OpenCode]]: tool-specific paths; core `SKILL.md` often ports with path changes only

See [[Agent Skills - Sources]] for official docs, awesome lists, and marketplaces.
