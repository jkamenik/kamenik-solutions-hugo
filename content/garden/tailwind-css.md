---
title: "Tailwind CSS"
date: 2026-05-27
lastmod: 2026-05-27
draft: false

keywords:
  - Tailwind CSS

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - code

aliases:
  - /radar/tools/tailwind-css
---

[Tailwind CSS](https://tailwindcss.com/) is a utility-first CSS framework. You compose layouts from small classes in markup instead of hand-writing large stylesheets. We **assess** it for internal web UIs and marketing sites; backend-heavy work does not require it.

## Blurb

> Tailwind CSS is a utility-first CSS framework for rapidly building custom user interfaces.

## Summary

**When to use:** React/Vue/Next sites where designers want fast iteration; teams comfortable with class-heavy HTML and a build step (PostCSS).

**When to skip:** no customer-facing CSS; design system already locked on another stack; email templates and PDFs that cannot use utility pipelines.

**Pairs with:** component libraries (Headless UI, shadcn); design tokens via `tailwind.config`; purge/content paths in CI for small bundles.
