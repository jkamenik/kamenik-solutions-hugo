---
title: Go Template
date: '2025-04-24'
lastmod: '2026-07-02'
draft: false
keywords:
- Go Template
params:
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: No Change
    subcategories:
    - language
---

[Go Template](https://pkg.go.dev/text/template). If you are a [[Go]] programmer then Go Templates makes a lot of sense.

## Blurb

> Package template implements data-driven templates for generating textual output.

## Summary

**Garden stance:** We **assess** Go Template for our estate.

**When to use:** Evaluate on a project when the capability clearly fits the requirement.

**When to skip:** When a simpler alternative already covers the need.

## Details

### Things to know

The [language](https://pkg.go.dev/text/template) is fully described in the programming documentation. Basically, it reads text for embeds. Anytime you want to drop to code you use `{{ ... }}`. The output of that block is then inserted in place. Data can be accessed with `$` (main object), or `.` (current scope). There are a relatively small set of built-ins like `range`, or `block`.

The main object (`$`) and all functions have to be registered directly in the [[go]] code. Meaning that different usages have very different behaviors. [Sprig](https://masterminds.github.io/sprig/) is a very common library of template functions that should be loaded to make the templates really useful.

### Example
```go
import (
 "github.com/Masterminds/sprig/v3"
 "html/template"
)

// This example illustrates that the FuncMap *must* be set before the
// templates themselves are loaded.
tpl := template.Must(
 template.New("base").Funcs(sprig.FuncMap()).ParseGlob("*.html")
)
```
`template.FuncMap` is a `map[string]any` and can be used to add any functions to the list, including internally developed ones.
