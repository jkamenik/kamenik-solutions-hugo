---
title: Zap
date: '2025-12-08'
lastmod: '2026-07-29'
draft: false
keywords:
- Zap
- uber-go/zap
params:
  aliases:
  - uber-go/zap
  garden:
    kind: item
    usefulness: trial
    category: code
    movement: No Change
    subcategories:
    - library
---

[Zap](https://github.com/uber-go/zap) is Uber's structured, leveled logging library for **[[GoLang]]**. We **trial** it when a service needs low-allocation JSON logs; not to be confused with OWASP [[Zed Attack Proxy (Zap)]].

## Blurb

> Blazing fast, structured, leveled logging in Go.

## Summary

**What it is:** Strongly typed fields (`zap.String`, `zap.Int`, …) instead of printf-style formatting. Production configs favor JSON; development often uses console encoding.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Existing Zap estate | Stay consistent with Uber-style instrumentation |
| Benchmark-sensitive services | Low allocation vs heavier facades |
| Team standard already Zap | Config via `zap.Config` or `zap.NewProduction()` |

**When to skip:**

- Greenfield modern Go: prototype with stdlib `log/slog` first
- Mixing multiple logging facades in one binary
- Need only trivial stderr prints

**Trade-offs:** Mature and fast. Another dependency and API to learn versus `slog`. Prefer one facade per service.

## Details

| Topic | Notes |
|-------|--------|
| Category | **[[Code]]** / **[[Library]]** (imported, not a standalone agent) |
| Ops | JSON lines into Loki, ELK, or CloudWatch; set level and sampling per env |
| Disambiguation | OWASP **[[Zed Attack Proxy (Zap)]]** is unrelated DAST tooling |

**References**

- [uber-go/zap](https://github.com/uber-go/zap)
