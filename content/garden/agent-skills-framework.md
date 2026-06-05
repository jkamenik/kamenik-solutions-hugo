---
title: "Agent Skills Framework"
date: 2026-04-20
lastmod: 2026-06-05

keywords:
  - Agent Skills Framework
  - Agent Skills
  - SKILL.md

params:
  aliases:
    - Agent Skills
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: "No Change"
    subcategories:
      - ai-techniques

aliases:
  - /garden/agent-skills/
  - /radar/techniques/agent-skills
  - /radar/techniques/agent-skills-framework
---

The [Agent Skills](https://agentskills.io/specification) format packages repeatable agent know-how as a folder with a required `SKILL.md` (YAML frontmatter plus markdown instructions). We **assess** it: portable across [[Claude Code]], [[Gemini]], [[Cursor]], [[Codex]], and other runtimes, but tool-specific extensions and discovery quality still vary. Use it when you want skills you can carry between agents. Pair with [[Agent Skills - Sources]] for vetted repos.

## Blurb

> Skills are reusable, discoverable modules that package instructions, scripts, and resources for AI agents. A skill is a directory with a required SKILL.md file and optional bundled resources. Skills use progressive disclosure: metadata stays in context; the body loads when the skill triggers; bundled files load on demand.

## Summary

| When | Action |
|------|--------|
| Building portable ops for coding agents | **Adopt** the layout: one folder per skill, `SKILL.md` with strong `name` and `description` |
| One-off prompts in a single tool | Skip; inline rules or tool-native config may be enough |
| Importing community skills | **Assess** each repo; use [[Agent Skills - Sources]]; run in sandbox first |

**Layout:** `skills/<skill-name>/SKILL.md` plus optional `scripts/`, `references/`, `assets/`. The `description` field is the primary trigger signal. Keep the body under ~500 lines. Push detail into reference files.

**In this vault:** `agent-skills/skills/` mirrors the pattern. [[gbrain]] two-layer pages and identity files in `AGENTS.md` / `CLAUDE.md` sit alongside skills.

## Details

### Required frontmatter

```yaml
---
name: my-skill          # lowercase, hyphens; matches folder name
description: "What it does and when to use it (trigger keywords live here)."
---
```

### Skill types (informal)

| Type | Purpose | Example |
|------|---------|---------|
| Capability | Teach a concrete tool or API | `apple-reminders`, `proofread` |
| Behavioral | Layer policy on other skills | `reminders-gtd`, `proofread-blog` |
| Domain | Your outcome-specific workflow | `morning-briefing`, `company-research` |

### Runtimes in the garden

- [[Claude Code]]: `.claude/skills/` or shared `agent-skills/`
- [[Cursor]] / [[cursor-agent]]: `.cursor/skills/`
- [[Gemini]] CLI, [[Codex]], [[Cline]], [[OpenCode]]: tool-specific paths; core `SKILL.md` often ports with path changes only

See [[Agent Skills - Sources]] for official docs, awesome lists, and marketplaces.
