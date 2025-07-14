---
title: 'Go Template'
date: 2025-04-24
lastmod: 2025-04-24

# Keywords help in classifying content
keywords:
  - Go Template
  - Template
  - Templating

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: assess

    # tools, techniques, platforms, languages & frameworks
    quadrant: languages

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

If you are a {{% wl "Go" %}} programmer then Go Templates makes a lot of sense.  But {{% wl "Helm" %}}, and {{% wl "Hugo" %}} are some of the more popular tools that use it, so its usage is relatively specialized.  For this reason you really have to assess if there is any need.

<!--more-->

## Things to know

The [language](https://pkg.go.dev/text/template) is fully described in the programming documentation.  Basically, it reads text for embeds.  Anytime you want to drop to code you use `{{ ... }}`. The output of that block is then inserted in place.  Data can be accessed with `$` (main object), or `.` (current scope).  There are a relatively small set of built-ins like `range`, or `block`.

The main object (`$`) and all functions have to be registered directly in the {{% wl "go" %}} code.  Meaning that different usages have very different behaviors.  [Sprig](https://masterminds.github.io/sprig/) is a very common library of template functions that should be loaded to make the templates really useful.

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
