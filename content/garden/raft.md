---
title: Raft
date: '2026-07-29'
lastmod: '2026-07-29'
draft: false
keywords:
- Raft
- Raft Consensus
- Raft Consensus Algorithm
params:
  aliases:
  - Raft Consensus
  - Raft Consensus Algorithm
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: New
    subcategories:
    - software-architecture
---

[Raft](https://raft.github.io/) is a leader-based consensus algorithm for replicated state machines. We **adopt** it as the default mental model for quorum logs, leader election, and CP control planes.

## Blurb

> Raft is a consensus algorithm that is designed to be easy to understand.

## Summary

**What it is:** Consensus decomposed into leader election, log replication, and safety. Equivalent to Multi-Paxos in fault tolerance. A majority of `2f+1` replicas must be alive to make progress. Designed by Diego Ongaro and John Ousterhout (USENIX ATC 2014).

**When to use:**

| Situation | Notes |
|-----------|--------|
| Learn consensus | Clearest teaching path before reading Paxos papers |
| Review etcd, Consul, or similar | Most implementations follow Raft shapes |
| Design CP metadata | Matches [[CAP Theorem]] CP quorum stores |

**When to skip:**

- Wide-area clusters with wild RTT variance (timeouts and single-leader stalls hurt)
- Need for any healthy replica to drive writes without election windows
- Prefer researching [[QuePaxa]] / [[Meerkat]] for timeout-light SMR

**Trade-offs:**

| Strength | Cost |
|----------|------|
| Understandable decomposition | Leader is a temporary single point of write progress |
| Broad industry implementations | Liveness depends on partial synchrony and tuned timeouts |
| Formal TLA+ specs exist | Mis-tuned election timeouts cause thrashing or slow failover |

**Pairs with:** [[CAP Theorem]] for CP vocabulary. [[TLA+]] for checking membership and safety. Contrast with [[QuePaxa]] when WAN or adversarial networks matter.

## Details

### Core Pieces

1. **Leader election** - One leader per term. Followers time out and campaign if heartbeats stop.
2. **Log replication** - Clients write through the leader. Entries commit when a majority replicates them.
3. **Safety** - Committed entries never change. Election restrictions keep logs consistent.

### Practical Notes

- Cluster size is usually odd (`3`, `5`, `7`) so majority quorums remain clear after failures.
- Reads served only by the leader need leases or linearizable read paths. Stale follower reads are a separate product choice.
- Membership changes are a sharp edge. Prefer the dissertation's simpler joint-consensus variant when changing voters.

### References

- [The Raft Consensus Algorithm](https://raft.github.io/)
- Diego Ongaro and John Ousterhout, [In Search of an Understandable Consensus Algorithm](https://raft.github.io/raft.pdf) (extended version)
- Ongaro Ph.D. dissertation (includes TLA+ specification)
