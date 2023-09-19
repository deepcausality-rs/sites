---
author: Marvin Hansen
title: About
date: 2023-06-30T15:03:00+08:00
draft: false
---

[//]: # (SPDX-License-Identifier: CC-BY-4.0)

## What is DeepCausality?

DeepCausality is a hyper-geometric computational causality library that enables fast and deterministic context aware
causal reasoning over complex multi-stage causality models. Deep Causality adds only minimal overheads, and thus is
suitable for real-time applications without additional acceleration hardware.

Examples where DeepCausality can be used include dynamic control systems in the IoT industry, dynamic monitoring systems
in the cloud industry, and dynamic market models in the financial industry. Start-ups aiming to disrupt existing
industries may also explore DeepCausality to gain a competitive edge.

See the [documentation for more](/docs/intro/).

## Why was DeepCausality developed?

The author of DeepCausality has a background in Fintech and spent considerable time modeling market volatility. Market
volatility modeling can be done in one of two ways. Mathematical models are still considered the gold standard, and many
institutions operate using them. Because markets work on time-series data, quantitative analysts (quants) use many
time-series statistical techniques (ARIMA) combined with various differential equations. While these models are complex
and require substantial optimization and computational power, they are robust and reliable in operations.

The second way emerged with the advent of artificial intelligence. The idea is relatively simple: train an AI model on
market data and successful trades, then the AI supposedly trades successfully. In practice, this rarely works, although
the reasons are rooted mainly in how contemporary AI works internally and remain largely unclear. There are several
impediments that make conventional artificial intelligence unsuitable for financial markets.
The [background section](/docs/background/) details how these three impediments affect modern machine learning. Solving
one of them is challenging but possible. However, resolving all three would require rethinking the entire foundation of
machine intelligence.

A lesser-known alternative to conventional artificial intelligence is the field
of [computational causality](https://direct.mit.edu/books/book/4789/Computation-Causation-and-Discovery), which has its
foundation in cause-effect relations. However, while computational causality has existed for some time, it is dominated
by academic research and few industry research groups, mainly because no clear-cut methodology has yet emerged. As a
response to the lack of production-ready libraries, the author invented DeepCausality to build what was missing in Rust.

The core concept of DeepCausality is rooted in advanced theoretical physics in which causal models are used to establish
a unified structure for Quantum Gravity. [Lucian Hardy at the
Perimeter Institute](https://perimeterinstitute.ca/people/lucien-hardy) singlehandedly pioneered and published a
novel [conceptualization of
causality](https://arxiv.org/abs/gr-qc/0509120)  ([summary](https://www.quantamagazine.org/quantum-mischief-rewrites-the-laws-of-cause-and-effect-20210311/))
which serves as a foundation in the quest to formalize quantum gravity. Without this groundbreaking contribution, there
would not have been a conceivable way of making advanced computational causality operational for comprehensive industry
applications.

HHowever, it took a few more innovations to make DeepCausality a reality. Among them are context, hyper geometric causal
structures, and contextual causal reasoning. For details, see
the [introduction](https://deepcausality.com/docs/intro/), [architecture](/docs/architecture/),
and [concept](https://deepcausality.com/docs/concepts/) sections of the documentation.

Before DeepCausality, complex market models were challenging to build, hard to understand, and required a lot of
expensive hardware. With DeepCausality the process is easier and faster by orders of magnitude. Capturing intricate
patterns in up to four-dimensional spaces and analyzing them in relation to multiple fast changing contexts actually
becomes feasible. Once the first version of DeepCausality was completed, it was clear that its application reaches well
beyond the financial industry and, in response, the author donated DeepCausality to the Linux Foundation so all of
mankind could benefit from this new technology.

## Linux Foundation

DeepCausality is hosted as a sandbox project at
the [Linux Foundation for data and artificial intelligence](https://lfaidata.foundation/).
The Linux Foundation is the world’s leading home for collaboration on open source software, hardware, standards, and
data. Linux Foundation projects are critical to the world’s infrastructure including Linux, Kubernetes, Node.js, ONAP,
RISC-V, SPDX, OpenChain, and more. The Linux Foundation focuses on advancing best practices and addressing the needs of
contributors, users, and solution providers to create sustainable models for open collaboration. For more information,
please visit  [linuxfoundation.org](https://www.linuxfoundation.org/). 