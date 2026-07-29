---
title: TurboVec
date: '2026-07-24'
lastmod: '2026-07-29'
draft: false
keywords:
- TurboVec
params:
  garden:
    kind: item
    usefulness: assess
    category: code
    movement: No Change
    subcategories:
    - library
---

[TurboVec](https://github.com/RyanCodrai/turbovec) is a Rust vector index with Python bindings built on Google Research TurboQuant. We **assess** it for local RAG where memory, online ingest, and no separate train step matter.

## Blurb

> A 10 million document corpus takes 31 GB of RAM as float32. turbovec fits it in 4 GB - and searches it faster than FAISS.

## Summary

**What it is:** Local approximate nearest-neighbor index. Implements data-oblivious quantization so you add vectors without a codebook train or rebuild as the corpus grows. Ships as `pip install turbovec` and `cargo add turbovec`. Drop-in stores exist for LangChain, LlamaIndex, Haystack, and Agno.

**When to use:**

| Situation | Notes |
|-----------|--------|
| Local or air-gapped RAG | Keep embeddings on-box; pair with open embedding models and **[[Ollama]]** |
| Memory-bound corpora | Roughly 8x smaller than float32 for the headline 10M-doc example |
| Growing indexes | Online ingest; no PQ-style train/rebuild cycle |
| Hybrid retrieval | `search(..., allowlist=...)` filters inside the SIMD kernel |

**When to skip:**

- Managed multi-tenant vector DBs with ops already paid for
- Workloads that already trust FAISS PQ FastScan and need its exact toolchain
- Needs beyond a local index (distributed serving, rich metadata query language)

**Trade-offs:** Strong ARM speed vs FAISS IndexPQFastScan in project benches; x86 is closer and sometimes slightly behind on 2-bit. Young solo-maintained project; watch API and release stability before betting a production path on it. FAISS remains the usual baseline to beat.

## Details

### Stack Fit

| Piece | Notes |
|-------|--------|
| Core | **[[Rust]]** crate + **[[Python]]** bindings (maturin) |
| Algorithm | [TurboQuant](https://arxiv.org/abs/2504.19874) (ICLR 2026) |
| Bit widths | 2-bit and 4-bit scalar quantization after random rotation |
| APIs | `TurboQuantIndex`, `IdMapIndex` (stable external ids + O(1) remove) |
| Persistence | `.tv` / `.tvim` write/load |

### How It Differs From Classic PQ

TurboQuant rotates vectors so coordinates follow a known marginal, then quantizes with a Lloyd-Max codebook derived from that math. No data-dependent codebook training. TQ+ adds a light per-coordinate calibration on first add. Length renormalization corrects inner-product bias at score time.

### Integrations

- LangChain: replaces in-memory vector store (`turbovec[langchain]`)
- LlamaIndex: replaces `SimpleVectorStore` (`turbovec[llama-index]`)
- Haystack: replaces in-memory document store (`turbovec[haystack]`)
- Agno: replaces LanceDB-backed store (`turbovec[agno]`)

### References

- [GitHub: RyanCodrai/turbovec](https://github.com/RyanCodrai/turbovec)
- [PyPI: turbovec](https://pypi.org/project/turbovec/)
- [TurboQuant paper (arXiv:2504.19874)](https://arxiv.org/abs/2504.19874)
