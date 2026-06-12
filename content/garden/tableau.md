---
title: "Tableau"
date: 2026-06-12
lastmod: 2026-06-12
draft: false

keywords:
  - Tableau

params:
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - dashboarding
---

[Tableau](https://www.tableau.com/) is Salesforce's enterprise visualization and analytics platform for analysts and business users. It emphasizes drag-and-drop dashboards and a large connector catalog. We **assess** it when procurement or existing Tableau skill pools dominate; greenfield OSS BI stays **[[Apache Superset]]** or **[[Metabase]]** Cloud.

## Blurb

> Tableau helps people see, understand, and act on data.

## Summary

**What it is:** Desktop Prep/Server/Cloud suite for visual analytics, published dashboards, and embedded views.

**When to use:** Enterprise already licensed Tableau; business teams need polished viz without SQL.

**When to skip:** Engineer-first SQL dashboards (**[[Redash]]**). Cloud-native OSS stack (**[[Grafana]]** + warehouse BI).

**Key features:** Visual prep, ask Data, row-level security in Server/Cloud, Salesforce integrations.

## Details

| Topic | Notes |
|-------|--------|
| **Deploy** | Tableau Cloud, Server, or Desktop plus Server for sharing |
| **Cost** | Per-user licensing; factor embed and refresh capacity |

**References**

- [Tableau documentation](https://help.tableau.com/)
