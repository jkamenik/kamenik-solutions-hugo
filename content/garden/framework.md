---
title: "Framework"
date: 2026-01-07
lastmod: 2026-06-12
draft: false

keywords:
  - Framework
  - application framework
  - web framework

params:
  aliases:
    - application framework
    - web framework
  garden:
    kind: subcategory
    parent_category: code
    subcategory_slug: framework
---

Under **[[Code]]**, **Framework** groups **opinionated application stacks** that own project shape: routing, lifecycle, dependency injection, ORM conventions, and "where code goes." You trade flexibility for speed. Prefer **[[Library]]** composition unless the framework's opinions match your product for years.

**In this subcategory:**

| Item | Rating | Use when |
|------|--------|----------|
| **[[Ruby on Rails]]** | **hold** | Maintaining legacy Rails; not default for greenfield |

**Related subcategories (do not duplicate tags):**

| Subcategory | Distinction |
|-------------|-------------|
| **[[Library]]** | You call it; it does not own the app skeleton (**[[OpenTelemetry]]**, **[[Zap]]**) |
| **[[Test Framework]]** | Exists to run/assert tests (**[[TestContainer]]**, **[[Helm Unittest]]**) |
| **[[game engine]]** | Real-time interactive runtime (player loops, not CRUD web) |
| **[[Language]]** | Syntax/spec only (**[[YAML]]**, **[[OpenAPI]]**) |

**What belongs here:**

- Web/app frameworks: Rails, Spring, Django, ASP.NET, Next.js (when rated as a **Code** dependency)
- Full-stack runtimes that dictate MVC (or similar) layout
- Items tagged `subcategories: ["[[Framework]]"]` on **[[Code]]** tools

**What does not belong here:**

- **[[Design Pattern]]** (technique-level patterns, not a product)
- **[[Declarative IaC]]** / cloud "frameworks" (Terraform modules are not app frameworks)
- **Agent Skills Framework** and similar **[[Technique]]** names (portable skill folders, not app code)
- Bare UI kits or single-purpose libs (use **[[Library]]**)
- Test runners (use **[[Test Framework]]**)

**Garden stance:**

- **Default:** small **[[Library]]** graph + boring **[[Language]]**; add a framework only when conventions clearly beat bespoke structure.
- **Hold** heavy monolith frameworks (**[[Ruby on Rails]]**) for new products unless the team and estate are already committed.
- **Assess** niche frameworks (e.g. **[[Ebitengine]]** belongs under **[[game engine]]**, not general web Framework).
- Framework upgrades are migration projects: pin versions, budget escape hatches (strangler, service extraction).

**How to tag:** `category: "[[Code]]"` and `subcategories: ["[[Framework]]"]` when the artifact is an opinionated app platform you build *inside*, not a CLI you operate (**[[Tool]]**) or infra you deploy (**[[Platform]]**).
