---
title: "Dagu"
date: 2026-05-09
lastmod: 2026-05-18
draft: false

keywords:
  - Dagu

params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: "New"
    subcategories:
      - orchestrator

aliases:
  - /radar/platforms/dagu
---

[Dagu](https://github.com/dagucloud/dagu)

`A lightweight workflow orchestrator that runs shell-based DAGs via a single binary and YAML definitions , worth assessing as a lower-ops alternative to Airflow or Argo for teams that don't need a full Kubernetes-native pipeline engine.`

## Blurb

> Dagu is a workflow orchestrator that lets you define workflows as Directed Acyclic Graphs (DAGs) using YAML, execute them with a single binary, and monitor them through a built-in web UI , all without a database or heavy infrastructure.

## Summary

Dagu positions itself as a simpler, self-contained alternative to heavier orchestrators like Apache Airflow or Argo Workflows. Key traits:

- **Single binary**; no database required; state is stored on disk
- **YAML-defined DAGs**; each step can be a shell command, sub-DAG, or HTTP call
- **Built-in web UI**; visualize DAG structure, execution history, and logs
- **Cron scheduling**; native support without an external scheduler
- **Low ops overhead**; runs on a single VM or container without Kubernetes

Best suited for teams running DevSecOps pipelines, data engineering tasks, or automation workflows at modest scale who want Airflow-style DAG semantics without the infrastructure burden.

## History
