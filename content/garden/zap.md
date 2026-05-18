---
title: "Zap"
date: 2025-12-08
lastmod: 2026-05-17
draft: false

keywords:
  - Zap
  - uber-go/zap

params:
  garden:
    kind: item
    usefulness: trial
    category: code
    movement: "No Change"
    subcategories:
      - library

aliases:
---

[Zap](https://github.com/uber-go/zap) (Uber) is a structured, leveled logging library for [[GoLang]]—not to be confused with the [[Zed Attack Proxy (Zap)]] security scanner. We rate it **trial** for new Go services: it remains a high-performance default when you want JSON logs and explicit fields, though Go 1.21+ `log/slog` in the standard library is now the first choice to evaluate before adding a third-party logger.

## Blurb

> Blazing fast, structured, leveled logging in Go.

## Summary

Zap optimizes for low allocation and clear leveled output (`Debug`, `Info`, `Warn`, `Error`) with strongly typed fields (`zap.String`, `zap.Int`, …) instead of printf-style formatting. Production configs favor JSON encoders; development configs often use console encoding with color. The API splits a terse `zap.NewProduction()` path from a configurable `zap.Config` for teams that need tuning.

If you are greenfield on modern Go, prototype with `log/slog` first—stdlib support, handler ecosystem, and attr-style fields cover many of the same goals. Reach for Zap when benchmarks, existing Uber-style instrumentation, or team standards already assume it.

## Details

- **Category:** [[Code]] / [[Library]]—imported into your binary, not a standalone agent.
- **Strengths:** speed, structured fields, sane defaults for production JSON logging, mature usage across the Go ecosystem.
- **Trade-offs:** another dependency to version; learning curve vs `slog`; avoid mixing multiple logging facades in one service.
- **Operations:** pair with centralized log aggregation (JSON lines → Loki/ELK/CloudWatch); define level and sampling policy per environment.
- **Disambiguation:** OWASP [[Zed Attack Proxy (Zap)]] is unrelated tooling for DAST.
