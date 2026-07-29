---
title: Sqitch
date: '2026-07-01'
lastmod: '2026-07-29'
draft: false
keywords:
- Sqitch
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: No Change
---

[Sqitch](https://sqitch.org/). Is a standalone database change management tool.

## Summary

**Garden stance:** We **assess** Sqitch for our estate.

**Key points:**

| Topic | Notes |
|-------|--------|
| **Engines** | Postgres, SQLite, MySQL, Oracle, Firebird, Vertica, Exasol, Snowflake, ODBC (feature flags at build time) |
| **Layout** | `sqitch.plan`, `deploy/`, `revert/`, `verify/` directories per project |
| **Config** | `sqitch.conf` at project, user, or system scope (Git-like layering) |
| **CI** | Run `sqitch deploy` and `sqitch verify` against ephemeral or staging targets |

**Practices:** Keep DDL and DML in separate changes when verify tests need an empty schema. Declare cross-project dependencies when shared libraries ship their own plans. Tag before release so deployed hashes lock and scripts stop being editable.

**References**

- [Sqitch documentation](https://sqitch.org/docs/manual/sqitch/)
- [About Sqitch](https://sqitch.org/about/)
- [Sqitch tutorial](https://sqitch.org/docs/manual/sqitchtutorial/)

## Details

| Topic | Notes |
|-------|--------|
| **Engines** | Postgres, SQLite, MySQL, Oracle, Firebird, Vertica, Exasol, Snowflake, ODBC (feature flags at build time) |
| **Layout** | `sqitch.plan`, `deploy/`, `revert/`, `verify/` directories per project |
| **Config** | `sqitch.conf` at project, user, or system scope (Git-like layering) |
| **CI** | Run `sqitch deploy` and `sqitch verify` against ephemeral or staging targets |

**Practices:** Keep DDL and DML in separate changes when verify tests need an empty schema. Declare cross-project dependencies when shared libraries ship their own plans. Tag before release so deployed hashes lock and scripts stop being editable.

**References**

- [Sqitch documentation](https://sqitch.org/docs/manual/sqitch/)
- [About Sqitch](https://sqitch.org/about/)
- [Sqitch tutorial](https://sqitch.org/docs/manual/sqitchtutorial/)
