---
title: Earlybird
date: '2024-10-01'
lastmod: '2026-07-02'
draft: false
keywords:
- Earlybird
- go-earlybird
params:
  aliases:
  - go-earlybird
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
    subcategories:
    - code-scanner
aliases:
- /radar/tools/earlybird
---

[Earlybird](https://github.com/americanexpress/earlybird). (Amex, Go) scans repositories for **secrets, PII, weak crypto, and key material** in source, comments, and committed files.

## Blurb

> EarlyBird is a sensitive data detection tool capable of scanning source code repositories for clear text password violations, PII, outdated cryptography methods, key files and more. - americanexpre...

## Summary

**Garden stance:** We **assess** Earlybird for our estate.

**Key points:** | Topic | Notes |
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
