---
title: EditorConfig
date: '2024-10-01'
lastmod: '2026-07-02'
draft: false
keywords:
- EditorConfig
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
aliases:
- /radar/tools/editorconfig
---

[EditorConfig](https://editorconfig.org/). Is a repo-root **`.editorconfig`** file plus editor plugins that apply shared whitespace, encoding, and newline rules before language formatters or linters run.

## Blurb

> EditorConfig is a file format and collection of text editor plugins for maintaining consistent coding styles between different editors and IDEs.

## Summary

**Garden stance:** We **adopt** EditorConfig for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

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
