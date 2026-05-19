---
title: "Ebitengine"
date: 2023-11-29
lastmod: 2026-05-18
draft: false

keywords:
  - Ebitengine

params:
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: "No Change"
    subcategories:
      - game-engine

aliases:
  - /radar/code/ebitengine
---

[Ebitengine](https://ebitengine.org/) (pronounced "eh-bee-ten-gin"; formerly **Ebiten**) is an open-source 2D [[game engine]] for [[GoLang]]. It targets desktop and mobile from a single Go codebase with a small API surface. We rate it **assess**: strong fit if you already standardize on Go and need a lightweight 2D stack, but it is a niche choice compared to Unity, Godot, or web-first engines.

## Blurb

> Ebitengine is an open source game engine for the Go programming language. Ebitengine's simple API allows you to quickly and easily develop 2D games that can be deployed across multiple platforms.

## Summary

Ebitengine wraps rendering, input, and audio for 2D games without pulling in a heavy editor or scripting layer. You write ordinary Go, which makes it easy to share logic with servers and tools your team already ships in [[GoLang]]. The trade-off is ecosystem size: fewer tutorials, assets, and hiring signals than mainstream engines.

## Details

- **Platforms:** Windows, macOS, Linux, browsers (via WebAssembly), iOS, Android, Nintendo Switch (with license).
- **Model:** immediate-mode 2D drawing; no built-in scene editor, games are code-first.
- **Strengths:** simple API, pure Go workflow, cross-compile story, active maintainer (Hajime Hoshi).
- **Limits:** 2D only; not the right default for 3D, AAA tooling, or teams without Go experience.
- **When to trial:** prototypes, tools, or indie 2D titles where Go is already the org language.
