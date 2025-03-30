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

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

Summary goes here.

<!--more-->

Additional details goes here.
