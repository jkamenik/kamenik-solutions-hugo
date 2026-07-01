---
title: Model-View-Controller (MVC)
date: '2025-12-12'
lastmod: '2026-07-01'
draft: false
keywords:
- Model-View-Controller (MVC)
- Model View Controller
params:
  aliases:
  - Model View Controller
  garden:
    kind: item
    usefulness: assess
    category: technique
    movement: No Change
    subcategories:
    - software-architecture
    - design-pattern
---

[Model-view-controller (MVC)](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) splits UI applications into model (data and rules), view (presentation), and controller (input and flow). We **assess** it per stack because frameworks often label layers "MVC" while shipping different boundaries. It remains a common web pattern, not a universal architecture default.

## Blurb

> Model-view-controller is a software design pattern commonly used for developing user interfaces that divides the related program logic into three interconnected elements.

## Summary

**What it is:** separation of concerns for interactive apps. The model holds domain state. The view renders state. The controller translates user actions into model updates and view refreshes.

**When it fits:** server-rendered web apps, desktop UI toolkits, and frameworks that enforce clear template vs logic splits (Rails, Django, ASP.NET MVC-style stacks).

**When to reassess:** SPAs where the "view" is a component tree and "controller" logic bleeds into front-end state managers; micro-frontends; or backends that are pure APIs with no server-side view. In those cases, explicit **[[Software Architecture]]** layers beat literal MVC folder names.

**Garden link:** **[[ORM]]** often backs the model layer in database-backed web apps. Keep persistence mapping out of views and thin controllers.

## Details

| Layer | Responsibility | Common mistake |
|-------|----------------|----------------|
| **Model** | Domain state, validation, persistence rules | Fat models that know HTTP or UI details |
| **View** | Presentation and formatting | Business logic embedded in templates |
| **Controller** | Request routing, orchestration | God controllers that skip the model |

### Variants and Neighbors

- **MVP / MVVM:** common in desktop and mobile UI stacks; same separation goal, different binding direction.
- **API-only backends:** often drop the view; do not force MVC naming when the system is REST resources plus services.
