---
title: "Cypress"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - Cypress

params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: "New"
    subcategories:
      - test-framework
aliases:
  - /radar/tools/cypress
---

[Cypress](https://www.cypress.io/) is a JavaScript end-to-end and component testing framework that runs tests inside the browser with a dedicated runner UI, time-travel debugging, and network stubbing. We **hold** it for new browser E2E work because **[[Playwright]]** is our **adopt** default. Existing Cypress suites are fine to maintain until a migration pays off.

## Blurb

> Fast, easy and reliable testing for anything that runs in a browser.

## Summary

**What it is:** Open source test runner (`cypress run`, `cypress open`) plus optional Cypress Cloud for parallelization, recording, and analytics. Strong DX for front-end teams already on JavaScript.

**When to use:** brownfield repos with a large Cypress investment and no cross-browser gap; component testing workflows already wired to Cypress; teams that rely on Cypress Cloud dashboards and flake detection.

**When to skip:** greenfield web E2E (use **[[Playwright]]**); need first-class Firefox/WebKit in one project; multi-tab or multi-origin flows that fight Cypress' in-browser architecture.

**Key capabilities:** automatic waiting, screenshot/video capture, `cy.intercept` network control, component testing for React/Vue/Angular, GitHub Action and **[[GitHub Actions]]** CI recipes.


## Details

| Topic | Notes |
|-------|--------|
| **Install** | `npm install cypress --save-dev`; `npx cypress open` for interactive runner |
| **Run** | `npx cypress run` headless in CI |
| **Config** | `cypress.config.js` or `.ts`; `baseUrl`, viewport, retries |
| **Cloud** | Optional paid service for parallel runs and test replay |

**Versus Playwright:** Cypress historically optimized Chromium-first in-browser runs; Playwright targets all major engines with a single API and ships tracing for CI. Prefer Playwright for new **[[Test Pyramid]]** E2E layers.

**Migration path:** run both frameworks in parallel on a slice of critical paths; port specs file-by-file; drop Cypress when Playwright coverage and CI time match or beat the old suite.

**References**

- [Cypress documentation](https://docs.cypress.io/)
- [GitHub repository](https://github.com/cypress-io/cypress)
