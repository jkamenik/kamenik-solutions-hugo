---
title: Meerkat
date: '2026-07-29'
lastmod: '2026-07-29'
draft: false
keywords:
- Meerkat
- Cloudflare Meerkat
params:
  aliases:
  - Cloudflare Meerkat
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: New
---

[Meerkat](https://blog.cloudflare.com/meerkat-introduction/) is Cloudflare Research's experimental global consensus service built on [[QuePaxa]]. We **assess** it as a watch item for WAN control-plane consensus, not something you can adopt today.

## Blurb

> Meerkat is an experimental consensus service that is still in development.

## Summary

**What it is:** A replicated log service for small control-plane state across many data centers. Applications (KV store, leases) sit atop the consensus log. Any replica can accept client requests. Powered by [[QuePaxa]] instead of [[Raft]] to avoid leader-timeout outages on Cloudflare's noisy WAN.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Track industry SMR | Follow Cloudflare Research posts and papers |
| Design WAN control planes | Mine requirements: linearizability, majority live, any-replica writes |
| Compare to managed stores | Contrast with [[FoundationDB]]-style CP metadata products |

**When to skip:**

- Need a product you can run or buy now (Meerkat is internal-only, not production)
- Stable single-region clusters where Raft already works
- General-purpose databases (explicitly out of scope)

**Trade-offs:**

| Strength | Cost |
|----------|------|
| Targets global linearizable control plane | Still experimental; no public service |
| QuePaxa avoids Raft leader stalls | Consensus RTT cost remains; global placement adds latency |
| Batching, local stale reads, CAS/transactions planned | Best for infrequent writes, not hot data paths |

**Pairs with:** [[QuePaxa]] (protocol), [[Raft]] (baseline they rejected for WAN), [[CAP Theorem]] (CP quorum goals), [[TLA+]] (they plan formal verification of a Rust implementation).

## Details

### Target Properties (Cloudflare)

1. Strong consistency (linearizability for the KV example; serializability planned).
2. Available for reads and writes while a majority of replicas can communicate.
3. Crash faults only (not Byzantine). Same broad threat model class as Raft systems.

### Why Not Raft (Their Argument)

- Authoritative leader blocks writes during elections and when the leader is merely slow.
- WAN RTT variance makes election timeouts hard to tune.
- Concurrent leadership campaigns can thrash. Cloudflare reports Raft-related incidents from these failure modes.

### Limits They State

- Not a general database. Aimed at small, infrequently written control-plane data.
- Decision latency tracks majority RTT. Global replica placement trades availability for latency.
- Not deployed to production as of the introduction post. Proofs-of-concept up to ~50 worldwide replicas.

### References

- [Introducing Meerkat](https://blog.cloudflare.com/meerkat-introduction/) (Cloudflare Blog)
- [QuePaxa paper](https://bford.info/pub/os/quepaxa/quepaxa.pdf)
