---
title: "Apache Airflow"
date: 2026-05-17
lastmod: 2026-06-12
draft: false

keywords:
  - Apache Airflow
  - Airflow

params:
  aliases:
    - Airflow
  garden:
    kind: item
    usefulness: assess
    category: tool
    movement: "New"
    subcategories:
      - orchestrator
aliases:
  - /radar/tools/apache-airflow
---

[Apache Airflow](https://airflow.apache.org/) is a Python-centric workflow orchestrator for **DAGs** of tasks (operators, sensors, schedules) with a central metadata database, scheduler, and workers. We rate it **assess**: the default incumbent for data engineering batch/ETL, but heavy to operate; prefer **[[Argo Workflows]]** (**trial**) on **[[Kubernetes]]** or **[[Dagu]]** (**assess**) when you want lighter ops for new DAG work.

## Blurb

> Apache Airflow is an open-source platform for developing, scheduling, and monitoring batch-oriented workflows.

## Summary

**Role:** orchestrate **[[Workflow]]** steps (extract, transform, load, ML feature jobs, reports), not application deploy. Different lane from **[[GitHub Actions]]** / **[[CI-CD Tools]]** (PR build/test) or **[[ArgoCD]]** (GitOps sync).

**When to assess / keep:**

- Mature data platform already on Airflow (operators, plugins, SLAs)
- Python-first DAGs with rich scheduling (cron, backfill, datasets in Airflow 2.x+)
- Team staffed to run scheduler, metadata DB, and worker pools

**When to choose alternatives instead:**

| Need | Prefer |
|------|--------|
| Steps are K8s pods, artifacts between tasks | **[[Argo Workflows]]** |
| Single VM, YAML DAGs, minimal infra | **[[Dagu]]** |
| CI on merge to main | **[[GitHub Actions]]** |
| K8s-native CI CRDs | **[[Tekton]]** (**assess**) |

**Ops cost:** Airflow expects persistent metadata (Postgres/MySQL), a scheduler process, executors (Celery, KubernetesExecutor, etc.), and monitoring. That is justified at data-platform scale; it is overkill for small automation.

## Details

| Topic | Notes |
|-------|--------|
| **Model** | DAGs in Python (`@dag`, operators); UI for run history |
| **Executors** | Local, Celery, Kubernetes; pick based on isolation and scale |
| **Secrets** | Connections/variables in metadata DB; integrate Vault/cloud secret managers |
| **Testing** | Unit-test DAG structure; use staging env for integration |
| **Security** | Lock down web UI, RBAC, and who can trigger DAGs |

**References**

- [Apache Airflow documentation](https://airflow.apache.org/docs/)
