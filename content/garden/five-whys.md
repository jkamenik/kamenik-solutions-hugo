---
title: "Five Whys"
date: 2026-06-22
lastmod: 2026-06-22
draft: false

keywords:
  - Five Whys
  - 5 Whys
  - Five Whys Root Cause Analysis

params:
  aliases:
    - 5 Whys
    - Five Whys Root Cause Analysis
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: "No Change"
---

[Five Whys](https://en.wikipedia.org/wiki/Five_whys)

The [Five Whys](https://en.wikipedia.org/wiki/Five_whys) technique asks "why?" repeatedly to trace a problem from its visible symptom to a fixable root cause. We **assess** it because it is fast and widely used in postmortems, but real failures branch and shallow answers produce useless action items. It belongs under **[[Technique]]** alongside **[[Incident Management]]** and **[[SRE]]** learning loops. Treat "five" as a depth heuristic per branch, not a literal question count.

## Blurb

> By repeating why five times, the nature of the problem as well as its solution becomes clear. (Taiichi Ohno)

## Summary

Five Whys looks simple on paper. In practice each answer can fork into multiple valid next questions. You are building a tree of cause chains, not a single straight line.

| Pitfall | What goes wrong | Fix |
|---------|-----------------|-----|
| **Literal five** | Stopping at an arbitrary depth | Follow each branch until you reach a changeable process |
| **Weak early whys** | Filler causes that cannot be implemented | Require quality answers for the first three levels |
| **Single branch only** | Missing parallel causes | Start from **[[Fishbone diagram]]**, then Five Whys on each rib |
| **Blame stopping point** | "Human error" as the root | Push to process, guardrail, or automation gaps |

**Facilitation rule:** Tell the group the first three "why" answers must be specific and actionable. Weak early layers poison every branch below them.

**Sibling technique:** **[[First Principles]]** is the forward-looking design counterpart. Use it when choosing architecture, not when tracing an incident backward.


## Details

### Branching Workflow

1. State the observable problem as a fact the group agrees on.
2. Ask "why?" and capture **every** plausible answer, not just the first.
3. For each answer, ask "why?" again. Track branches separately (whiteboard, doc outline, or **[[Fishbone diagram]]**).
4. Stop a branch when the fix is a durable process, guardrail, or automation change.
5. Prioritize action items on branches that recur across incidents.

### Quality Bar for Early Layers

The first three answers should name mechanisms, not vibes. Compare:

| Weak | Strong |
|------|--------|
| "Someone was careless" | "Runbook step 4 has no verification gate" |
| "Deploy was rushed" | "Change window has no rollback checklist" |
| "Monitoring failed" | "Alert routed to a queue with no on-call subscription" |

### When to Pair with Fishbone

Use **[[Fishbone diagram]]** (or a mindmap stand-in) when the incident spans people, process, tooling, and environment. Run Five Whys on the highest-signal ribs after brainstorming.
