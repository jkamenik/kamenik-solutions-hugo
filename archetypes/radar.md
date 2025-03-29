---
title: '{{ replace .File.ContentBaseName "-" " " | title }}'
date: {{ .Date }}
lastmod: {{ .Date }}
draft: true

{{- $quad := path.Dir .Path | path.BaseName  }}

# Keywords help in classifing content
keywords:
  - radar
  - {{ $quad }}

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: adopt

    # tools, tehcniques, platforms, languages & frameworks
    quadrant: {{ $quad }}

    # explicitly state the is_new value.  Otherwise the date is used
    # is_new: false

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

Summary goes here.

<!--more-->

Additional details goes here.
