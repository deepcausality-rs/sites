---
title: DeepCausality v.0.8 adds support for non-Euclidean context
description: This post summarizes the new feature of DeepCausality v.0.8
date: 2025-06-27
author: Marvin Hansen
---

[//]: # (SPDX-License-Identifier: CC-BY-4.0)

## Overview

The DeepCausality project announces the release of DeepCausality 0.8 that strengthens the core of the framework with added async concurrency, added non-Euclidean context, added relative temporal index, and a unified adjustable trait implementation.

## 🚀 Highlights in 0.8

- **Async concurrency** full compatibility with Tokio
- **Added non-Euclidean geometry** contexts
- **Added relative temporal index** for simplified handling of time graphs.
- **Unified `Adjustable` trait** implementation across all context types
- **Simplified trait system** for easier extensibility and integration
- **95% test coverage** across the entire codebase


##  Added support for Tokio & Async Rust!

In DeepCausality 0.8, all instances of `RefCell` were replaced with `Arc` across the framework, allowing safe usage in multi-threaded runtimes like **Tokio** or **Rayon**.
As a result, all Causaloids, Contextoids, and Model types are now `Send` and `Sync`, enabling true parallel inference pipelines. See the new [Tokio code example](https://github.com/deepcausality-rs/deep_causality/tree/main/examples/tokio) for details about how to build concurrent causal inference with DeepCausality.


## Added non-Euclidean context

Previously, DeepCausality supported flat-space representations such as EuclideanSpace and EuclideanSpacetime. With 0.8, DeepCausality gains native support for:

### 📍 Non-Euclidean Space Contexts
- EcefSpace - 3D Cartesian space relative to the Earth's center of mass
- NedSpace - A local tangent plane spatial context using the North-East-Down (NED) reference frame
- WGS84 Geospace -  geodetic coordinates space
- QuaternionSpace — rotation-aware 3D orientation tracking

### 🪐 Non-Euclidean Spacetime Contexts
- Minkowski spacetime — special relativistic flat spacetime
- Lorentzian spacetime — general relativistic curved spacetime
- Tangent Bundle spacetime — position and velocity within local tangent spacetime

### 🧭 Advanced Time Representations
- Discrete time - represents discrete, uniformly spaced ticks
- Euclidean time semantically represents the rotated, imaginary-time axis as a real-valued scalar.
- Lorentzian time corresponds to the real-valued coordinate time used in special and general relativity
- Symbolic time models time points that are defined in terms of symbolic relationships.

**What Can You Do With The New Context Types?**

**Tangent Spacetime**
Combines spacetime position and velocity to model movement in a relativistic manifold. Enables local inertial modeling, frame drift detection, and velocity-aware corrections in high-altitude avionics navigation.

**Lorentzian Spacetime**
Models gravitational effects, time dilation, or geometric distortion commonly adjusted for in Global Satellite Navigation Systems (GNSS) such as GPS, Galileo, or GLONASS.

**Quaternion Space**
Quaternions efficiently model 3D orientation in space and are used for robotics, computer vision, and inertial navigation systems.

DeepCasuality 0.8 introduces the unique capability of flexible integration of heterogeneous geometries. For example, a Euclidean context represents data in a Euclidean representation whereas additional contexts for QuaternionSpace or LorentzianSpacetime represent non-Euclidean data. DeepCausality supports multiple contexts since 0.6 and, because of its generic design, a QuaternionSpace context will be statically verified by the compiler to hold only QuaternionSpace data thus preventing dangerous unit or geometry mismatches. This enables the fusion of different sensor data i.e. position data, sensor data, and drift detection data with each data set residing in its respective geometric context.

In scenarios where data of different space, time, or spacetime representations have to reside within the same context, DeepCausality offers three convenience types for uniform yet type-safe access to heterogeneous geometry data:

* SpaceKind
* TimeKind
* SpaceTimeKind

Each of those convenience types implements all relevant traits over an abstract algebraic data structure that gives uniform access to the underlying types. For example, a contextoid of type SpaceKind gives uniform access to Euclidean, Ecef, Ned, WGS84, and Quaternion space all from within the same context. Likewise, a contextoid of type SpaceTimeKind gives uniform access to all spacetime types from within the same context.

All context and all convenience types implement the various traits of the extensive context trait systems, which allows advanced users fine-grained customization. If you need a different spacetime distance metric, you can overwrite the Metric trait. If you need a custom geometry, you can implement the relevant traits and plug your custom geometry types into DeepCausality.

## Added Relative Temporal Index to Context

A temporal hypergraph, by design, holds all past and present temporal values simultaneously within its structure. This co-existence of multiple temporal points simplifies non-trivial temporal arithmetic over hetero-scaled time units, yet it imposes a vexing problem: How do you know if a time value in a node of the graph is current or past?

The problem is non-trivial because, as time progresses, the context continuously generates the non-Euclidean temporal hypergraph representation with the implication that, at one lookup, the value of a temporal node is current, but at the next one, it might be past; however, the exact temporal distance at which a “current” value becomes “past” depends on the node’s time scale.

DeepCausality 0.8 solves the problem by adding a relative temporal index to the context that allows to get or set the current or previous time index relative to its time scale. The new CurrentTimeIndex and PreviousTimeIndex are optional, but when imported provide a default implementation that allows to set scale depending time indexes.

For example, setting the index for the current day becomes as simple as calling the corresponding *set_current_day_index* method within the index. Once the index of the current day has been retrieved using the *get_current_day_index*, the graph node holding the current day data can be retried from the context using the existing *get_node* methods from the context. Advanced users can overwrite the TimeIndexable, CurrentTimeIndex, and PreviousTimeIndex to customize time indexing to specific requirements.

## Unified `Adjustable` Trait Across All Context Types

Modeling dynamic systems requires contexts that can evolve. DeepCausality 0.8 introduces a simplified and more powerful way to handle dynamic context data. All AdjustableXYZ types are gone  for good. Now, you work with primary context types, like EuclideanSpace, and when you need dynamic updates or adjustments then import the Adjustable trait and implemented update() and adjust() methods become available on the original type. All Adjustable implementations for all context types include rigorous validation and overflow protection, ensuring that your dynamic context modifications are safe, robust, and reliable.


## Conclusion

DeepCausality 0.8 offers uniform and explainable causal reasoning across Euclidean and non-Euclidean context data to support advanced use cases for dynamic causal modeling.

Get Started with DeepCausality 0.8 Today!

* Check out the Release Notes for full details.
* Explore the [code examples on GitHub](https://github.com/deepcausality-rs/deep_causality/tree/main/examples).
* **Join the [community]**(https://deepcausality.com/community/).


## About

[DeepCausality](https://deepcausality.com/) is a hyper-geometric computational causality library that enables fast and deterministic context-aware causal reasoning in Rust. Please give us a [star on GitHub.](https://github.com/deepcausality-rs/deep_causality)

The LF AI & Data Foundation supports an open artificial intelligence (AI) and data community, and drives open source innovation in the AI and data domains by enabling collaboration and the creation of new opportunities for all the members of the community. For more information, please visit [lfaidata.foundation](https://lfaidata.foundation).

The author and maintainer of the DeepCausality project, Marvin Hansen, is the director of Emet-Labs, a FinTech research company specializing in applying computational causality to financial markets.