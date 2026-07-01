---
title: DORA Metrics
date: '2026-06-22'
lastmod: '2026-07-01'
draft: false
keywords:
- DORA Metrics
- DORA
- DORA Four Keys
params:
  aliases:
  - DORA
  - DORA Four Keys
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: No Change
---

[DORA metrics](https://dora.dev/) are the DevOps Research and Assessment team's validated measures of software delivery and operational (SDO) performance. The framework tracks throughput and stability with four core metrics, plus reliability as a fifth measure. We **adopt** them as the default engineering health baseline under **[[DevOps]]**. Treat them as directional delivery evidence, not executive value metrics on their own.

## Blurb

> DORA's research program represents nine years of research and data from over 36,000 professionals worldwide. Our team conducts research to understand the practices, processes, and capabilities that enable teams to achieve higher levels of software delivery and organizational performance.

## Summary

**The four keys (software delivery performance):**

| Metric | Dimension | What it measures |
|--------|-----------|------------------|
| **Deployment frequency** | Throughput | How often you successfully release to production |
| **Lead time for changes** | Throughput | Commit (or work start) to running in production |
| **Change failure rate** | Stability | Share of changes that degrade service or need remediation |
| **Failed deployment recovery time** | Stability | How long it takes to recover from a failed deployment or incident |

DORA reports and tooling may still label the fourth metric **time to restore service** (MTTR). Same intent: restore user-impacting service quickly.

**Fifth metric (operational performance):**

| Metric | What it measures |
|--------|------------------|
| **Reliability** | How well services meet user expectations (availability, latency, performance, scalability) |

Read all metrics together. High deploy frequency with a high change failure rate is not high performance.

**Performance tiers:** DORA research clusters teams from survey data each year. Tiers are emergent benchmarks, not fixed universal thresholds. Use [DORA Quick Check](https://dora.dev/quickcheck/) for current industry comparison. Use tiers for trend tracking, not vanity rankings.

**Reporting altitude and audience:**

| Audience | What to show | What to avoid |
|----------|--------------|---------------|
| **Delivery team** | Raw DORA metrics, drill-down dashboards | Business outcome claims the data cannot support |
| **Dependent teams** | Team-level trends tied to shared services | Org-wide rollups that hide local context |
| **Executives and budget holders** | Value story with 1-2 supporting metrics | Leading with DORA alone |

DORA answers "how healthy is delivery?" It does not answer "why should we fund the platform?" Map each metric to a stakeholder concern before rolling it up.

**Example link chain (stability → capacity → outcome):**

| DORA signal | Intermediate capability | Stakeholder outcome |
|-------------|-------------------------|---------------------|
| Lower change failure rate | Fewer fire drills | More predictable release dates |
| Faster recovery time | Less unplanned rework | More capacity for features |
| Higher deploy frequency | Smaller batches | Faster feedback on product bets |

Without that chain, measurement cost looks like overhead.

**Where DORA fits in the garden:**

| Practice | Relationship |
|----------|--------------|
| **[[DevOps]]** | DORA measures delivery culture outcomes |
| **[[Continuous Delivery]]** | Lead time and deploy frequency reflect CD maturity |
| **[[Continuous Integration]]** | Shorter lead time starts with fast, reliable CI |
| **[[SRE]]** | Recovery time and reliability align with error budgets and ops learning |
| **[[Incident Management]]** | Change failure rate and recovery time need sane incident flow |
| **[[Dashboarding]]** | Where teams visualize DORA trends for operators |

**When to use:** Team and org dashboards, improvement experiments, platform direction checks, and postmortem prioritization.

**When to skip as the whole story:** Executive business cases, platform ROI narratives, and product outcome reviews. Pair DORA with stakeholder-defined value metrics and narrative.

## Details

| Topic             | Notes                                                                                                                            |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **Scope**         | System-level outcomes, not individual developer output                                                                           |
| **Data sources**  | CI/CD events, deploy logs, incident records, VCS timestamps                                                                      |
| **Tooling**       | DORA Quick Check; native DORA views in some platforms; custom **[[Dashboarding]]** on **[[OpenTelemetry]]** or pipeline metadata |
| **Anti-patterns** | Gaming metrics, local optimization, comparing unlike systems, executive decks that start with four keys                          |
| **Complements**   | SPACE and flow metrics for developer experience; business KPIs for altitude                                                      |

**Definitions (practical):**

- **Lead time for changes:** elapsed time from code committed to successfully running in production.
- **Change failure rate:** percentage of production changes that result in degraded service, rollback, or hotfix.
- **Failed deployment recovery time / MTTR:** elapsed time from production failure to restored service for users.

**Collecting honestly:**

- Define "deployment" and "failure" the same way across teams before comparing.
- Split metrics by service or product line when architectures differ.
- Review quarterly against last year, not against a static "elite" label from an old report.

**References**

- [DORA](https://dora.dev/)
- [DORA Quick Check](https://dora.dev/quickcheck/)
- [2025 DORA Report](https://dora.dev/research/2025/dora-report/)
- [2024 DORA Report](https://dora.dev/research/2024/dora-report/)
- [Four Keys (Google Cloud)](https://cloud.google.com/blog/products/devops-sre/using-the-four-keys-to-measure-your-devops-performance)
