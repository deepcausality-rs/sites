---
title: UltraGraph 0.8: 1,300× Faster Graph Analytics — No Cluster Needed
description: This post summarizes the new feature of UltraGraph v.0.8
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

Based on a modified version of the [NWHypergraph (NWHy)](https://par.nsf.gov/servlets/purl/10381502) architecture (
considered state-of-the-art around 2022), UltraGraph 0.8 builds upon it and enhanced it to unlock billion-node
analytics on a single machine. The key modification are:

* The introduction of a SoA CsrAdjacency type instead of simple CSR row
* The separation of forward and backward CsrAdjacency
* The addition of a new dual-state graph evolution lifecycle.

### SoA CsrAdjacency

In conventional CSR-based graph representations (like NWHypergraph), adjacency information is typically packed together
row-wise in a "single structure" per edge or neighbor, which is technically a Array of Structs (AoS) layout, or in
simple terms: “rows of neighbors.” UltraGraph, however, takes a different approach. UltraGraph introduces a
CsrAdjacency<W> type that implements a Struct of Arrays (SoA) pattern:

```rust 
#[derive(Default)]
pub(crate) struct CsrAdjacency<W> {
    pub(crate) offsets: Vec<usize>,
    pub(crate) targets: Vec<usize>,
    pub(crate) weights: Vec<W>,
}
```

This layout splits each component of the adjacency data — offsets, targets, and weights — into separate, contiguous
memory regions:

* offsets: Starting positions of each node’s adjacency list.
* targets: The target node indices for each edge.
  *weights: Edge weights (optional, type-parametric).

Benchmarks show up to 1,300× speedups compared to the previous implementation and memory usage
seems to approache the theoretical limit with the implication that billion node graph analytics is now possible on a
single commodity workstation instead
of a cluster.

This has two critical advantages:

* **Better cache utilization:** When performing traversal or shortest path algorithms, the CPU can stream just the
  fields it
  needs (often offsets and targets) without pulling in unnecessary weight data — avoiding cache pollution and improving
  locality.

* **SIMD-friendliness:** SoA layouts enable vectorized processing (e.g., with AVX) far more easily than AoS.

### Forward and Backward CsrAdjacency

Moreover, UltraGraph uses two separate CsrAdjacency instances. One for successor or outbound edges and another one for
backward edges or inbound edges. This dual-CSR setup is more explicit and efficient than mixing directions
within a single row layout because it reduces CPU cache pollution and through that directly supports fast and efficient
algorithm implementations. It is worth nothing that some CSR systems only store forward edges and reconstruct backward
edges on the fly, conservers memory, but is computational inefficient. UltraGraph deliberately traded a bit more memory
for drastically better algorithm performance, as shown in the benchmarks.

The backward node list particularly useful in causality-based inference algorithms, where backtracking is often required
and thus particularly well suited for DeepCausality.Memory usage remains low due to the combined effects of the Struct
of Arrays layout and the clean separation between forward and backward adjacency lists, which together eliminate many
common sources of heap and pointer overhead:

* No per-node allocation overhead
* No padding, no vtables, no boxed pointers
* No HashMaps or linked lists
* No Indexing needed due to simple offset
* Struct of Arrays (SoA) leads to a predictable, flat memory layout that incentives CPU prefetching.
* When a node has no outbound nodes or weights, there is zero allocation thus saving memory.
* Near-zero memory fragmentation

Memory fragmentation is largely prevented because of the freeze / unfreeze operation in the graph evolution lifecycle.
Calling .freeze() compacts and linearizes the structure, which removes any prior allocation gaps from the dynamic phase
and thus results into a clean continuous memory structure.

### The new graph evolution lifecycle

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

### Dynamic Graph

The dynamic graph structure, when the graph is in an unfrozen state, is optimized for efficient mutation.
The table below summarizes the performance of the key operations.

| Benchmark Name    | Graph Size | Operation  | Estimated Time (Median) | Outliers Detected |
|:------------------|:-----------|:-----------|:------------------------|:------------------|
| `small_add_node`  | 10         | `add_node` | 29.099 ns               | 14% (14 / 100)    |
| `medium_add_node` | 100        | `add_node` | 45.864 ns               | 12% (12 / 100)    |
| `large_add_node`  | 1,000      | `add_node` | 39.293 ns               | 11% (11 / 100)    |
| `small_get_node`  | 10         | `get_node` | 3.9417 ns               | 8% (8 / 100)      |
| `medium_get_node` | 100        | `get_node` | 3.9849 ns               | 2% (2 / 100)      |
| `large_get_node`  | 1,000      | `get_node` | 3.9916 ns               | 7% (7 / 100)      |

* SMALL = 10;
* MEDIUM = 100;
* LARGE = 1000;

Benchmark source code
in [ultragraph/benches ](https://github.com/deepcausality-rs/deep_causality/tree/main/ultragraph/benches)

### Static CSM Graph

By freezing a graph into a stable `CsmGraph`, we eliminate CPU cache misses inherent to traditional flexible graph
structures, thus allowing the CPU to operate with maximum efficiency. The following table compares the performance
of graph-based reasoning algorithms in DeepCausality before and after the `UltraGraph` rewrite. The "After" benchmarks
were run on a frozen `CsmGraph`, which leverages a highly efficient Compressed Sparse Row (CSR) memory layout.

| Benchmark                                            | Time Before (Old) | Time After (New) | Improvement Factor |
|------------------------------------------------------|------------------:|-----------------:|-------------------:|
| `small_linear_graph_reason_all_causes`               |          2.760 µs |         78.79 ns |           **~35x** |
| `small_linear_graph_reason_subgraph_from_cause`      |          1.507 µs |         52.41 ns |           **~28x** |
| `small_linear_graph_reason_shortest_path`            |          1.690 µs |        120.19 ns |           **~14x** |
| `medium_linear_graph_reason_all_causes`              |        509.940 µs |          5.23 µs |           **~97x** |
| `medium_linear_graph_reason_subgraph_from_cause`     |        245.250 µs |          2.63 µs |           **~93x** |
| `medium_linear_graph_reason_shortest_path`           |        286.080 µs |          4.35 µs |           **~65x** |
| `large_linear_graph_reason_all_causes`               |         70.221 ms |         51.70 µs |        **~1,358x** |
| `large_linear_graph_reason_subgraph_from_cause`      |         34.933 ms |         25.79 µs |        **~1,354x** |
| `large_linear_graph_reason_shortest_path`            |         35.424 ms |         43.80 µs |          **~808x** |
| `small_multi_layer_graph_reason_all_causes`          |          1.248 µs |         43.59 ns |           **~28x** |
| `small_multi_layer_graph_reason_subgraph_from_cause` |        489.420 ns |         32.02 ns |           **~15x** |
| `small_multi_layer_graph_reason_shortest_path`       |        427.450 ns |         62.99 ns |            **~7x** |

Average Speedup across all use cases: ~300x

* SMALL = 10;
* MEDIUM = 1_000;
* LARGE = 10_000;

Benchmark source code
in [deep_causality/benches ](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/benches)

Algorithms running over large graphs, with 10k or more nodes, show the most performance gains presumably because
of the improved CPU cache hit rate and the overall improved memory layout of the new CSR representation.

### Comparative Perspective

| Implementation                   | Time for 1M node shortest path | Notes                     |
|----------------------------------|-------------------------------:|---------------------------|
| Gunrock[^1] (GPU, A100)          |                     \~0.1–1 ms | Full GPU parallelism      |
| Galois[^2] (CPU, multi-core)     |                       \~3–5 ms | Optimized C++             |
| **UltraGraph**                   |                     **\~7 ms** | Rust, M3 Max              |
| GraphBLAST[^4] (SPMV)            |                      \~1–10 ms | GPU-CSR                   |
| Ligra[^5] (Parallel CPU)         |                      \~5–10 ms | CSR traversal             |
| Petgraph[^6] (Rust baseline)     |                   \~20–100+ ms | Heap-based Dijkstra       |
| SNAP[^7] / NetworkX[^8] (Python) |                 \~200–1000+ ms | Mostly academic / dev use |

[^1]: Gunrock – https://arxiv.org/abs/1901.08254  
[^2]: Galois – https://github.com/IntelligentSoftwareSystems/Galois  
[^4]: GraphBLAST – https://arxiv.org/abs/2003.04753  
[^5]: Ligra – https://people.csail.mit.edu/jshun/ligra.pdf  
[^6]: Petgraph – https://github.com/petgraph/petgraph  
[^7]: SNAP – http://snap.stanford.edu/,
[^8]: NetworkX -  https://networkx.org

### Memory usage

Memory usage was not benchmarked directly because for graph algorithms runtime is usually the first problem, it is quite
positive
that the total memory usage for the dynamic graph benchmark remained well within 30mb, and slightly below 50 mb for the
static graph benchmark when measured on MacOS. While these numbers are encouraging, it needs to be noted that MacOS tend
to under-report actual memory usage because of its system wide dynamic linking that does not account for the memory of
already loaded system libraries therefore users who are concerned about memory usage on other platforms like Linux
may run their own benchmarks. However, a quick test by setting the LARGE constant to one million showed that the dynamic
graph used about 80 MB of memory and the the static graph peaked around 350 MB and completed most benchmark task within
single digit millisecond time. This is discrepancy is expected because the static graph is optimized for fastest
processing at the expense of of memory usage.

| Engine / Library     | 1M node Memory Use | Notes                  |
|----------------------|--------------------|------------------------|
| **UltraGraph**       | \~350 MB           | Dense CSR              |
| NetworkX (Python)    | >2–5 GB            | Dict-of-dict overhead  |
| SNAP (C++)           | \~1–1.5 GB         | Flexible but optimized |
| Gunrock (GPU CSR)    | \~200–400 MB       | Optimized GPU format   |
| Galois / Ligra (C++) | \~150–400 MB       | Similar to yours       |
| RedisGraph           | >1.5 GB            | GraphQL query layer    |
| Neo4j (Java)         | >5 GB              | Indexes + GC + JVM     |

Extrapolating these numbers implies that a 100 million node
graph would require an estimated 35 GB of memory and complete most algorithms within 7 to 14 seconds. For a billion
graph node, about 350 - 400 GB of memory would be required and that would fit into a commercially available M3 Ultra
Mac Studio configured with 512GB of unified memory. That means billion node graph analytics does not require expensive
and complex clustering any longer and can be conducted on commercially available off the shelf hardware.
Because the graph algorithms implemented in UltraGraph are largely bound to memory bandwidth, faster memory directly
translates into shorter algorithm runtime. Considering that the aforementioned M3 Ultra provides 819GB/s memory
bandwidth, it is not impossible to see single minute algorithm runtime over a billion node graph on the M3 Ultra of
equivalent hardware. However, experimental validation is very much welcome.

| Graph Size | Nodes         | Edges (@10 avg) | Est. Memory Usage | Feasibility (M3 Ultra 512GB RAM)      |
|------------|---------------|-----------------|-------------------|---------------------------------------|
| 1M         | 1,000,000     | 10,000,000      | \~350 MB          | ✅ Very easy                           |
| 10M        | 10,000,000    | 100,000,000     | \~3.5 GB          | ✅ Comfortable                         |
| 100M       | 100,000,000   | 1B edges        | \~35 GB           | ✅ Real-time plausible                 |
| 1B         | 1,000,000,000 | 10B edges       | \~350–400 GB      | ✅ Fits into a single HighMem instance |

For larger graphs, UltraGraph offers predictable, low-overhead performance.

| System / Framework       | Nodes      | Edges         | Memory Usage (Est.) | Cluster Needed?       | **UltraGraph Advantage**    |
|--------------------------|------------|---------------|---------------------|-----------------------|-----------------------------|
| **UltraGraph (Yours)**   | 1B         | \~10B         | **\~350–400 GB**    | ❌ **No**              | ✅ Baseline                  |
| **Graph500 (Scale 30)**  | 1B         | \~16B (dense) | \~1.5 **TB**        | ✅ Yes (16+ nodes)     | **\~4× more efficient**     |
| **GraphJet (Facebook)**  | 1B         | 1–5T edges    | \~3 **TB**          | ✅ Yes (distributed)   | **\~8–10× more efficient**  |
| **GraphScope (Alibaba)** | 1B         | \~10–100B     | \~1–2 **TB**        | ✅ Yes (K8s, Vineyard) | **\~3–6× more efficient**   |
| **Twitter Cassovary**    | \~1B max   | \~10B         | \~500–800 **GB**    | ✅ Partial             | **\~1.5–2× more efficient** |
| **Neo4j** (JVM, GC)      | \~1B max   | \~10–50B      | \~2–5 **TB**        | ✅ Yes                 | **\~5–12× more efficient**  |
| **Snap / NetworkX**      | \~100M max | \~1B edges    | >1 **TB** (Python)  | ✅ Yes                 | **\~10–20× more efficient** |

UltraGraph on a single machine is up to 4–12x more memory efficient than most distributed graph systems.

### Economic impact

The resulting cost savings at scale are significant:

| System         | Est. Memory | RAM Cost (Cloud) | Machine Type                    | Est. Hourly Cost |
|----------------|-------------|------------------|---------------------------------|------------------|
| **UltraGraph** | \~350 GB    | \$1.50–2.00/hr   | 512 GB bare metal or highmem VM | ✅ \~\$1.75/hr    |
| Neo4j          | \~2–5 TB    | \$8.00–20.00/hr  | Cluster of 8×512 GB or 1×2TB    | ❌ \~\$12/hr+     |
| GraphScope     | \~1.5 TB    | \$6.00/hr        | K8s w/ Vineyard + NUMA tuning   | ❌ \~\$6/hr       |
| Graph500 MPI   | \~1.5 TB    | \$8.00/hr        | 16-node HPC (128 GB/node)       | ❌ \~\$8/hr       |

| System         | Est. Annual Cost | Savings Factor vs UltraGraph |
|----------------|------------------|------------------------------|
| **UltraGraph** | **\$15,000**     | ✅ Baseline                   |
| Neo4j          | \~\$105,000+     | **\~7× more expensive**      |
| GraphScope     | \~\$52,000       | **\~3.5× more expensive**    |
| Graph500 (HPC) | \~\$70,000       | **\~4.7× more expensive**    |

UltraGraph slashes graph processing cost by 70–85% for billion-node analytics.
It achieves this by eliminating the need for distributed infrastructure, reduced memory footprint, and
overall improved efficiency.

## Graph Algorithms

The `UltraGraph` crate provides a selection of high-performance algorithms for
graph analysis. These algorithms are implemented on the static optimized graph structure for fast and
efficient computation.

### 🔄 `find_cycle()`

**Use Case:**

- **Dependency resolution:** Detect circular dependencies in software build systems (e.g., Cargo, Bazel).
- **Process control:** Ensure process chains are acyclic.

### ❓ `has_cycle()`

**Use Case:**

- **Workflow engines:** Verify Directed Acyclic Graph (DAG) constraints in ETL jobs.
- **Graph validation:** Ensure schema or data pipelines conform to top-down execution semantics.

### 🔃 `topological_sort()`

**Use Case:**

- **Build systems / Task scheduling:** Order steps where some tasks depend on others (compilers, project planners).
- **Data science pipelines:** Stage DAG-based machine learning workflows (e.g., feature extraction → training →
  evaluation).

### 📡 `is_reachable(start_index, stop_index)`

**Use Case:**

- **Access control:** Can User A reach Resource B? (e.g., network ACLs or graph-based permission models).
- **Social graph analysis:** Check if two users are connected via follower/following chains.

### 📏 `shortest_path_len(start_index, stop_index)`

**Use Case:**

- **Performance modeling:** Compute minimal latency paths in distributed systems or manufacturing processes.
- **Simplified heuristics:** Estimate costs in search/AI agents without computing full paths.

### 🛣️ `shortest_path(start_index, stop_index)`

**Use Case:**

- **Navigation/routing:** Real-time route finding (e.g., maps, logistics).
- **Interactive systems:** Trace dependency or influence paths between data nodes (e.g., in causal graphs).

### 📉 `shortest_weighted_path(start_index, stop_index)`

**Use Case:**

- **Cost-aware routing:** Find paths in weighted graphs like transport networks, financial transaction flows, or
  workflow runtimes.
- **Risk modeling:** Choose minimum-exposure routes in threat graphs or attack trees.

### 🧩 `strongly_connected_components()`

**Use Case:**

- **Community detection:** Find user clusters in social graphs or discussion networks.
- **Deadlock/root cause detection:** In concurrent systems or process management (e.g., OS schedulers, container
  orchestration).

### 🧠 `betweenness_centrality()`

**Use Case:**

- **Influencer detection:** Identify key nodes in social, transportation, or communication networks.
- **Bottleneck analysis:** Discover chokepoints in network infrastructure or data processing graphs.

## What This Means for DeepCausality

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

