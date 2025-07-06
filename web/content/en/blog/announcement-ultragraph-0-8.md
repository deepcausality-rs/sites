---
title: UltraGraph 0.8 A Foundational Leap into Graph Analytics
description: This post summarizes the new feature of UltrGraph v.0.8
date: 2025-07-06
author: Marvin Hansen
---

[//]: # (SPDX-License-Identifier: CC-BY-4.0)

## Overview

Today, the DeepCausality project announces the release of UltraGraph version 0.8. The team has rebuild the core of the
UltraGraph crate and replaced the previous petgraph based foundation with a new tailor made hypergraph representation
designed for the future of dynamic and large-scale graph analytics.

This release is the culmination of a journey that began with a profound realization: our philosophy had outgrown our
tools. As the DeepCausality project continues to implement the Effect Propagation Process (EPP) to support dynamic
emergent causality, it became painfully obvious that the static, memory-intensive MatrixGraph we were using before has
become a major roadblock. In response, a new hypergraph representation was designed and implemented.

## The new graph evolution lifecycle

The single biggest change in UltraGraph 0.8 is its new dual-state architecture. We recognize that graph-based systems
have two distinct phases: a dynamic "Evolve" phase where the structure is built and modified, and a stable "Analyze"
phase where high-speed queries are essential.

1) **The DynamicGraph State:** This is now the default state for every new graph. It's an adjacency-list-based structure
   optimized for flexibility. Adding nodes and edges is a cheap O(1) operation, perfect for systems where the graph
   structure emerges dynamically over time.

2) **The Frozen State:** When you're ready for analysis, you call `.freeze()`. This is a one-time "compilation" step
   that transforms your graph into a hyper-optimized, immutable Compressed Sparse Row (CSR) format. This state is
   designed for one thing: raw speed.

This new lifecycle is our answer to the challenges of emergent causality. It provides a controlled, predictable way to
transition between a state of evolution and a state of high-performance analysis. The best? When your frozen graph needs
to be modified, you call `.unfreeze()` and your graph structure can evolve further.

## Performance That Speaks for Itself

By freezing a graph into a stable `CsmGraph`, we eliminate CPU cache misses inherent to traditional flexible graph
structures, thus allowing the CPU to operate with maximum efficiency. The results are transformational: On the DeepCausality benchmarks, all reasoning algorithms are now seeing substantial speedups.

| Benchmark (Large Scale)      | Time Before (Old `MatrixGraph` Core) | Time After (New `CsmGraph` Core) | Improvement Factor |
|:-----------------------------|:-------------------------------------|:---------------------------------|:-------------------|
| `reason_all_causes`          | 70.221 ms                            | **51.70 µs**                     | **~1,358x**        |
| `reason_subgraph_from_cause` | 34.933 ms                            | **25.79 µs**                     | **~1,354x**        |
| `reason_shortest_path`       | 35.424 ms                            | **43.80 µs**                     | **~808x**          |

### What This Means for DeepCausality

This new version of `ultragraph` is the engine powering the next version of DeepCausality. It provides the foundation
to:

* **Scale to Massive Graphs:** Analyze systems at a scale that was previously impossible due to memory constraints.
* **Model Emergent Systems:** Directly support the "grow as you go" nature of dynamic causality.
* **Build with Confidence:** Leverage a stable, performant, and dependency-free core for mission-critical applications.

## Conclusion

UltraGraph 0.8 offers unprecedented speed for hypergraph analytics on larger graphs. 

* Explore [the code and examples on GitHub](https://github.com/deepcausality-rs/deep_causality/tree/main/ultragraph).
* [Join the community](https://deepcausality.com/community).

## About

DeepCausality is a hyper-geometric computational causality library that enables fast and deterministic context-aware
causal reasoning in Rust. The DeepCausality project is hosted at the Linux Foundation for Artificial Intelligence and
Data (LF AI & Data). Learn more about DeepCausality on GitHub and join the DeepCausality-Announce Mailing List.

The LF AI & Data Foundation supports an open artificial intelligence (AI) and data community, and drives open source
innovation in the AI and data domains by enabling collaboration and the creation of new opportunities for all the
members of the community. For more information, please visit lfaidata.foundation.

The author and maintainer of the DeepCausality project, Marvin Hansen, is the director of Emet-Labs, a FinTech research
company specializing in applying computational causality to financial markets.

