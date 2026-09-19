---
title: herdr
date: '2026-09-18'
lastmod: '2026-09-18'
draft: false
keywords:
- herdr
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: New
---

[herdr](https://herdr.dev) is an agent-native terminal multiplexer where coding agents run in real panes and keep working after you disconnect. We **adopt** it as the multiplexer in the TUI IDE stack.

## Blurb

> Herdr is where your coding agents live. However many you run, across however many projects, each in its own terminal. Walk away and they keep working. Come back from any machine and they're where you left them.

## Summary

Use herdr on the VPS to run the [[OpenCode]] TUI and any number of agents in workspaces, tabs, and panes. It marks each pane as working, blocked, idle, or done, which matters on a phone screen where you cannot babysit every pane.

It replaced [[tmux]] as the multiplexer of choice because of mouse support, agent state at a glance, and a similar experience to [[Supacode]]. Sessions live in a background server, so they survive laptop close and network drops.

Theming follows the outer terminal with `[theme] name = "terminal"`.

## Details

- **Upstream:** https://herdr.dev
- **Role:** terminal multiplexer and agent runtime in the TUI IDE stack
- **Model:** workspaces, tabs, and panes; lifecycle states for agents
- **Transport:** SSH bootstrap over [[Mosh]]; `herdr --remote` is SSH-only today
- **Integration:** first-class [[OpenCode]] lifecycle hooks via `herdr integration install opencode`
- **Related:** [[tmux]], [[Supacode]], [[Mosh]], [[OpenCode]], [[NeoVim]]
