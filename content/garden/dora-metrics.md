---
title: DORA Metrics
date: '2026-06-22'
lastmod: '2026-07-02'
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

[DORA Metrics](https://dora.dev/). Are the DevOps Research and Assessment team's validated measures of software delivery and operational (SDO) performance.

## Blurb

> DORA is a long running research program that seeks to understand the capabilities that drive software delivery and operations performance. DORA helps teams apply those capabilities, leading to better organizational performance.

## Summary

**Garden stance:** We **adopt** DORA Metrics for our estate.

**Key points:** | Topic             | Notes                                                                                                                            |
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
