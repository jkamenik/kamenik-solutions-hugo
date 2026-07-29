---
title: CAP Theorem
date: '2026-07-15'
lastmod: '2026-07-29'
draft: false
keywords:
- CAP Theorem
- "Brewer's Theorem"
- Brewer Theorem
params:
  aliases:
  - "Brewer's Theorem"
  - Brewer Theorem
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: New
    subcategories:
    - software-architecture
---

[CAP Theorem](https://en.wikipedia.org/wiki/CAP_theorem) says a distributed data store cannot guarantee Consistency, Availability, and Partition tolerance at the same time. We **adopt** it as the default vocabulary for consistency trade-offs in distributed design.

## Blurb

> You can have at most two of these properties for any shared-data system

## Summary

**What it is:** Brewer's conjecture (PODC 2000), later proved by Gilbert and Lynch. Under a network partition you must choose: keep serving possibly stale answers (favor Availability), or refuse unsafe reads/writes (favor Consistency).

**When to use:** Design reviews for multi-node stores, multi-region apps, **[[Microservices]]** data ownership, and **[[NoSQL]]** engine choice. Translate product SLOs into an explicit C vs A stance when partitions happen.

**When to skip:** Single-node or single-site systems with no partition risk. Do not use CAP as a slogan to reject SQL or transactions without a real distribution requirement.

| Trade-off under partition | Meaning | Typical examples |
|---------------------------|---------|------------------|
| CP | Prefer correct data; may error or block | Consensus quorum stores, many primary-replica DBs with failover |
| AP | Prefer answering; may return stale or divergent data | DNS-style caching, some eventually consistent KV stores |
| CA | Consistency + availability only if you assume no partitions | Classic single-site databases (not a wide-area guarantee) |

**Pairs with:** **[[First Principles]]** when teams treat "we need all three" as a requirement. **[[Software Architecture]]** for system-boundary decisions. Treat CAP Consistency as not the same as ACID transactional consistency.

## Details

### The Three Guarantees

| Guarantee | CAP meaning |
|-----------|-------------|
| Consistency | Every successful read sees the latest write (or errors). CAP-C is not ACID-C. |
| Availability | Every request to a non-failed node gets a response. It may not be the newest value. |
| Partition tolerance | The system keeps running when the network drops messages between nodes. |

On modern networks, partitions are assumed. Real designs are usually CP or AP during a partition, not a free CA triangle.

### Common Misreads

- **"Pick two" forever:** Outside a partition, many systems provide both C and A. The hard choice shows up when the network splits.
- **CAP-C equals ACID:** CAP Consistency is about latest-value visibility across replicas. ACID Consistency is about invariants inside a transaction.
- **AP means no correctness:** AP systems still need conflict rules, versioning, or repair. They trade linearizability during partitions, not all forms of correctness.
- **Microservices automatically need AP:** Service boundaries do not pick CAP for you. Shared databases and cross-service reads still force an explicit stance.

### How to Apply in Reviews

1. Name the data item and the failure mode (zone loss, region split, degraded link).
2. Ask which client outcomes are worse: stale/conflicting reads, or errors/timeouts.
3. Match the store and API (quorum, leader election, async replication, CRDTs) to that choice.
4. Document the choice in the design note. Do not hide it behind "highly available and strongly consistent."

### References

- [Wikipedia: CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem)
- Eric Brewer, [Towards Robust Distributed Systems](https://people.eecs.berkeley.edu/~brewer/PODC2000.pdf) (PODC 2000 keynote slides)
- Seth Gilbert and Nancy Lynch, "Brewer's conjecture and the feasibility of consistent, available, partition-tolerant web services" (ACM SIGACT News, 2002)
