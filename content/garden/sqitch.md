---
title: Sqitch
date: '2026-07-01'
lastmod: '2026-07-01'
draft: false
keywords:
- Sqitch
params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: New
---

[Sqitch](https://sqitch.org/) is a standalone database change management tool. It runs native SQL deploy, revert, and verify scripts per engine. We **assess** it for schema delivery when teams want migrations outside ORM-owned changelogs. It orders changes through a plan file and dependency graph instead of numbered files alone.

## Blurb

> Sqitch is not tied to any framework, ORM, or platform. Rather, it is a standalone change management system with no opinions about your database engine, application framework, or development environment.

## Summary

**What it is:** A CLI and project layout for database schema evolution. Each change gets deploy, revert, and optional verify scripts in engine-native SQL (for example `psql` for **[[Postgres]]**). A `sqitch.plan` file records change names, dependencies, and integrity hashes in a Merkle-style chain.

**When to use:** Multi-engine shops, SQL-first teams, and services where **[[ORM]]** migration tools feel too coupled to application code. Good when you need explicit revert scripts and verify checks in CI before promote.

**When to skip:** Small apps with a single ORM that already ships reliable migrations. Teams that want one Java or .NET stack tool with no separate SQL workflow. Greenfield Postgres-only work where Flyway-style numbered SQL is already standard and working.

**Workflow:** `sqitch init`, `sqitch add`, edit deploy/revert/verify scripts, `sqitch deploy`, tag releases when the plan should freeze. Changes can be rewritten until tagged, which supports iterative or test-driven schema work.

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
