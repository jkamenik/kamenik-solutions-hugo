---
title: Apache Airflow
date: '2026-05-17'
lastmod: '2026-07-02'
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
    movement: No Change
    subcategories:
    - orchestrator
aliases:
- /radar/tools/apache-airflow
---

[Apache Airflow](https://airflow.apache.org/). Is a Python-centric workflow orchestrator for **DAGs** of tasks (operators, sensors, schedules) with a central metadata database, scheduler, and workers.

## Blurb

> Platform created by the community to programmatically author, schedule and monitor workflows.

## Summary

**Garden stance:** We **assess** Apache Airflow for our estate.

**Key points:** | Topic | Notes |
|-------|--------|
| **Model** | DAGs in Python (`@dag`, operators); UI for run history |
| **Executors** | Local, Celery, Kubernetes; pick based on isolation and scale |
| **Secrets** | Connections/variables in metadata DB; integrate Vault/cloud secret managers |
| **Testing** | Unit-test DAG structure; use staging env for integration |
| **Security** | Lock down web UI, RBAC, and who can trigger DAGs |

**References**

- [Apache Airflow documentation](https://airflow.apache.org/docs/)

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
