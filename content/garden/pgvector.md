---
title: Pgvector
date: '2026-07-24'
lastmod: '2026-07-24'
draft: false
keywords:
- Pgvector
- Postgres vector extension
params:
  aliases:
  - Postgres vector extension
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: New
    subcategories:
    - library
---

[pgvector](https://github.com/pgvector/pgvector) adds exact and approximate vector similarity search to **[[Postgres]]**. We **assess** it when embeddings should share transactions, joins, backups, and access controls with relational application data.

## Blurb

> Open-source vector similarity search for Postgres

## Summary

**When to use:**

- Vector search belongs beside relational data and SQL filters.
- Existing **[[Postgres]]** operations, backups, replication, and security should cover embeddings too.
- One system is preferable to a separate vector service.
- Exact search or HNSW is enough for the target corpus and latency.

**When to skip:**

- Vector search dominates the workload and needs a specialized local library such as **[[FAISS]]** or **[[TurboVec]]**.
- The corpus, query rate, or distribution model exceeds the practical limits of one Postgres deployment.
- You need an ANN algorithm or compressed index that pgvector does not provide.

**Trade-offs:** pgvector keeps vectors close to business data and supports transactional updates. HNSW offers better speed-recall behavior but costs memory and build time. IVFFlat builds faster and uses less memory, but it requires training and careful list/probe tuning.

## Details

### Capabilities

| Area | Support |
|------|---------|
| Search | Exact nearest neighbor, HNSW, IVFFlat |
| Types | `vector`, `halfvec`, `bit`, `sparsevec` |
| Distances | L2, inner product, cosine, L1, Hamming, Jaccard |
| Database features | ACID transactions, joins, WAL, PITR, replication, SQL filters |
| Clients | Any language with a Postgres client |

### Index Choice

| Index | Strength | Cost |
|-------|----------|------|
| None | Exact results and simple writes | Full scan cost grows with table size |
| HNSW | Strong speed-recall trade-off; no training step | Slower builds and higher memory use |
| IVFFlat | Faster builds and lower memory use | Training plus list and probe tuning |

Create one index per distance operator class. Filtering can reduce ANN recall because filtering is applied during index scans. Iterative scans can widen the search when the first pass does not return enough matching rows.

### Basic Shape

```sql
CREATE EXTENSION vector;
CREATE TABLE items (
  id bigserial PRIMARY KEY,
  embedding vector(1536)
);
CREATE INDEX ON items USING hnsw (embedding vector_cosine_ops);
```

Query nearest neighbors with the operator matching the index. For cosine distance, use `ORDER BY embedding <=> $1 LIMIT $2`.

### Comparison Points

- Choose **[[pgvector]]** when relational consistency and SQL filters dominate.
- Choose **[[FAISS]]** for a broad embedded ANN toolkit or GPU search.
- Assess **[[TurboVec]]** when compact online ingest and local deployment dominate.

### References

- [pgvector repository](https://github.com/pgvector/pgvector)
- [pgvector README](https://github.com/pgvector/pgvector/blob/master/README.md)
