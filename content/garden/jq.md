---
title: jq
date: '2023-07-23'
lastmod: '2026-07-02'
draft: false
keywords:
- jq
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
aliases:
- /radar/tools/jq
---

[jq](https://jqlang.org/). Is a lightweight command-line JSON processor: the default tool for slicing, filtering, mapping, and transforming JSON in shell pipelines, CI, and ad hoc debugging.

## Summary

jq (`jqlang/jq`) is a portable C binary with zero runtime dependencies: filter expressions, pretty-printing, arithmetic, objects/arrays, and streaming for large inputs. The project revived under the [jqlang](https://github.com/jqlang) org (1.7+ after a long hiatus); current stable is **1.8.x** per [jqlang.org](https://jqlang.org/).

Use in one-liners (`curl … | jq '.items[]'`), policy checks (parse `terraform show -json`), and log wrangling. Prefer **[[yq]]** when you need YAML round-trips with comments preserved; prefer `jq` when JSON is the native format or you want the de facto query dialect.

## Details

- **Install:** [download](https://jqlang.org/download/) (static binary), Homebrew (`jq`), apt/dnf packages; verify with `jq --version`.
- **Docs:** [tutorial](https://jqlang.org/tutorial/), [manual](https://jqlang.org/manual/).
- **License:** MIT (upstream).
- **CI / ops:** pipe API and tool JSON output through `jq` for assertions and field extraction; combine with `curl`, `gh api`, `kubectl … -o json`.
- **Fit:** [[Tool]]: CLI JSON query/processor.
- **Contrast:** [[yq]] for YAML-first workflows; language-native JSON APIs when a shell one-liner is not enough.
