---
title: "Integration Testing"
date: 2026-06-12
lastmod: 2026-06-12
draft: false

keywords:
  - Integration Testing

params:
  garden:
    kind: item
    usefulness: adopt
    category: technique
    movement: "New"
---

[Integration testing](https://en.wikipedia.org/wiki/Integration_testing) verifies that modules, services, and infrastructure boundaries work together correctly. It sits above **[[Unit Testing]]** on the **[[Test Pyramid]]** and runs in **[[Continuous Integration]]** before release. We **adopt** integration tests for any system with external IO, APIs, or shared persistence.

## Blurb

> Integration testing is the phase in software testing in which individual software modules are combined and tested as a group.

## Summary

**What it is:** Tests that exercise real collaborators: databases, queues, HTTP APIs, filesystems, or containers, often slower and fewer than unit tests.

**When to use:** Service boundaries, repository layers, Terraform modules with live providers (carefully), and CI smoke paths after build.

**When to skip:** Pure logic with no IO (keep **[[Unit Testing]]**). Full production E2E suites that belong in staged environments only.

**Practices:** Prefer **[[TestContainer]]** or ephemeral dependencies over shared staging DBs; keep tests deterministic; tag slow suites separately in CI.

## Details

| Layer | Garden tools |
|-------|----------------|
| API / browser | **[[Playwright]]**, **[[Cypress]]**, **[[Selenium]]** |
| Containers | **[[TestContainer]]**, **[[Container Structure Test]]** |
| Policy / config | **[[Conftest]]**, **[[Helm Unittest]]** (template-level) |

**Contrast:** **[[Code Scanner]]** items analyze static artifacts; integration tests execute behavior.
