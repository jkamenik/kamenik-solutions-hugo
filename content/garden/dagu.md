---
title: Dagu
date: '2026-05-09'
lastmod: '2026-07-02'
draft: false
keywords:
- Dagu
params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: No Change
    subcategories:
    - orchestrator
---

[Dagu](https://github.com/dagucloud/dagu). `A lightweight workflow orchestrator that runs shell-based DAGs via a single binary and YAML definitions , worth assessing as a lower-ops alternative to Airflow or Argo for teams t We **assess** it under **[[Platform]]** in the garden.

## Blurb

> Local-first workflow engine with a Web UI for small teams. Define DAGs in a declarative YAML format. Self-contained and no DBMS required. Use any AI agent to manage your DAGs. - dagucloud/dagu

## Summary

Dagu positions itself as a simpler, self-contained alternative to heavier orchestrators like Apache Airflow or Argo Workflows. Key traits:

- **Single binary**; no database required; state is stored on disk
- **YAML-defined DAGs**; each step can be a shell command, sub-DAG, or HTTP call
- **Built-in web UI**; visualize DAG structure, execution history, and logs
- **Cron scheduling**; native support without an external scheduler
- **Low ops overhead**; runs on a single VM or container without Kubernetes

Best suited for teams running DevSecOps pipelines, data engineering tasks, or automation workflows at modest scale who want Airflow-style DAG semantics without the infrastructure burden.

## Details

### History
