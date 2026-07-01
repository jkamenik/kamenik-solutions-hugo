---
title: Inter-process Communication (IPC)
date: '2025-12-21'
lastmod: '2026-07-01'
draft: false
keywords:
- Inter-process Communication (IPC)
- Inter-process Communication
params:
  aliases:
  - Inter-process Communication
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: No Change
    subcategories:
    - api
---

[Inter-process communication (IPC)](https://en.wikipedia.org/wiki/Inter-process_communication) is how cooperating processes on one host exchange data and synchronize work. We **assess** each mechanism in context because the right choice spans language runtimes, OS primitives, and network-shaped local APIs. Treat **[[RPC]]** as a separate pattern when traffic crosses machine boundaries. Prefer the simplest channel that meets isolation and reliability needs before adopting socket or **[[gRPC]]** stacks.

## Blurb

> In computer science, inter-process communication refers to the mechanisms and protocols an operating system provides to allow processes to manage shared data and synchronize their activity.

## Summary

IPC covers same-machine cooperation: pipes, shared memory, signals, Unix domain sockets, and runtime abstractions such as **[[GoLang]]** channels. It is not the same problem as service-to-service **[[RPC]]**, though many tools reuse network protocols locally for isolation and language boundaries.

**Pick carefully:** Not every IPC form fits every design. Some primitives suit local isolation; others inherit **[[RPC]]** coupling when stretched beyond one host. Match the mechanism to the boundary instead of defaulting to the most flexible option.

**Same-machine stance:** Local IPC is acceptable when it improves stability and maintainability on one host. That includes **[[gRPC]]** over Unix domain sockets for plugin hosts, sidecars, and tooling control planes (**[[Docker]]**, **[[Terraform]]**).

**Cross-network:** Once cooperation crosses a network boundary, stop calling it IPC. Prefer explicit service contracts (**[[REST]]**, bounded **[[gRPC]]** services). Apply the garden **hold** stance on general **[[RPC]]** for cross-computer work.

**When IPC fits:** parent/child processes, sidecars, plugin hosts, CLI tooling talking to a local daemon, or OS service models that standardize on sockets (for example systemd-style local APIs).

**When to pause:** if the design already spans hosts or teams, default to explicit **[[REST]]** or bounded **[[gRPC]]** service contracts instead of stretching IPC into distributed **[[RPC]]**.

**Tooling examples:** **[[Docker]]** and **[[Terraform]]** use **[[gRPC]]** for control-plane style communication between a client and a local or co-located process. That is an IPC-shaped use of RPC, not a license to treat remote procedure calls as the default integration style.

## Details

| Mechanism | Typical use | Garden note |
|-----------|-------------|-------------|
| **Pipes / FIFOs** | Simple parent-child or shell pipelines | Lowest ceremony; narrow contracts |
| **Shared memory** | High-throughput same-host data sharing | Needs strict synchronization discipline |
| **Unix domain sockets** | Local daemon APIs, container runtimes | Common when processes must stay isolated |
| **Language channels** | In-process goroutines or actor mailboxes | Prefer when all logic shares one runtime |
| **Local gRPC** | Plugin or tooling control planes | **assess**; see **[[gRPC]]** and **[[RPC]]** notes |

### Accept vs Avoid

| Situation | Stance |
|-----------|--------|
| Single host, need process isolation | Pipes, channels, Unix domain sockets, local **[[gRPC]]** |
| Single host, same runtime | Language-native channels first |
| Cross-network or cross-team service calls | Not IPC; design explicit APIs; **[[RPC]]** is **hold** |
| Network protocol reused locally for convenience | OK on one machine; do not copy the pattern to remote peers |

### Decision Checklist

1. Are both peers guaranteed to run on one machine (or one tightly coupled host group)?
2. Can you use a language-native channel instead of a wire protocol?
3. If you need sockets, is a documented local API enough without full **[[RPC]]** semantics?
4. If the answer to (1) is no, stop treating the problem as IPC and design an explicit service boundary.

### Failure Modes

- Stretching local **[[gRPC]]** patterns to remote services without versioning or failure semantics
- Treating any socket protocol as IPC even when peers live on different networks
- Picking shared memory or signals when a simpler pipe or channel would suffice
