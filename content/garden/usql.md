---
title: usql
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- usql
params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: No Change
aliases:
- /radar/tools/usql
---

[usql](https://github.com/xo/usql). Is a single binary that speaks the `psql`-style command line to many SQL and NoSQL databases.

## Summary

**What it is:** Go-based CLI with `\` meta-commands, variables, syntax highlighting, context completion, and optional copy between connections.

**When to use:** daily ad hoc queries across heterogeneous data stores; jump hosts or bastion workflows where installing every native client is painful; scripting with `-c` and `-f` like `psql`.

**When to skip:** deep admin features tied to one vendor (e.g. `\copy` parity gaps); GUI-first analysts; teams standardized on a single cloud console.

**Covers:** relational engines (Postgres, MySQL, SQL Server, SQLite, Oracle) plus Cassandra, ClickHouse, MongoDB, Redis, and more (see upstream database support table).

## Details

| Feature | Notes |
|---------|--------|
| **Install** | `brew install usql` or release binaries from GitHub |
| **Connect** | `usql pg://...`, `usql mysql://...`, DSN-style URLs |
| **Copy** | `\copy` between databases (cross-engine data moves) |
| **Output** | CSV, JSON, vertical, HTML table formats |

**Practices:** store credentials in env vars or `.usqlrc`, not on the command line in shell history; test `\d` / describe behavior per engine before relying on it in runbooks.

**References**

- [usql README](https://github.com/xo/usql)
- [Database support matrix](https://github.com/xo/usql#database-support)
