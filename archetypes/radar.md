---
{{- $title := replace .File.ContentBaseName "-" " " | title }}
title: '{{ $title }}'
date: {{ .Date }}
lastmod: {{ .Date }}
draft: true

{{- $quad := path.Dir .Path | path.BaseName  }}

# Keywords help in classifing content
keywords:
  - {{ $title }}

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: assess

    # tools, techniques, platforms, languages & frameworks
    quadrant: {{ $quad }}

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

Summary goes here.

<!--more-->

Additional details goes here.
