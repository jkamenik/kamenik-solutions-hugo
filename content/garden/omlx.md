---
title: oMLX
date: '2026-07-07'
lastmod: '2026-07-07'
draft: false
keywords:
- oMLX
params:
  garden:
    kind: item
    usefulness: assess
    category: platform
    movement: New
---

[oMLX](https://omlx.ai/) is a macOS-native MLX inference server with tiered KV cache persistence to SSD, built for coding-agent workloads on Apple Silicon. We **assess** it as a potential [[Ollama]] alternative when cache reuse and multi-model serving matter more than the broadest model catalog.

## Blurb

> macOS-native MLX server with smart caching. Claude Code, OpenClaw, and Cursor respond in 5 seconds, not 90.

## Summary

oMLX targets the pain point where coding agents invalidate KV cache often and force long recomputes. It persists cache blocks to SSD so overlapping prefixes restore in milliseconds instead of recomputing from scratch. That can cut time-to-first-token on long contexts from tens of seconds to a few seconds.

**When to consider**

- Apple Silicon Mac running macOS 15+ with enough unified memory (64 GB+ for larger models).
- Local OpenAI- or Anthropic-shaped clients: Claude Code, Cursor, OpenClaw, or custom agents.
- Multi-model setups (LLM, VLM, embeddings, rerankers) with LRU eviction from one server.

**When to skip**

- Non-macOS hosts or the simplest install path with the largest model library ([[Ollama]] still wins on reach).
- Workloads that never reuse prefixes; SSD cache adds less value.
- Need peak single-user interactive speed without caring about cache persistence (benchmarks often favor Rapid-MLX for that profile).

**Key trade-offs vs [[Ollama]]**

| Area | oMLX | [[Ollama]] |
|------|------|------------|
| Platform | macOS 15+, Apple Silicon | macOS, Linux, Windows |
| KV cache | Hot memory + cold SSD tiers | In-memory; full recompute on invalidation |
| Model source | MLX weights from HuggingFace | Large curated library + pulls |
| Ops surface | Menu bar app + admin dashboard | CLI-first, very approachable |

## Details

- **Upstream:** [omlx.ai](https://omlx.ai/), [jundot/omlx](https://github.com/jundot/omlx) (Apache 2.0). Evolved from vllm-mlx with multi-model serving, tiered caching, VLM support, and a macOS menu bar app.
- **Requirements:** macOS 15 (Sequoia)+, Python 3.10+, Apple Silicon (M1+). 16 GB RAM minimum; 64 GB+ recommended for larger models.
- **API:** OpenAI-compatible HTTP on `localhost:8000`; native `/v1/messages` Anthropic endpoint. Dashboard generates client config snippets.
- **Models:** MLX-format HuggingFace models (Qwen, LLaMA, Mistral, Gemma, DeepSeek, and others). Built-in HuggingFace downloader in the admin UI.
- **Features:** Continuous batching, concurrent requests, multi-model LRU management, reasoning-tag handling, vision-language models since v0.2.0.
- **Ecosystem:** Other Apple Silicon MLX servers include Rapid-MLX (speed-focused) and Apple's mlx-lm reference server. [[Ollama]] 0.19+ adds an experimental MLX backend that narrows the native-MLX gap.
