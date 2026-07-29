---
title: QuePaxa
date: '2026-07-29'
lastmod: '2026-07-29'
draft: false
keywords:
- QuePaxa
- QuePaxa Consensus
params:
  aliases:
  - QuePaxa Consensus
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: New
    subcategories:
    - software-architecture
---

[QuePaxa](https://bford.info/pub/os/quepaxa/quepaxa.pdf) is a crash-fault consensus protocol with Raft-class normal-case speed that does not depend on timeouts for liveness. We **assess** it for WAN and hostile-network state machine replication.

## Blurb

> We present QuePaxa, the first protocol offering state-of-the-art normal case efficiency without depending on timeouts.

## Summary

**What it is:** SOSP 2023 protocol from Tennage, Basescu, Ford, and coauthors. Randomized asynchronous consensus core plus a one Round-Trip Time (RTT) fast path for a preferred leader. Concurrent proposers cooperate instead of thrashing. Hedging delays replace conservative election timeouts.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Unstable WAN RTTs | Avoid Raft-style false timeouts and long failover |
| DoS or slow-leader risk | Async core stays live when a single leader is targeted |
| Research / greenfield SMR | Compare before defaulting to [[Raft]] |

**When to skip:**

- Stable LAN clusters where Raft already meets SLOs
- Need for off-the-shelf libraries with long production track records
- Teams that will not operate a less common protocol

**Trade-offs:**

| Strength | Cost |
|----------|------|
| Liveness without timeout tyranny | Newer; fewer battle-tested libraries than Raft |
| Normal-case Multi-Paxos-class throughput | Non-leader proposals may take more RTTs |
| Adaptive leader and hedging (bandit-style) | Operational mental model is harder than Raft |

**Pairs with:** [[Raft]] as the industry baseline. [[Meerkat]] as the first known industrial QuePaxa deployment experiment (Cloudflare Research). [[CAP Theorem]] for CP quorum framing. [[TLA+]] / SPIN-style verification culture from the paper appendices.

## Details

### Design Highlights

1. **Async core** - Guarantees progress under asynchrony with high probability via randomized priorities (FLP workaround).
2. **Fast path** - Designated leader can commit in one round trip by priority selection.
3. **Hedging** - Later proposers wait short delays instead of firing costly view changes.
4. **Adaptation** - Leader choice and hedge schedule adjust to measured conditions.

### Reported Results (Paper)

- LAN ~584k cmd/sec; WAN ~250k cmd/sec under normal conditions (prototype vs Multi-Paxos class).
- Remains live under attacks and misconfigurations that stall Raft / Multi-Paxos.
- Hedging can be set aggressively short without losing liveness from false triggers.

### References

- [QuePaxa PDF](https://bford.info/pub/os/quepaxa/quepaxa.pdf) (SOSP 2023)
- Cloudflare, [Introducing Meerkat](https://blog.cloudflare.com/meerkat-introduction/) (industrial interest)
