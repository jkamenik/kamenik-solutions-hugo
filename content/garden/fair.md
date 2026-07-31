---
title: FAIR
date: '2026-07-30'
lastmod: '2026-07-30'
draft: false
keywords:
- FAIR
- Factor Analysis of Information Risk
- Open FAIR
- FAIR Risk
params:
  aliases:
  - Factor Analysis of Information Risk
  - Open FAIR
  - FAIR Risk
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: New
---

[FAIR](https://www.fairinstitute.org/what-is-fair) (Factor Analysis of Information Risk) is a quantitative model for expressing cyber and operational risk in financial terms. We **assess** it when High/Medium/Low scores are not enough for control or budget decisions.

## Blurb

> Factor Analysis of Information Risk (FAIR™) is the only international standard quantitative model for information security and operational risk.

## Summary

**When to use:** You need comparable loss exposure for a scoped scenario (asset + threat + effect). Stakeholders want dollars and likelihood, not color charts. You are choosing among controls by expected loss reduction vs cost.

**When to skip:** You only need a compliance checklist, not a decision. You cannot scope a scenario or calibrate estimates. Broad "all ransomware" scopes usually produce noise.

| Topic | Notes |
| ----- | ----- |
| **Output** | Loss exceedance curves, average annual loss, percentiles (e.g. P90) |
| **Inputs** | Calibrated ranges for frequency and magnitude factors |
| **Complements** | NIST CSF, ISO 27001, and similar frameworks define programs. FAIR quantifies loss exposure on top. |
| **Pairs with** | **[[DevSecOps]]** for measurable security work in delivery. **[[Kerckhoffs's principle]]** for control design that does not rely on obscurity. |

**Core model:**

- **Loss Event Frequency (LEF):** how often a loss materializes
- **Loss Magnitude (LM):** how costly each event is (primary + secondary loss)

Risk for a scenario is the distribution from combining LEF and LM (often via Monte Carlo).

## Details

### Factor Tree (Practical)

**Loss Event Frequency** decomposes into threat event frequency and vulnerability (chance the threat succeeds). Vulnerability further depends on threat capability vs control resistance.

**Loss Magnitude** splits into:

| Loss type | Examples |
| --------- | -------- |
| **Primary** | Response, replacement, downtime, direct remediation |
| **Secondary** | Fines, lawsuits, reputation, customer churn, credit monitoring |

### Workflow

1. Scope one scenario tightly (asset, threat community, effect).
2. Estimate each factor as a range (min / most likely / max), calibrated with data or experts.
3. Simulate to get a loss distribution and decision metrics.
4. Compare controls by how they change frequency, magnitude, or both.

### Standards and Ecosystem

The Open Group publishes Open FAIR as O-RT (Risk Taxonomy) and O-RA (Risk Analysis). The FAIR Institute maintains community education and the FAIR Cyber Risk Management Framework. Commercial engines exist; the model itself is a methodology, not a single product.

### Common Pitfalls

- Treating ordinal scores (1-5) as if they were ratio-scale measurements
- Mixing unlike scenarios into one "enterprise cyber risk" number
- Skipping calibration; then the simulation only amplifies bad guesses
- Confusing FAIR with program frameworks that do not prescribe how to compute risk

### References

- [What is FAIR? (FAIR Institute)](https://www.fairinstitute.org/what-is-fair)
- [FAIR Risk Management](https://www.fairinstitute.org/fair-risk-management)
- [The Open Group - Open FAIR](https://www.opengroup.org/forum/security/riskmanagement)
