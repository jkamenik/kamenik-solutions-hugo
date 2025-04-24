---
title: 'Go'
date: 2024-04-09
lastmod: 2025-04-24

# Keywords help in classifying content
keywords:
  - Go
  - GoLang

params:
  # Tech Radar details
  radar:
    # adopt, trial, assess, hold
    ring: adopt

    # tools, techniques, platforms, languages & frameworks
    quadrant: languages

    # Blib direction detail: New, Moved In, Moved Out, No Change
    status: "No Change"
---

[Go](https://go.dev) is a language that google created to handle its unique scaling needs.  It turns out that designing for those needs, eliminates the performance and scale cliff that almost everyone experiences.  Since the language itself is fairly simple this has made it a boon for anywhere large scale and/or highly concurrent programming is needed.  For this reason it has become the de facto language for many DevOps tools, so if you are in that space then you should know it.

<!--more-->

> [!NOTE] GoLang
> Because "Go" is very generic "GoLang" can be used in search.

One of its core strengths is an active community of maintainers and a Special Interest Group ({{% wl "SIG" %}}) that forces a workable reference implementation of all things before they can be added to the language.  Unlike many other languages where a theoretical feature is added only to be poorly thought out, the SIG forces a working example to be implemented in a fork of the language before it is brought in.

This can make it frustrating for those familiar with other language constructs like package management, inheritance, or generics.  Go seems to move slowly and when picked the solutions don't always look like they do in other languages.  However, this is a strength of Go
