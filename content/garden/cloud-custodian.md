---
title: Cloud Custodian
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- Cloud Custodian
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - code-scanner
aliases:
- /radar/tools/cloud-custodian
---

[Cloud Custodian](https://cloudcustodian.io/). We **assess** it under **[[Tool]]** in the garden.

## Summary

**What it is:** Policy-as-data YAML plus a Python runtime, CLI (`custodian`), and optional serverless modes (Cloud Custodian Org for multi-account).

**When to use:** replace ad hoc cleanup scripts; enforce tagging, off-hours shutdown, encryption checks, or unused resource removal across accounts; central metrics and reporting on policy runs.

**When to skip:** small single-account shops covered by native Config or Policy; teams already committed to OPA/Rego (**[[Conftest]]**, Gatekeeper) for the same rules; no ops capacity to tune false positives.

**Pairs with:** **[[Terraform]]** provisioning plus Custodian enforcement in live accounts; **[[Shift Left]]** IaC scans on PRs, Custodian on deployed resources.

## Details

| Topic | Notes |
|-------|--------|
| **Policy shape** | `policies:` list with `resource`, `filters`, `actions` |
| **Modes** | pull (cron), cloudtrail/event-driven, periodic |
| **Extensibility** | mailer, c7n-org for org-wide rollout |

**Practices:** start with notify-only actions; dry-run in staging accounts; version policies in **[[git]]** like application code.

**References**

- [Cloud Custodian documentation](https://cloudcustodian.io/docs/)
- [GitHub repository](https://github.com/cloud-custodian/cloud-custodian)
