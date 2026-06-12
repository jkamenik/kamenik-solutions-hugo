---
title: "Slack"
date: 2026-05-17
lastmod: 2026-05-21
draft: false

keywords:
  - Slack

params:
  garden:
    kind: item
    usefulness: trial
    category: platform
    movement: "New"
aliases:
  - /radar/platforms/slack
---

[Slack](https://slack.com/) is a team messaging and collaboration platform (channels, DMs, search, apps). We rate it **trial**: fine as the default human coordination layer when the org already pays for it; do not let Slack become your control plane for production.

## Blurb

> Slack is your productivity platform.

## Summary

**Use Slack for:** team chat, incident coordination rooms, lightweight notifications, and linking out to real systems (tickets, dashboards, runbooks).

**Avoid Slack for:** **[[ChatOps]]**-style bot commands against prod, mixing pager-grade alerts with casual channels, or granting integrations broad cloud/API scopes because "it's convenient."

**Garden alignment:** **[[ChatOps]]** is **hold**; Slack's app marketplace encourages patterns we reject for DevSecOps. Prefer dedicated on-call (**[[Incident Management]]**) and audited automation outside chat.

## Details

| Topic | Notes |
|-------|--------|
| **Alerting** | Mirror critical alerts into a dedicated channel; do not rely on Slack alone for paging |
| **Integrations** | Review OAuth scopes and retention; treat bots like production software |
| **Agents** | Omnichannel agents ([[OpenClaw]], [[hermes-agent]]) can attach here; same **hold** caution applies |
| **Alternatives** | Microsoft Teams, Google Chat, or matrix-style tools when customers mandate them |
