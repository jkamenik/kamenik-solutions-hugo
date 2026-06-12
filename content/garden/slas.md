---
title: "SLAs"
date: 2026-05-17
lastmod: 2026-06-12
draft: false

keywords:
  - SLAs
  - SLA
  - Service Level Agreement
  - Service Level Agreements

params:
  aliases:
    - SLA
    - Service Level Agreement
    - Service Level Agreements
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "New"
aliases:
  - /radar/techniques/slas
---

[SLAs](https://en.wikipedia.org/wiki/Service-level_agreement)

**Service level agreements (SLAs)** are measurable commitments between a provider and a customer: availability, response time, support windows, and remedies when targets are missed. We **adopt** defining SLAs (and the **SLO/SLI** machinery behind them) for **[[Software as a Service]]** and managed platforms so sales, engineering, and ops share the same numbers.

## Blurb

> A service-level agreement (SLA) defines the level of service expected by a customer from a supplier, laying out the metrics by which that service is measured and the remedies or penalties, if any, should the agreed-on service levels not be achieved.

## Summary

**SLA vs SLO vs SLI:**

| Term | Meaning |
|------|---------|
| **SLI** | What you measure (e.g. successful requests / total) |
| **SLO** | Internal target (e.g. 99.9% over 30 days) |
| **SLA** | Customer-facing promise, often with credits or termination rights |

**Why adopt:**

- **[[Enterprise Ready]]** procurement expects written uptime and support tiers
- Aligns product and **[[DevOps]]** on error budgets before **[[Continuous Deployment]]** pace outruns reliability
- Forces honest capacity planning (see **[[SRE]]** practices)

**Common SLA metrics:**

| Metric | Example commitment |
|--------|-------------------|
| **Availability** | 99.9% monthly API uptime |
| **Latency** | p95 < 300ms for core APIs |
| **Support** | P1 response within 1 hour (business hours) |
| **RTO/RPO** | Recovery objectives for disaster scenarios |

**What to avoid:** marketing "five nines" without instrumentation; SLAs you cannot measure from production telemetry; unlimited liability without error-budget policy.

## Details

| Topic | Notes |
|-------|--------|
| **Measurement** | SLIs from real probes and RED metrics; no manual spreadsheet honesty |
| **Exclusions** | Document maintenance windows, customer-caused outages, force majeure |
| **Credits** | Tie remedies to repeatable formulas; legal review |
| **Internal SLO** | Set SLO stricter than SLA so you miss the customer line rarely |
| **Incidents** | Postmortems when SLO burn rate spikes; feed back to architecture |

**References**

- [Wikipedia: Service-level agreement](https://en.wikipedia.org/wiki/Service-level_agreement)
- [Google SRE: SLI, SLO, SLA](https://sre.google/sre-book/service-level-objectives/)
