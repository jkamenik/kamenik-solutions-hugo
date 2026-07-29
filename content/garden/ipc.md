---
title: Inter-process Communication (IPC)
date: '2025-12-21'
lastmod: '2026-07-29'
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

[Inter-process Communication (IPC)](https://en.wikipedia.org/wiki/Inter-process_communication). Is how cooperating processes on one host exchange data and synchronize work.

## Summary

**Garden stance:** We **assess** Inter-process Communication (IPC) for our estate.

**Key points:**

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
