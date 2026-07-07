---
title: Playwright
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- Playwright
params:
  garden:
    kind: item
    usefulness: adopt
    category: tool
    movement: No Change
    subcategories:
    - test-framework
aliases:
- /radar/tools/playwright
---

[Playwright](https://playwright.dev/). Is Microsoft's end-to-end test framework for modern web apps.

## Summary

**What it is:** Node-first test runner (Python, Java, .NET ports exist) plus browser automation library, codegen, trace viewer, and UI mode for debugging.

**When to use:** default choice for web E2E on greenfield or migrated repos; cross-browser regression in **[[Continuous Integration]]** (especially **[[GitHub Actions]]**); API plus browser tests in one project; flaky-test reduction via auto-wait and trace replay.

**When to skip:** mobile-native apps (use dedicated mobile frameworks); simple smoke tests where a lightweight HTTP check suffices; legacy Cypress suites with no cross-browser requirement and no plan to consolidate.

**Key capabilities:** locators, network mocking, auth state reuse, visual comparisons, component testing (experimental), Docker images for CI.

## Details

| Topic | Notes |
|-------|--------|
| **Install** | `npm init playwright@latest` scaffolds config and sample tests |
| **Run** | `npx playwright test`; `--ui` for interactive debug |
| **CI** | Official GitHub Action; shard and retry built in |
| **Traces** | `trace: 'on-first-retry'` captures repro artifacts |

**Versus [[Selenium]]:** Playwright ships browsers and waits; Selenium needs driver management and explicit sleeps more often. Prefer Playwright for new work; migrate Selenium incrementally.

**Versus Cypress:** Playwright runs multiple tabs/contexts and all major engines; Cypress historically centered Chromium and in-browser execution. Standardize on Playwright unless a team has a strong Cypress-only constraint.

**Garden stance:** **Adopt** for web E2E in the **[[Test Pyramid]]** layer above **[[Unit Testing]]**; wire into **[[GitHub Actions]]** required checks on pull requests.

**References**

- [Playwright documentation](https://playwright.dev/docs/intro)
- [GitHub repository](https://github.com/microsoft/playwright)
