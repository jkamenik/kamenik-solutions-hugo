---
title: 'DSO Conjecture'
date: 2026-07-15
lastmod: 2026-07-17
keywords:
  - DevSecOps
  - DSO
  - CAP Theorem
---
The Developer-Security-Operations (DSO) conjecture is [[CAP Theorem]] applied to engineering orgs. Like CAP's famous "pick two," it is a teaching shortcut for alignment: under pressure, you drop a pillar. While Eric Brewer later warned that CAP's "2 of 3" framing oversimplifies real systems, it stands as a good framing that is broadly applicable.  This is my personal conjecture from years of working in software orgs of all types.

The DSO Conjecture states that a business's software engineering organization can provide at most two of these three guarantees:

- **D**eveloper Tolerance - How far the company tolerates arbitrary developer choices (language, framework, toolchain).
- **S**ecurity Consistency - How reliably the company keeps systems and data secure under change.
- **O**perational Availability - How reliably the product or service stays available to customers.

No pair is universally better. Problems start when a company or team isn't clear about which guarantees are the real ones.

<!--more-->

## The Company Types

At most you can have two guarantees. You do not need two. Undecided and single-letter rows are fine as early stages of maturing. But real maturity is found when you settle on a pair.

| Trade-offs  | Meaning                                                                                                                                                                                                    | Common Terms Used                                                                 |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| (undecided) | No guarantee set chosen yet. Experimentation is fine until scale or regulation forces a pick.                                                                                                              | "Startup", "Agile", "Greenfield"                                                  |
| D           | Developer freedom first. A common early stage while product-market fit is still unclear.                                                                                                                   | "Developer Focused", "Fail fast"                                                  |
| S           | Security first, often from regulation or a security product. Fine as a stage if the plan adds D or O later.                                                                                                | "High Sec", "Compliant", "Regulated"                                              |
| O           | Operations first. Platform or provider mindset while the service must stay up.                                                                                                                             | "Highly Available", "NOC", "Provider", "Platform"                                 |
| DO          | Balance feature delivery against keeping production up. Security often lands as backlog enhancements that steal Dev time. Some teams brand this "DevSecOps" to widen appeal without changing the tradeoff. | "Production Ready", "Automated", "DevOps"                                         |
| SO          | Balance security with operational demands. Non-security change is gated. Security and platform updates keep moving.                                                                                        | "Secure", "SecOps", "Shared Fate"                                                 |
| DS          | Ship highly secure software; customers own day-to-day ops and availability.                                                                                                                                | "Single App", "Zero External Dependencies", "Simple deployment", "Endpoint Agent" |

None of these is wrong when the tradeoffs match the requirements. A greenfield spike that starts undecided or at pure D can be the right move. Stay there only if maturing into a pair is part of the plan. It gets dangerous when the company stops at one pillar and flip-flops among the other two without choosing. Marketing that sells all three while engineering is quietly DO or SO creates the same pain.

### Pivoting: Architecture, Process, and Tools Headwinds

A common issue I see is the business wants to pivot to or add an additional vertical to the addressable market segment.  If the new market segment already matches the pillar-pair then success can be had.  However, switching to a market where the pillar-pair is different results in failure.

Once a pair is real, architecture, processes, and tools drift toward those pillars. Pipelines, review gates, platform defaults, hiring loops, and even repo layout start assuming that tradeoff. Switching pillars later is not a slogan change. It is full rework: rebuild controls, retrain teams, and retire habits that optimized the old pair.  It is not a simple new segment focus.

A great example of this is going from a banking vertical to a medical vertical vs going from CISO-types to Developer-types.  The first will likely be possible, while the second will not.  Banking and Medical verticals are both highly regulated SO style businesses, and while the exact details differ, their risk stance is similar enough to have success.  However, CISO-types are strongly S or SO, while Developer-types are strongly D or DO.  Those are incompatible pairs, so the org's locked architecture will fight the new buyer.

### Circumventing the Conjecture with One Role

Another failure mode is picking one pillar, then stuffing the other two into a single job title. That is an attempt to circumvent the conjecture. It sets that role up to fail.

Example: a security-focused org (S) hires "DevOps" without saying whether D or O is the real partner pillar. The person is asked to maximize developer freedom and operational availability at once. Under pressure they will pick the wrong missing pillar for that week's crisis.

The best path is clear alignment communication. Name the two guarantees and soften the expectation on the other. Then hire and measure against that pair.

## Shielding Alignments

Larger companies often need offerings aligned to different pillars than other parts of the company or the company as a whole. This can work with dedicated teams that realign to the needed pair. Those teams need to be shielded by charter, product boundary, or P&L success.

### Example: Google Cloud Platform

[[Google Cloud Platform|GCP]] leans SO as a company. Shared fate, secure defaults, and opinionated platform hygiene favor Security Consistency and Operational Availability over unbounded Developer Tolerance.

Two clear SO signals:

- **Always-on encryption.** Google encrypts customer content at rest by default. No opt-in. Security and ops hygiene are baked in; developers only get to choose between provider managed and customer managed keys.
- **[[Google GKE|GKE]] node auto-upgrade.** Nodes upgrade by default so the fleet stays current; but the choice of upgrade window allows it to be within a maintenance window. This forces the developer to ensure their apps are architected to tolerate such maintenance.  Platform security updates keep moving even when product teams would rather freeze.

That is the org lean, but not true of every GCP offering.  Take **Compute Engine**: it is a more traditional IaaS offering, which leans DO.  Pick the OS, own the guest stack, schedule your own patching (VM Manager helps, but it is still your job). Google still encrypts disks by default. Beyond that, Developer Tolerance and operational control sit with the customer. Security of the guest OS and workload is not forced.

Shielding is how Google can stay SO-minded overall while still selling a DO-leaning offering. Different team, different pair, same company. Because of this customers need to understand the trade-off not for GCP as a whole, but of each offering and choose accordingly.  They should pick the offering that matches *their* pair, not assume every GCP service is SO.

## Softening Jargon: Eventual Consistency

Orgs often soften a missing pillar without naming the loss. The softener sits on the pillar that is **not** really guaranteed. The other two are the real priorities.

In CAP, when availability and partition tolerance matter most, teams say "eventual consistency." The word "eventual" softens Consistency. That signals AP: Availability and Partition tolerance are the critical pair. Consistency is deferred, not inherent. Apps must work around stale or divergent reads.

Businesses use the same pattern. Softening one pillar in language implicitly names the other two as the real pair.  "Java shop" for example, indicates that developer choice is secondary. Security and Ops are what the org will actually facilitate.  While "Secure by design" indicates that security is thought of as a developer motion, not a stand-alone function.  Therefore, Developer and Ops are the focus.

Trade-offs are rarely stated outright. Listen for which pillar gets the softener. That is usually the one that will yield under pressure.

| Softener                         | Pillar being softened | Real pair                                            |
| -------------------------------- | --------------------- | ---------------------------------------------------- |
| "Eventual consistency"           | Consistency (CAP)     | Availability + Partition tolerance                   |
| "Secure by design" / "Automated" | Security Consistency  | Developer Tolerance + Operational Availability (DO)  |
| "Java shop" / "approved stack"   | Developer Tolerance   | Security Consistency + Operational Availability (SO) |


## Sources

- Eric Brewer, [CAP Twelve Years Later: How the "Rules" Have Changed](https://sites.cs.ucsb.edu/~rich/class/cs293b-cloud/papers/brewer-cap.pdf) (IEEE Computer, 2012)
- [Default encryption at rest](https://docs.cloud.google.com/docs/security/encryption/default-encryption)
- [GKE: Auto-upgrading nodes](https://cloud.google.com/kubernetes-engine/docs/how-to/node-auto-upgrades)
- [Shared responsibilities and shared fate on Google Cloud](https://docs.cloud.google.com/architecture/framework/security/shared-responsibility-shared-fate)
- [Compute Engine OS patch management (VM Manager)](https://cloud.google.com/compute/vm-manager/docs/patch)
- Tyler Treat, [Security, Maintainability, Velocity: Choose One](https://bravenewgeek.com/security-maintainability-velocity-choose-one/) (parallel org tradeoff framing)
