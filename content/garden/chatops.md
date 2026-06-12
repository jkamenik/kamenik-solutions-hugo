---
title: "ChatOps"
date: 2023-07-23
lastmod: 2026-05-18
draft: false

keywords:
  - ChatOps

params:
  garden:
    kind: item
    usefulness: hold
    category: technique
    movement: "No Change"
aliases:
  - /radar/techniques/chatops
---

[ChatOps](https://en.wikipedia.org/wiki/ChatOps) is the practice of running operations through a chat interface: posting alerts into channels and/or invoking bots that execute commands. Platforms like **[[Slack]]** encourage it heavily (thousands of integrations). We rate the **technique** **hold**: fine for memes and low-stakes coordination; a bad default for production **[[DevSecOps]]**.

## Blurb

> ChatOps is a collaboration model that connects people, tools, process, and automation into a transparent workflow.

## Summary

**Two flavors:**

1. **Alerting in chat:** notifications from CI, monitoring, or deploy tools land in team channels.
2. **Actions from chat:** slash commands and bots mutate infrastructure (deploy, restart, encrypt disks, etc.).

**Why hold:** chat is high-noise and low-audit compared to pipelines and break-glass tools. Mixing pager-worthy events with coworker banter trains people to ignore channels. Giving chat bots production credentials fails most audits and creates irresistible distraction for engineers.

**What to do instead:** route pages through **[[Incident Management]]** tooling; run automation via CI, **[[GitOps]]**, or approved runbooks with identity separation. Use **[[Slack]]** (**trial**) for human coordination, not as the control plane.

## Details

### Alerting in chat

Alerting matters in **[[DevSecOps]]**; the signal must be scarce and actionable. A `#production` channel that also gets jokes and threads buries real incidents. Prefer dedicated on-call paths with explicit severity, not "whatever showed up in Slack."

### Actions from chat

Triggering automation from chat sounds convenient until someone runs the wrong command in the wrong channel. Production access for chat integrations is a liability; investment here dies on compliance reviews. Tools like **[[Keel]]** that lean on ChatOps are long-term dead ends for the same reason.

### Garden stance

**hold** for new ChatOps workflows. Existing bots: restrict scopes, document owners, plan retirement. Do not build new prod dependencies on chat commands.
