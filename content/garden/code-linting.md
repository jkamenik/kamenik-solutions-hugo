---
title: "Code Linting"
date: 2024-10-01
lastmod: 2026-05-18
draft: false

keywords:
  - Code Linting

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "No Change"

aliases:
  - /radar/techniques/code-linting
---

[Linting](https://en.wikipedia.org/wiki/Lint_(software)) is automated static checking of source for style, correctness, and common bug classes before merge. We **adopt** it as a **[[Technique]]**: pick team standards once, encode them in config, and make failures block **[[Pull Request]]**s so review debates opinions instead of repeating the same nits.

## Blurb

> In computer programming, lint or linter is any tool that flags suspicious constructs, likely programming errors, bugs, stylistic errors, and suspicious constructs.

## Summary

**Why adopt:** stops endless formatting and "you missed a semicolon" threads; catches whole classes of defects cheaply; pairs with **[[Shift Left]]** and **[[DevSecOps]]** when security linters run on the same PR path.

**Layers (typical stack):**

| Layer | Purpose | Garden examples |
|-------|---------|-----------------|
| Editor baseline | Consistent encoding, EOL, indent | **[[EditorConfig]]** (**adopt** as **[[Tool]]**) |
| Language linters | ESLint, golangci-lint, RuboCop, etc. | Run locally and in CI |
| CI bundle | One job, many linters | **[[Super-Linter]]** in **[[GitHub Actions]]** |
| Org dashboard | Trends, policy across repos | **[[Codacy]]** (**assess**), optional |

**Rules of thumb:**

- Config lives **in the repo** (`.editorconfig`, `eslint.config.js`, `.golangci.yml`); version with code.
- **Required checks** on `main`: a green linter run is not optional.
- Fix or suppress with intent; do not disable rules globally because one legacy folder whines.
- Linters complement **[[Code Review]]**; they do not replace human judgment on design.

**Not the same as:** **[[Code Scanner]]** products (vendor SKUs), **[[Policy as Code]]** for Terraform/K8s (**[[Conftest]]**), or **[[Unit Testing]]** (behavior vs style/static rules).

## Details

| Topic | Notes |
|-------|--------|
| **Local** | `make lint` or pre-commit hooks so devs see failures before push |
| **CI** | Same command as local; no "works on my machine" drift |
| **PR** | Report status to the PR; see **[[Pull Request]]** |
| **Monorepo** | Path filters or per-package configs to keep runtime sane |
| **AI-generated code** | Lint gates matter more, not less; tighten before merge |

**When to add Codacy:** many repos and languages and leaders need a single quality scorecard; otherwise **[[Super-Linter]]** plus native linters is enough.
