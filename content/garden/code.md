---
title: "Code"
date: 2024-03-27
lastmod: 2026-05-21
draft: false

keywords:
  - Code

params:
  garden:
    kind: category
    category: code
---

**Code** is the garden quadrant for **dependencies and notations in the repo**: languages and DSLs, libraries, frameworks, and test harnesses you import or reference. It is not where we classify things you **operate** (**[[Tool]]**: IDEs, CI runners, scanners) or **deploy on** (**[[Platform]]**: clouds, orchestrators), nor **how you work** (**[[Technique]]**: patterns, practices, delivery methods).

**Subcategories (how to tag):**

| Subcategory | Tag when… | Examples |
|-------------|-----------|----------|
| **[[Language]]** | The artifact is a syntax, spec, or data language | **[[YAML]]**, **[[JSON]]**, **[[HCL]]**, **[[OpenAPI]]**, **[[Protobuf]]** |
| **[[Library]]** | Reusable package/API you link; no app skeleton | **[[Zap]]**, **[[tree-sitter]]**, **[[OpenTelemetry]]** |
| **[[Framework]]** | Opinionated app stack (routing, lifecycle, layout) | **[[Ruby on Rails]]** |
| **[[Test Framework]]** | Primary job is running/writing automated tests | **[[Helm Unittest]]**, **[[TestContainer]]**, **[[Container Structure Test]]** |
| **[[game engine]]** | Real-time interactive runtime for games | **[[Ebitengine]]** |

**Direct items (no subcategory):** general-purpose languages and misc code artifacts that do not fit a subcategory yet, e.g. **[[GoLang]]**, **[[Python]]**, **[[Ruby]]**, **[[Dev Container]]** specs. Prefer a subcategory when one clearly applies.

**Garden stance at this level:** favor small, composable **[[Library]]** dependencies over heavy **[[Framework]]** lock-in unless the framework pays for itself; keep **[[Language]]** choices boring and portable (**[[YAML]]**, **[[JSON]]** adopt); implement testing via **[[Test Framework]]** items tied to **[[Unit Testing]]** / **[[Integration Testing]]** techniques, not ad-hoc scripts.

Publish subcategory pages (**[[Language]]**, **[[Library]]**, etc.) so Hugo taxonomy and the public garden can list children under **Code**.
