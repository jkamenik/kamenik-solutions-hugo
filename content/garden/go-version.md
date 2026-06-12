---
title: "go-version"
date: 2026-05-28
lastmod: 2026-06-12
draft: false

keywords:
  - go-version

params:
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: "New"
    subcategories:
      - library
aliases:
  - /radar/languages/go-version
---

[go-version](https://github.com/hashicorp/go-version) is a **[[GoLang]]** library from **[[HashiCorp]]** for parsing, comparing, and constraining [SemVer](https://semver.org/) strings. We **assess** it when a tool or operator needs version ranges (`>= 1.2, < 2.0`), prerelease ordering, or constraint checks in Go code.

## Blurb

> go-version is a library for parsing versions and version constraints, and verifying versions against a set of constraints.

## Summary

**What it does:** Parses SemVer (including prerelease and metadata), compares versions, sorts collections, and evaluates constraint expressions (`=`, `!=`, `>`, `>=`, `<`, `<=`, pessimistic `~>`).

**When to use:** Go CLI or operator that must gate upgrades, pick compatible chart or module versions, or validate user input before install.

**When to skip:** pure string equality is enough; you already depend on a larger framework that ships its own semver helper; non-SemVer version schemes (date-based, custom).

**Typical call sites:** Terraform providers, Helm-related tooling, internal release automation written in Go.

## Details

| API surface | Notes |
|-------------|--------|
| `version.NewVersion` | Parse a single version string |
| `version.NewConstraint` | Parse constraint sets (`">= 1.0, < 2.0"`) |
| `Constraints.Check` | Test whether a version satisfies constraints |
| `WithPrefix` | Strip custom prefixes (e.g. `v1.2.3`) before parse |

**Practices:** reject non-SemVer input at the boundary; log the normalized form you compared; pin the module in `go.mod` like any other library dependency.

**References**

- [go-version on pkg.go.dev](https://pkg.go.dev/github.com/hashicorp/go-version)
- [SemVer spec](https://semver.org/)
