---
{{- $title := replace .File.ContentBaseName "-" " " | title }}
title: '{{ $title }}'
date: {{ .Date | time.Format "2006-01-02" }}
lastmod: {{ .Date | time.Format "2006-01-02" }}
draft: true

{{- $quad := path.Dir .Path | path.BaseName  }}

# Keywords help in classifying content
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

<!-- TODO: Add a Summary -->

<!--more-->

<!-- TODO: Add additional info -->
