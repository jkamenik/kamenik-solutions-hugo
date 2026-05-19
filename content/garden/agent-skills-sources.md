---
title: "Agent Skills - Sources"
date: 2026-05-06
lastmod: 2026-05-18
draft: false

keywords:
  - Agent Skills - Sources

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "New"
    subcategories:
      - ai-techniques
      - claude-code

aliases:
  - /radar/techniques/agent-skills-sources
---

A living research document tracking good sources of [[Agent Skills Framework|agent skills]] to draw from. Covers [[Claude Code]], [[Gemini CLI]], and cross-ecosystem skill/prompt repositories.

> **Maintenance:** Review quarterly. Update "last checked" dates when vetting a source. Remove dead or low-quality links.

## Blurb

> The SKILL.md format is an open standard for teaching thinking AI models specific, repeatable skills. A growing ecosystem of community repositories, marketplaces, and cross-agent collections makes skills portable across Claude Code, Gemini CLI, Cursor, Codex, and others.

## Official Sources

| Source | URL | Notes |
|--------|-----|-------|
| Anthropic Skills Docs | https://code.claude.com/docs/en/skills | Canonical SKILL.md format spec |
| anthropics/skills (GitHub) | https://github.com/anthropics/skills | Anthropic's own first-party skills; reference implementations |
| Claude Code issue tracker | https://github.com/anthropics/claude-code/issues | Community bug reports often reveal undocumented skill patterns |

## Curated "Awesome" Lists

Aggregator repos and sites , good for broad discovery.

| Source | Notes | Last Checked |
|--------|-------|--------------|
| [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) | Skills, hooks, slash-commands, orchestrators, plugins. Most comprehensive single list. | 2026-05-06 |
| [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills) | Focused on SKILL.md-format skills; ~8.7k stars | 2026-05-06 |
| [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) | 1000+ production-ready skills across Claude.ai, Claude Code, and coding agents | 2026-05-06 |
| [rohitg00/awesome-claude-code-toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit) | 135 agents, 35 skills, 42 commands, 176+ plugins, 20 hooks, 15 rules | 2026-05-06 |

## Individual Collections

Maintained by practitioners , often higher signal-to-noise than aggregators.

| Source | URL | Notes | Last Checked |
|--------|-----|-------|--------------|
| wshobson/commands | https://github.com/wshobson/commands | Production-ready slash commands; good engineering workflow patterns | 2026-05-06 |
| glebis/claude-skills | https://github.com/glebis/claude-skills | Personal collection; broad use-cases | 2026-05-06 |
| alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 232+ skills across Claude Code, Codex, Gemini CLI, Cursor | 2026-05-06 |
| garrytan/gstack | https://github.com/garrytan/gstack | [[gbrain]] author's exact Claude Code setup; 23 opinionated tools spanning CEO, Designer, Eng Manager, Release Manager, Doc Engineer, and QA roles | 2026-05-06 |

## Marketplaces & Directories

| Source | URL | Notes |
|--------|-----|-------|
| SkillsMP | https://skillsmp.com/ | Marketplace for agent skills across Claude, Codex, ChatGPT |
| Toolradar blog | https://toolradar.com/blog/best-claude-code-skills-2026 | Curated top-20 list; good for quick survey |
| Firecrawl blog | https://www.firecrawl.dev/blog/best-claude-code-skills | Editorial picks; refresh periodically |
| ScriptByAI resource list | https://www.scriptbyai.com/claude-code-resource-list/ | Broad 2026 resource compilation |

## MCP Servers (Complements Skills)

MCP servers extend *what tools Claude can call*; skills extend *how Claude reasons*. Both compound.

| Source | URL | Notes | Last Checked |
|--------|-----|-------|--------------|
| modelcontextprotocol/servers | https://github.com/modelcontextprotocol/servers | Official reference implementations | 2026-05-06 |
| wong2/awesome-mcp-servers | https://github.com/wong2/awesome-mcp-servers | Most-linked community list | 2026-05-06 |
| mcp-awesome.com | https://mcp-awesome.com/ | 1200+ quality-verified servers, searchable directory | 2026-05-06 |
| abordage/awesome-mcp | https://github.com/abordage/awesome-mcp | Auto-updated daily; good for freshness | 2026-05-06 |

## Cross-Ecosystem Inspiration

Not SKILL.md format, but good sources for *ideas* , patterns that adapt directly.

| Source | Notes |
|--------|-------|
| Cursor rules repos (`awesome-cursorrules`) | `.cursorrules` files are functionally similar to SKILL.md; large existing corpus |
| GitHub Copilot custom instructions | Per-repo instructions that shape behavior , same pattern, different runtime |
| ChatGPT custom instructions / GPT Actions | Prompt patterns for persona, workflow, and tool-use |
| OpenAI Codex CLI plugins | SKILL.md format is cross-compatible; Codex skills often translate directly |

## Blogs & Articles

| Source | URL | Notes |
|--------|-----|-------|
| DEV Community - Claude Code Skills Practical Guide | https://dev.to/muhammad_moeed/claude-code-skills-a-practical-guide-for-2026-3f6p | Hands-on walkthrough |
| Medium - 10 Must-Have Skills | https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 | Quick survey of high-value skills |

## Evaluation Criteria

When vetting a new source:

1. **Format compliance**; Is it SKILL.md format, or requires adaptation?
2. **Cross-agent portability**; Works only in Claude Code, or also Gemini CLI / Cursor / Hermes?
3. **Maintenance signal**; Last commit date, open issues, star trajectory.
4. **Domain fit** (DevSecOps, PKM, automation) relevant to [[Kamenik Solutions]] or personal use?
5. **Quality bar**; Are skills self-contained with a clear trigger description in frontmatter?

## Open Threads

- Survey `hesreallyhim/awesome-claude-code` for DevSecOps and PKM-relevant skills to import

## See Also

- [[Agent Skills]], framework overview
- [[gbrain]], two-layer page convention used by this document
- [[hermes-agent]], local agent runtime
- [[Claude Code]]
- [[Gemini CLI]]
