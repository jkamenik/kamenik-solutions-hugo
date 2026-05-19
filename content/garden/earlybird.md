---
title: "Earlybird"
date: 2024-10-01
lastmod: 2026-05-18
draft: false

keywords:
  - Earlybird
  - EarlyBird
  - go-earlybird

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "No Change"
    subcategories:
      - code-scanner

aliases:
  - /radar/tools/earlybird
---

[EarlyBird](https://github.com/americanexpress/earlybird) (Amex, Go) scans repositories for **secrets, PII, weak crypto, and key material** in source, comments, and committed files. We rate it **assess**: promising **[[Code Scanner]]** for **[[Shift Left]]** / **[[DevSecOps]]**, but tune `false-positives.json` and ignore rules before gating merges. Complements **[[Policy as Code]]** (IaC shape), not a replacement.

## Blurb

> EarlyBird is a sensitive data detection tool capable of scanning source code repositories for clear text password violations, PII, outdated cryptography methods, key files and more.

## Summary

**What it does:** CLI `go-earlybird` against local paths, remote Git URLs, pre-commit hooks, or a REST API. Output to console, JSON, or CSV. Maps findings to CWE classes (hardcoded credentials, cleartext storage, weak PRNG, suspicious comments, etc.).

**When to assess:**

| Fit | Notes |
|-----|--------|
| **Org-wide secret hygiene** | Batch scan many repos; export JSON for SIEM or PR comments |
| **Pre-commit / CI** | Block commits with high-confidence hits before push |
| **Beyond regex grep** | Rule packs for PII patterns, crypto smells, inclusivity scans |

**Why still assess (not trial/adopt):**

- Tuning cost: expect a false-positive budget (see pilot below).
- Overlap with **gitleaks**, **TruffleHog**, **detect-secrets**; pick one standard per org.
- Does not cover dependency CVEs (**[[Codacy]]**-class SAST) or IaC policy (**[[Conftest]]**).

**Garden stance:** run a pilot on representative repos; commit `false-positives.json` and `.ge_ignore` to Git; wire into **[[GitHub Actions]]** only after signal-to-noise is acceptable.

## Details

| Topic | Notes |
|-------|--------|
| **Install** | `build.sh` + `install.sh` (Linux/macOS) or Windows `build.bat`; config under `~/.go-earlybird` |
| **Scan** | `go-earlybird --path=...` or `--git=https://...` |
| **Ignore files** | `.ge_ignore` with `.gitignore` globs ([IGNORE.md](https://github.com/americanexpress/earlybird/blob/main/docs/IGNORE.md)) |
| **Line ignore** | Comment containing `EARLYBIRD-IGNORE` on that line |
| **False positives** | `false-positives.json`: `Codes`, `Pattern` (regex), `FileExtensions`, `Description` ([docs](https://github.com/americanexpress/earlybird/blob/main/docs/FALSEPOSITIVES.md)) |

**Example false-positive rule** (ignore rules 1, 2, 4 when pattern `abc` matches):

```json
{
  "rules": [{
    "Codes": [1, 2, 4],
    "Pattern": "abc",
    "FileExtensions": [],
    "Description": "Just because"
  }]
}
```

Rules apply when **both** `Pattern` and `FileExtensions` match (empty `FileExtensions` = all extensions). To disable a code entirely, use pattern `.*`. To skip markdown: `"FileExtensions": [".md"]`.

**Pilot snapshot (internal, 2024):** 21 false positives, 19 valid, 3 noise; re-run after rule tuning before org mandate.

**Pipeline placement:** same PR path as lint (**[[Continuous Integration]]** step 5 in garden CI model); do not rely on scanner alone without secret rotation process.

**References**

- [americanexpress/earlybird](https://github.com/americanexpress/earlybird)
- [Usage](https://github.com/americanexpress/earlybird/blob/main/docs/USAGE.md)
- [Hooks (pre-commit)](https://github.com/americanexpress/earlybird/blob/main/docs/HOOKS.md)
