---
title: A Model of Communication
date: '2024-10-01'
lastmod: '2026-07-02'
draft: false
keywords:
- A Model of Communication
params:
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: No Change
    subcategories:
    - specification
aliases:
- /radar/techniques/a-model-of-communication
---

[A Model of Communication](https://campus-adr.net/ODRModule/a_model_of_communication.html) is a technique we use to limit standing privilege and grant audited, time-bound access instead. We **assess** it under **[[Technique]]** in the garden.

## Summary

**What it is:** A teaching model from Bill Warters' ODR learning module (Wayne State). It adapts Claude Shannon's information-theory diagram to human CMC. The sender encodes intent into a message, transmits it through a medium, and the receiver decodes it while noise may distort the signal. A feedback path closes the loop.

**Core components:**

| Element | Role |
|---------|------|
| Information source | Person or system with intent to convey |
| Encoder / message | Meaning packaged for the chosen medium |
| Transmitter / channel | Tool that carries the signal (email, chat, video) |
| Noise | Anything that degrades fidelity (latency, ambiguity, missing cues) |
| Decoder / destination | Receiver interprets meaning and acts |
| Feedback | Return path so the sender can adjust |

**Medium dimensions that matter for engineering teams:**

| Dimension | Lean / low bandwidth | Rich / high bandwidth |
|-----------|----------------------|------------------------|
| Timing | Async (email, tickets, docs) | Sync (calls, pair sessions, chat) |
| Social cues | Text-only, easy to misread | Video, tone, rapid clarification |
| Persistence | Durable record, slow loop | Ephemeral or live, fast loop |
| Noise risk | Ambiguity, tone gaps, delayed feedback | Scheduling cost, interruption, recording gaps |

**When to use the model:**

- Choosing default channels for a team (standups vs async status, incident comms vs design docs)
- Explaining why a "quick Slack" escalates or why email feels stuck
- Designing feedback loops (reviews, RFCs, office hours) so intent survives the medium

**When to skip:**

- You need a quantitative SLA or tooling matrix only (pair with runbooks and channel policies)
- The audience already has a mandated stack (model informs *how* to use it, not *whether* to buy)

**Relation to garden:** Sits in **[[Specification]]** alongside reference architectures. Useful when setting collaboration norms, not when picking a single vendor.

## Details

![Communication Model](https://campus-adr.net/ODRModule/CommunicationModelDiagram.png)

The diagram above is the human-CMC variant: it adds feedback and highlights that sender and receiver may share different context. Noise is not only technical. It includes cultural mismatch, partial attention, and medium limits (no tone in plain text, no thread history in a hallway conversation).

### Shannon-Weaver Lineage

Van Veenen and Warters trace the model to Shannon's work at Bell Labs (1940s). The simplified chain is source → encode → transmit → (noise) → receive → decode → destination. For ODR, the transmitter is often a computer; the same frame applies to engineering collaboration tools.

### Matching Medium to Message

Poor fit shows up as rework, escalation, or "we already decided this" loops. Examples:

| Message type | Poor medium | Better fit |
|--------------|-------------|------------|
| Nuanced disagreement | Long async thread without summary | Sync conversation plus written decision |
| Firm decision / policy | Verbal-only standup | Durable doc or ticket with owners |
| Quick unblock | Email chain | Sync chat or call |
| Audit trail needed | Ephemeral chat | Ticket or doc with version history |

### ODR Module Context

The [source module](https://campus-adr.net/ODRModule/a_model_of_communication.html) is part of a broader ODR orientation (limitations of CMC, positive effects, task-to-form mapping). The [module index](https://campus-adr.net/ODRModule/) links adjacent pages on not replicating face-to-face processes online. Licensed CC BY-NC-ND 3.0 for educational use.

### References

- [A Model of Communication](https://campus-adr.net/ODRModule/a_model_of_communication.html) (primary)
- [Communication Theory and ODR - an Orientation](https://campus-adr.net/ODRModule/) (module home)
