---
title: "dbt-core"
date: 2026-01-14
lastmod: 2026-05-18
draft: false

keywords:
  - dbt-core
  - dbt
  - dbt Core

params:
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "No Change"

aliases:
  - /radar/tools/dbt-core
---

[dbt Core](https://docs.getdbt.com/) is the open-source CLI that transforms data in the warehouse: versioned SQL models, tests, docs, and a DAG executed with `dbt build`. We rate it **trial** for analytics engineering in the warehouse; pair orchestration with **[[Apache Airflow]]** or **[[Argo Workflows]]** when schedules and cross-system DAGs sit outside dbt.

## Blurb

> dbt is a SQL-first data transformation workflow for teams who already know SQL.

## Summary

**Role:** transform data **inside** the warehouse (models, tests, docs). Not a general **[[CI-CD Tools]]** runner; not **[[Apache Airflow]]** (though Airflow often triggers `dbt run`).

**When to trial:**

- Warehouse-native analytics engineering (Snowflake, BigQuery, Redshift, Postgres, etc.)
- Git-reviewed SQL models, `dbt test`, and generated lineage docs
- Team comfortable with Jinja-templated SQL and `dbt_project.yml` layout

**When to skip:**

- No warehouse or transforms belong in an app service, not SQL models
- Need only light ETL scripts; a smaller tool may suffice
- Org will not adopt project structure (`models/`, `macros/`, `seeds/`, etc.)

**Typical flows:**

| Goal | Commands |
|------|----------|
| Fresh deps + run | `dbt deps` then `dbt build` (or `dbt run` + `dbt test`) |
| Docs locally | `dbt docs generate` then `dbt docs serve` |
| Clean artifacts | `dbt clean` before deps when debugging compile state |

## Details

### Project layout

The **project** is the unit of work. It **must** include `dbt_project.yml` (model paths, profiles, vars). Main artifact types:

| Artifact | Purpose |
|----------|---------|
| **Models** | Transforms; nodes in the execution DAG |
| **Snapshots** | SCD-style history for mutable sources |
| **Seeds** | CSV loads into the warehouse |
| **Tests** | Data quality on models and sources |
| **Macros** | Reusable Jinja/SQL |
| **Sources** | Upstream tables loaded by other tools |
| **Exposures** | Downstream consumers of the project |
| **Analyses** | Ad hoc SQL (not materialized on `run`) |

(Semantic models, metrics, and saved queries apply when using the metrics layer; see current dbt docs for your version.)

### CLI reference (common)

- `build` — run DAG in order (models, tests, seeds, snapshots as configured)
- `run` — execute models only
- `test` — run tests (usually after `run`)
- `compile` — render SQL without executing
- `deps` — install package dependencies
- `debug` — connection and profile diagnostics
- `freshness` — source freshness checks
- `snapshot` / `seed` — run those node types

### Incremental models on existing tables

When a table is owned elsewhere but dbt should merge new rows:

1. Model name matches the table (case-sensitive per adapter)
2. `materialized='incremental'`
3. `unique_key` set for merge/upsert
4. `incremental_strategy` (`append` or `merge` per adapter)
5. Use `is_incremental()` and `{{ this }}` for watermark logic

```sql
{% if is_incremental() %}
  AND created_at > (SELECT COALESCE(MAX(scan_timestamp), '1970-01-01'::timestamp) FROM {{ this }})
{% endif %}
```

See [Incremental models](https://docs.getdbt.com/docs/build/incremental-models).

**Garden pattern:** **trial** dbt for warehouse transforms; orchestrate schedules with **[[Apache Airflow]]** (**assess**) or **[[Argo Workflows]]** (**trial**) when the DAG spans more than dbt.

**References**

- [dbt documentation](https://docs.getdbt.com/)
- [dbt-core on GitHub](https://github.com/dbt-labs/dbt-core)
