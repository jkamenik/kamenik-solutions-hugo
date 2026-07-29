---
title: GitHub Spec Kit
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- GitHub Spec Kit
- Spec Kit
- Specify CLI
params:
  aliases:
  - Spec Kit
  - Specify CLI
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: New
    subcategories:
    - ai-agent
---

[GitHub Spec Kit](https://github.github.io/spec-kit/) is an intent-driven harness that scaffolds specifications, plans, tasks, and agent commands for [[Spec-Driven Development (SDD)|SDD]]. We **trial** it as a structured way to apply SDD across different AI coding agents.

## Blurb

> Spec Kit is an extensible, intent-driven harness that pushes any coding agent beyond code, guiding it across your SDLC or any business process.

## Summary

Spec Kit packages an SDD workflow into templates, scripts, and agent-specific commands. It keeps specification artifacts in the repository and supports many coding-agent integrations without making one agent the permanent choice.

- **Use when:** a team wants a repeatable SDD workflow with generated project scaffolding.
- **Value:** standard phases make requirements, plans, tasks, and implementation easier to inspect and review.
- **Trade-off:** the full workflow adds ceremony and generated files. Small changes may need only a subset of the phases.
- **Trial goal:** use it on a real multi-file feature and evaluate artifact quality, agent portability, and maintenance cost.

Related garden notes: [[Spec-Driven Development (SDD)]], [[Specification]], and [[AI Agent]].

## Details

Install the Specify CLI and initialize a project:

```bash
uv tool install specify-cli
specify init my-project --integration copilot
```

The standard workflow exposes ordered agent commands:

| Phase | Command | Purpose |
|-------|---------|---------|
| Constitution | `/speckit.constitution` | Define project principles and guardrails |
| Specify | `/speckit.specify` | Describe the what and why |
| Clarify | `/speckit.clarify` | Resolve material ambiguity |
| Plan | `/speckit.plan` | Establish the technical approach |
| Tasks | `/speckit.tasks` | Create actionable work items |
| Implement | `/speckit.implement` | Implement against the tasks and spec |
| Analyze | `/speckit.analyze` | Check consistency across artifacts |
| Converge | `/speckit.converge` | Reconcile implementation with intent |

A shorter path can use specify, plan, tasks, implement, and converge. Production work can add constitution, clarify, checklist, and analyze phases when the extra controls provide value.

Spec Kit supports many coding-agent integrations and includes a generic integration. This allows teams to keep the workflow while changing the agent that executes it.
