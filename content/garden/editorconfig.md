---
title: "EditorConfig"
date: 2024-10-01
lastmod: 2026-06-12
draft: false

keywords:
  - EditorConfig

params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: "No Change"
aliases:
  - /radar/tools/editorconfig
---

[EditorConfig](https://editorconfig.org/) is a repo-root **`.editorconfig`** file plus editor plugins that apply shared whitespace, encoding, and newline rules before language formatters or linters run. We **adopt** it as the bottom layer of **[[Code Linting]]**: cheap consistency across VS Code, Cursor, JetBrains, and vim without debating tabs in every PR.

## Blurb

> EditorConfig helps maintain consistent coding styles for multiple developers working on the same project across various editors and IDEs.

## Summary

**What it fixes:** UTF-8 vs Latin-1 surprises, CRLF vs LF churn, trailing whitespace noise, and "my editor used 2 spaces, yours used 4" diffs. It does **not** replace ESLint, Prettier, golangci-lint, or **[[Super-Linter]]**; it sets the **baseline** those tools assume.

**Why adopt:**

| Benefit | Detail |
|---------|--------|
| **VCS-friendly** | Small text file; merges are rare |
| **Editor-agnostic** | Plugins for most IDEs; native support in some |
| **Shift left** | Applies on save locally, same rules in **[[Dev Container]]** if the plugin is installed |
| **Pairs with CI** | Linters still enforce logic; EditorConfig reduces formatting-only failures |

**Rules of thumb:**

- Commit `.editorconfig` at repo root with `root = true`.
- Use globs per language (`[*.{js,ts}]`, `[*.go]`, `[*.md]`).
- Do not duplicate every Prettier option; let formatters own language semantics.
- Document team choices in **[[Code Linting]]** standards, not in wiki-only tables.

## Details

**Example baseline** (team defaults; adjust per repo):

```ini
root = true

[*]
indent_style = space
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = false

[*.md]
indent_size = 4
trim_trailing_whitespace = true
insert_final_newline = true
```

| Property | Typical use |
|----------|-------------|
| `indent_style` / `indent_size` | Spaces vs tabs per language |
| `end_of_line` | `lf` for cross-platform repos |
| `charset` | `utf-8` default |
| `trim_trailing_whitespace` | Cleaner diffs (often off for `.md` if needed) |
| `insert_final_newline` | POSIX text files; may differ for `*` vs `*.md` |

**Monorepos:** nested `.editorconfig` in packages is allowed; closest match wins. Prefer one root file unless a subtree truly needs different EOL rules.

**CI:** optional `editorconfig-checker` in **[[GitHub Actions]]** if editors without plugins are common; most teams rely on linters plus local plugins.

**Not the same as:** `.gitattributes` (Git checkout normalization); Prettier config; **[[Policy as Code]]**.

**References**

- [EditorConfig](https://editorconfig.org/)
- [Formal specification](https://spec.editorconfig.org/)
