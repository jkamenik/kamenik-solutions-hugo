---
title: GraphQL
date: '2025-12-11'
lastmod: '2026-07-02'
draft: false
keywords:
- GraphQL
params:
  garden:
    kind: item
    usefulness: hold
    category: technique
    movement: No Change
    subcategories:
    - api
---

[GraphQL](https://graphql.org/) is a query language for APIs and a runtime for fulfilling those queries with your existing data. We **hold** it under **[[Technique]]** in the garden.

## Summary

Published by Facebook in 2015, it solves a problem that is unique to them that really only existed for a short period of time. Namely, requests were coming in so fast that it was wasting a lot of bandwidth, since not all clients needed the same information.

[[OpenAPI]] is a much lighter weight solution, which solves far more use-cases, until you really do hit the hyper-scale of Facebook. Until you do it is best if you avoid GraphQL.

---
