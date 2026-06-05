---
{{- $title := replace .File.ContentBaseName "-" " " | title }}
title: '{{ $title }}'
date: {{ .Date | time.Format "2006-01-02" }}
lastmod: {{ .Date | time.Format "2006-01-02" }}
draft: true

keywords:
  - {{ $title }}

params:
  aliases: []
  garden:
    usefulness: assess
    category: tool
    movement: "New"
---

<!-- TODO: Add a summary -->

<!--more-->

<!-- TODO: Add additional info -->
