---
title: "Container Structure Test"
date: 2023-03-03
lastmod: 2026-06-12
draft: false

keywords:
  - Container Structure Test

params:
  garden:
    kind: item
    usefulness: adopt
    category: code
    movement: "No Change"
    subcategories:
      - test-framework
---

[Container Structure Test](https://github.com/GoogleContainerTools/container-structure-test) (Google Container Tools) validates **built container images** before push or deploy: command output, filesystem paths, file contents, and image metadata. We **adopt** it under **[[Code]]** / **[[Test Framework]]** for any pipeline that produces **[[Containerization]]** artifacts, run after `docker build` (or equivalent) in **[[GitHub Actions]]** or CI.

## Blurb

> Container Structure Tests are a powerful framework to validate the structure of a container image.

## Summary

**Role:** image acceptance tests defined in YAML, executed against a tag or tarball:

```bash
container-structure-test test --image <image> --config <testfile>
```

**Test types:**

| Type | Validates |
|------|-----------|
| **Command** | Run a command in the image; check exit code and output |
| **File existence** | Path present or absent |
| **File content** | Expected or forbidden substrings in a file |
| **Metadata** | Env, exposed ports, entrypoint, user, etc. |

**When to use:** golden images, minimal distroless/runtime images, and charts that bake config into the image; catch "wrong binary missing" before Kubernetes ever sees the tag.

**When to skip:** application integration tests that need live Postgres/Kafka (use **[[TestContainer]]**, **assess**). Helm template output (use **[[Helm Unittest]]**, **adopt**).

**Pairs with:** **[[Unit Testing]]** for app code; **[[Docker]]** or compatible builders; **[[Open Container Initiative]]** image layout expectations.

## Details

| Topic | Notes |
|-------|--------|
| **Config** | One or more YAML test files; version schema in project docs |
| **CI** | Fail the job on any test failure; pin the CST binary version |
| **Speed** | Faster than booting a cluster; slower than pure unit tests |
| **Scope** | Image contract only, not runtime policy or network behavior |

**References**

- [container-structure-test](https://github.com/GoogleContainerTools/container-structure-test)
