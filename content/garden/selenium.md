---
title: "Selenium"
date: 2026-05-28
lastmod: 2026-06-22
draft: false

keywords:
  - Selenium

params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: "New"
    subcategories:
      - test-framework
aliases:
  - /radar/tools/selenium
---

[Selenium](https://www.selenium.dev/) is the long-standing browser automation stack (WebDriver, Grid, IDE) that drives real browsers through language bindings and separate driver binaries. We **hold** it for new browser E2E work because **[[Playwright]]** is our **adopt** default. Keep existing Selenium suites until migration pays off; do not start greenfield E2E on Selenium.

## Blurb

> Selenium automates browsers. That's it!

## Summary

**What it is:** Open source WebDriver protocol implementation with client libraries (Java, Python, C#, JavaScript, Ruby, and others), optional Selenium Grid for distributed runs, and Selenium IDE for record-and-playback prototyping.

**When to use:** brownfield repos with large Selenium investments; enterprises standardized on WebDriver across many languages; Grid topologies already tuned for parallel browser farms.

**When to skip:** greenfield web E2E (use **[[Playwright]]**); teams that want bundled browsers, auto-wait, and tracing without driver version matrices; JavaScript-only shops evaluating **[[Cypress]]** (also **hold** for new work).

**Key capabilities:** cross-browser WebDriver sessions, Grid scaling, language-agnostic API, wide CI cookbook coverage.


## Details

| Topic | Notes |
|-------|--------|
| **WebDriver** | Language binding talks to a browser-specific driver (ChromeDriver, geckodriver, etc.) |
| **Grid** | Hub/node layout for parallel browsers; ops overhead versus Playwright sharding |
| **IDE** | Quick script capture; export to code; not a substitute for maintained test suites |
| **CI** | Works in **[[GitHub Actions]]** and other **[[Continuous Integration]]** runners with driver install steps |

**Versus Playwright:** Selenium separates browser, driver, and binding versions. Playwright bundles browsers, auto-waits, and trace artifacts. Prefer Playwright for new **[[Test Pyramid]]** E2E layers.

**Versus Cypress:** Cypress targets JavaScript in-browser runs with a dedicated runner. Selenium is language-neutral and WebDriver-native. Both are **hold** for net-new work here.

**Migration path:** identify critical paths; port specs to Playwright with parallel runs; retire Grid nodes when Playwright parallelism and flake metrics match or beat the old stack.

**References**

- [Selenium documentation](https://www.selenium.dev/documentation/)
- [GitHub organization](https://github.com/SeleniumHQ)
