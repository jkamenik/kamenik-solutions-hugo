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

## Blurb

> SOPS is an editor of encrypted files that supports YAML, JSON, ENV, INI and BINARY formats and encrypts with AWS KMS, GCP KMS, Azure Key Vault, HuaweiCloud KMS, age, and PGP.

## Summary

**What it is:** Encrypts leaf values only so diffs stay reviewable. Backends include cloud KMS, age, and PGP. CNCF Sandbox; community under `getsops`. Beats rolling your own file encryption when you need committed secret shapes without a vault product.

**Rule of thumb:** No password manager → **assess** SOPS. Password manager already chosen → stay there (for **[[1Password]]**: `op inject` / `op run`).

**When to use:**

| Situation | Notes |
|-----------|--------|
| No password manager | Structured secrets in Git without inventing crypto |
| Multi-cloud KMS recipients | Same file encrypted to KMS ARNs or age keys |
| IaC / k8s config | Pair with **[[Terraform]]** vars or **[[Kubernetes]]** manifests |

**When to skip:**

- Any mature password manager already in use; prefer its CLI and inject patterns
- Platform secret stores only (Vault, cloud SM, sealed-secrets)
- Team cannot manage `.sops.yaml` and key distribution

**Trade-offs:** Excellent for PR-visible secret shape without a vendor vault. Do not stack SOPS beside a password-manager CLI for the same job. Not a full secret manager; it is an encrypted-file editor.

## Details

| Topic | Notes |
|-------|--------|
| Config | `.sops.yaml` creation rules by path regex |
| Model | Random DEK encrypts values; master keys wrap the DEK |
| Ops | Decrypt in CI with IAM/age; never commit plaintext |
| History | Started at Mozilla (2015); CNCF Sandbox (2023) |
| With a password manager | Stay in that ecosystem; e.g. **[[1Password]]** `op inject` / `op run` |

**References**

- [getsops.io docs](https://getsops.io/docs/)
- [getsops/sops on GitHub](https://github.com/getsops/sops)
- [1Password CLI](https://developer.1password.com/docs/cli/)
