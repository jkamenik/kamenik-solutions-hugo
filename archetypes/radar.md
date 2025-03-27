---
title: '{{ replace .File.ContentBaseName "-" " " | title }}'
date: {{ .Date }}
draft: true

# Tech Radar details

# adopt, trial, assess, hold
ring: adopt

# tools, tehcniques, platforms, languages & frameworks
quadrant: '{{ .File.Dir | path.Base }}'

# First time on the board?
isNew: false

# Blib direction detail: New, Moved In, Moved Out, No Change
status: "No Change"
---

Description goes here.
