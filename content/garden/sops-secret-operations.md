---
title: SOPS (Secret OPerationS)
date: '2024-10-01'
lastmod: '2026-07-29'
draft: false
keywords:
- SOPS (Secret OPerationS)
- SOPS
- Secrets OPerationS
params:
  aliases:
  - SOPS
  - Secrets OPerationS
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[SOPS](https://getsops.io/) encrypts structured secret files (YAML, JSON, ENV, INI, binary) while leaving keys readable for review. We **assess** it when you have no password manager and need Git-friendly secrets under **[[GitOps]]** or IaC. If you already have a vault, stay in that ecosystem.
