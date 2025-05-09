---
title: 'YAMLScript'
date: 2024-04-09
lastmod: 2025-05-08
# Keywords help in classifying content
keywords:
  - YamlScript
  - Yaml

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

[YAMLScript](https://github.com/yaml/yamlscript) (YS) is valid YAML, however, it is not API compatible with YAML.  Therefore, even if `example.ys` can be read by a YAML interpreter the output would not contain the same objects as the parsed YS.  Currently no main stream programs use it, but we are optimistic that it might eventual replace {{% wl "Go Templates" %}} for things like {{% wl "Helm" %}}.  But until that happens you have to assess if it suits your needs.

<!--more-->

All YS files must start with `!yamlscript/v0/data`, or a SheBang (`#!`).  This will cause non-compliant parsers to fail, and instruct compliant ones on which language to use for the rest of the file.

## Example Data
```yaml
!yamlscript/v0/data

base =: 42
example: int(base)
```

will result in

```yaml
example: 43
```

## Example Program

```yaml
#!/usr/bin/env ys-0

# Print the verses to "99 Bottles of Beer"
#
# usage:
#   ys 99-bottles.ys [<count>]

defn main(number=99):
  each [n (number .. 1)]:
    say: paragraph(n)

defn paragraph(num): |
  $bottles(num) of beer on the wall,
  $bottles(num) of beer.
  Take one down, pass it around.
  $bottles(num - 1) of beer on the wall.

defn bottles(n):
  cond:
    n == 0 : 'No more bottles'
    n == 1 : '1 bottle'
    =>     : "$n bottles"
```

`main` is the entry point and all command line arguments are split as function arguments.  Builtins like `each`, `say`, `cond` take zero or more arguments and perform work given by their object definition.  User defined functions are called using `()`.

This is a functional language and thus the program and object definitions are unordered.  For example in `cond` the "=>" string indicates the default case; it is only placed last as a convention.  This also means that all conditions have to be fully evaluated before the default case can be chosen.  Not usually a issue, but something to be aware of.

In `paragraph` the `|` indicates that the next block is text.  The `$` in the block is interpolation.
