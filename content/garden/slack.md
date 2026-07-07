---
title: Slack
date: '2026-05-17'
lastmod: '2026-07-02'
draft: false
keywords:
- Slack
params:
  garden:
    kind: item
    usefulness: trial
    category: platform
    movement: No Change
aliases:
- /radar/platforms/slack
---

[Slack](https://slack.com/). Is a team messaging and collaboration platform (channels, DMs, search, apps).

## Blurb

> Boost productivity and save time with Slack‌ - ‌the AI work platform for managing projects, automating workflows, and connecting teams securely. Start working smarter today.

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
