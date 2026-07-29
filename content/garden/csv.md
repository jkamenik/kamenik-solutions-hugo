---
title: CSV
date: '2026-07-23'
lastmod: '2026-07-23'
draft: false
keywords:
- CSV
- Comma-Separated Values
- text/csv
params:
  aliases:
  - Comma-Separated Values
  - text/csv
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: New
---

[CSV](https://www.rfc-editor.org/rfc/rfc4180) (Comma-Separated Values) is the common text format for exchanging tabular data between spreadsheets and systems. We **adopt** it for small-to-medium interchange where humans may open the file.

## Blurb

> This RFC documents the format used for Comma-Separated Values (CSV) files and registers the associated MIME type "text/csv".

## Summary

**What it is:** Line-oriented records with comma-separated fields; optional header row; quoting rules for commas, quotes, and newlines. Documented in RFC 4180 as MIME type `text/csv`. Implementations still vary; be liberal in what you accept.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Human-editable dumps | Spreadsheet round-trips, one-off exports |
| Small tables | Config lists, seed data, report attachments |
| Lowest common denominator | Partners who cannot take Parquet |

**When to skip:**

- Large analytic tables (**[[Parquet]]**)
- Nested or typed structures (**[[JSON]]**, Arrow)
- Strict schemas and evolution (table formats / databases)

**Trade-offs:** Universal and simple; ambiguous dialects, weak typing, and poor compression at scale.

## Details

### Practical Notes

| Topic | Notes |
|-------|--------|
| Spec | RFC 4180 (informational); RFC 7111 updates |
| MIME | `text/csv` with optional `header` parameter |
| Engines | **[[DuckDB]]** and most warehouses read CSV directly |

### References

- [RFC 4180](https://www.rfc-editor.org/rfc/rfc4180)
