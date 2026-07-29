---
title: FAISS
date: '2026-07-24'
lastmod: '2026-07-24'
draft: false
keywords:
- FAISS
params:
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: New
    subcategories:
    - library
---

[FAISS](https://github.com/facebookresearch/faiss) is Meta's C++ library for dense-vector similarity search and clustering, with Python wrappers and optional GPU acceleration. We **assess** it as the established baseline for local exact and approximate nearest-neighbor search.

## Blurb

> Faiss is a library for efficient similarity search and clustering of dense vectors.

## Summary

**When to use:**

- You need a mature local library rather than a database service.
- You need exact search, HNSW, product quantization, or GPU indexes under one API.
- You need a baseline for evaluating **[[TurboVec]]**, **[[pgvector]]**, or another vector engine.

**When to skip:**

- You need SQL joins, transactions, metadata filtering, and operational persistence. Start with **[[pgvector]]**.
- You want online low-bit quantization without a separate training phase. Assess **[[TurboQuant]]** or **[[TurboVec]]**.
- You need a managed, distributed vector service rather than an embedded library.

**Trade-offs:** FAISS exposes many index families and tuning controls, but that flexibility adds complexity. Index choice affects recall, latency, memory, training cost, and update behavior. Persistence and application-level metadata remain your responsibility.

## Details

### Index Families

| Family | Use |
|--------|-----|
| Flat | Exact L2 or inner-product search; useful as a recall oracle |
| HNSW | Graph-based approximate search without quantizer training |
| IVF | Partition vectors into inverted lists; tune probes for speed versus recall |
| PQ | Compress vectors with learned product-quantization codebooks |
| GPU | Run supported exact and approximate indexes on one or more GPUs |

FAISS compares vectors with L2 distance or dot product. Cosine similarity uses dot product after normalization. Some compressed indexes store only encoded vectors, reducing memory at the cost of precision.

### Comparison Points

| Option | Better Fit |
|--------|------------|
| **FAISS** | Broad local ANN toolkit, benchmarking, GPU search |
| **[[TurboVec]]** | Compact online ingest using **[[TurboQuant]]**, especially for local RAG |
| **[[pgvector]]** | Vectors beside relational data in **[[Postgres]]** |

### References

- [FAISS repository](https://github.com/facebookresearch/faiss)
- [FAISS documentation](https://faiss.ai/)
- [The FAISS Library](https://arxiv.org/abs/2401.08281)
