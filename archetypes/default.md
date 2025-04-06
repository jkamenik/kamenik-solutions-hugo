---
{{- $title := replace .File.ContentBaseName "-" " " | title }}
title: '{{ $title }}'
date: {{ .Date | time.Format "2006-01-02" }}
draft: true

# Keywords help in classifying content
keywords:
  - {{ $title }}
---

Summary

<!--more-->

Full content
