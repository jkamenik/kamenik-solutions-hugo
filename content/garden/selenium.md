---
title: Selenium
date: '2026-05-28'
lastmod: '2026-07-02'
draft: false
keywords:
- Selenium
params:
  garden:
    kind: item
    usefulness: hold
    category: tool
    movement: No Change
    subcategories:
    - test-framework
aliases:
- /radar/tools/selenium
---

[Selenium](https://www.selenium.dev/). Is the long-standing browser automation stack (WebDriver, Grid, IDE) that drives real browsers through language bindings and separate driver binaries.

## Summary

**Garden stance:** We **hold** Selenium for our estate.

**Key points:** | Topic | Notes |
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
