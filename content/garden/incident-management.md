---
title: "Incident Management"
date: 2025-06-14
lastmod: 2026-05-18
draft: false

keywords:
  - Incident Management

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/incident-management
---

[Incident Management](https://en.wikipedia.org/wiki/Incident_management)

Incident Management is the practice of detecting, responding to, resolving, and learning from unplanned disruptions to production systems. It is a core discipline in [[SRE]] and [[DevOps]], any team running a production service needs it, even informally. Without a defined process, incidents become chaotic, response time suffers, and the same problems recur.

A mature incident management practice includes:

1. **Detection**; alerting and monitoring that surfaces issues before users report them (see [[OpenTelemetry]], [[Up-time Monitoring]])
2. **Response**; a defined on-call rotation, severity levels, and a clear incident commander role
3. **Communication**; a status page or channel where stakeholders get updates without interrupting responders
4. **Resolution**; runbooks and playbooks that responders can execute under pressure
5. **Learning**; blameless postmortems that produce action items, not finger-pointing

## Blurb

> Incident management is a term describing the activities of an organization to identify, analyze, and correct hazards to prevent a future re-occurrence. These incidents within a structured organization are normally dealt with by either an incident response team (IRT), an incident management team (IMT), or the Incident Command System (ICS).

## Summary

Every team shipping to production should adopt incident management, even if lightly. Start with severity definitions (P1–P3), an on-call schedule, and a postmortem template. The investment pays back immediately the first time a P1 hits and everyone knows their role. Tools like PagerDuty, Opsgenie, or even a simple Slack workflow can carry you a long way. The process matters more than the tooling.
