---
author: Marvin Hansen
title: "Introduction"
date: 2023-08-27T14:06:21+08:00
draft: false
---

[//]: # (SPDX-License-Identifier: CC-BY-4.0)

{{< toc >}}

## Overview

DeepCausality is a hyper-geometric computational causality library that enables fast and deterministic context aware
causal reasoning. Deep causality offers multiple benefits such as fast reasoning, low-cost operations due to low
computational requirements, the ability to analyse numerous data feeds in real-time, and even reasoning across data that
changes over time, space, and spacetime through an adjustable context.

Examples where DeepCausality can be used include dynamic control systems in the IoT industry, dynamic monitoring systems
in the cloud industry, and dynamic market models in the financial industry. Start-ups aiming to disrupt existing
industries may also explore any combination of deep learning and DeepCausality to gain a competitive edge.

## What is computational causality?

Contemporary deep learning has taken statistics one step further, but there are still certain limitations with its
correlation-based foundation. For more details, see the [background section.](/docs/background/). For one, correlation
leads to non-determinism because, just by chance, a variable can correlate with otherwise random values. Then,
separating the signal from the noise requires very large data quantities. More fundamentally, deep learning requires
that data used during training must follow the same distribution as the data the model encounters in production. If that
is not the case, then deep learning is insufficient, and the model requires re-training. When the data distribution is
either unstable or continuously shifting, deep learning falls short.

Computational causality, on the other hand, utilizes cause-and-effect relationships to go beyond correlation-based
predictive models and toward AI systems that can prescribe actions more effectively and autonomously. Then,
computational causality is data distribution invariant meaning it is not necessary that training, testing, and
production data must adhere to the same data distribution. Essentially, causality-based reasoning is deterministic,
meaning that the same set of input data feeds into a model and yields the same result, and this is very different from
correlation-based deep learning, which may or may not give you a similar answer.

Computational causality and deep learning operate at opposite ends of the spectrum meaning that they are complimentary
in the sense that computational causality excels where deep learning falls short. Likewise, where causality underwhelms,
deep learning outperforms it. Specifically, computational causality is outstanding at fast deterministic reasoning using
only very little data, but cannot do generative models such as large languages models or image generations, a
traditional strength of deep learning.

Computational causality is actively researched by leading academics, such as:

* [Judea Pearl](http://bayes.cs.ucla.edu/jp_home.html) at UCLA
* [Lucien Hardy](https://perimeterinstitute.ca/people/lucien-hardy) at the Perimeter Institute
* [Ilya Shpitser](https://www.cs.jhu.edu/~ilyas/) at Johns Hopkins University
* [Miguel Hernan](https://www.hsph.harvard.edu/miguel-hernan/), [Causal Lab](https://causalab.sph.harvard.edu/) at
  Harvard University
* [Elias Bareinboim](https://causalai.net/) at Columbia University

However, it was not until the last five years that the IT industry started exploring and adopting computational
causality. Netflix, for example, published in 2022 that they use causality in their recommendation engine.
Unfortunately, Netflix did not open source its causality software. Other companies contributed meaningful work to the
field through their open-source commitment:

* [Causality and Machine Learning](https://www.microsoft.com/en-us/research/group/causal-inference/) at Microsoft
  Research
* [Causal ML](https://github.com/uber/causalml) at uber.

Currently, all publicly available research in computational causality relies on libraries written in Python, with Rust
not being explored yet. DeepCausality changes that and brings computational causality to Rust.

## Why Rust?

DeepCausality has been designed to be fast, efficient, robust, and reliable from its inception. Rust was chosen as the
programming language because it fully aligns with the project goals. Rust’s memory safety was the decisive argument,
considering that causal models may grow large and complex and require strong memory guarantees to operate reliably and
cost-effectively.

## What is DeepCausality?

DeepCausality is a hypergeometric computational causality library for Rust that contributes several novel concepts:

1. Hypergeometric recursive causal models
2. Hypergeometric context up to four dimensions
3. Contextual causal reasoning
4. End-to-end explainability
5. Causal State Machines

### Hypergeometry

Contemporary computational causality has arithmetic and algebra as its foundation, which works well for formalization
but has its limits when complexity grows. When a use case requires hundreds if not thousands of causal relations, then
the arithmetic becomes increasingly complex. While mathematical complexity is no obstacle to academic research, it is to
scalability. On the other hand, geometry uses much simpler arithmetic, but for other reasons cannot handle complex
structures; therefore, the actual challenge centers around simplifying structural complexity.

DeepCausality solves structural complexity with recursive isomorphic causal data structures that enable concise
expression of complex structures. That means, instead of relying on algebraic structures, causal models are expressed as
graph networks over which DeepCausality reasons. DeepCausality can reason over a single cause in the graph, a selected
sub-graph, or the graph itself.

A causal hypergraph may contain any number of nodes with any number of relations to other nodes, with each node
representing a cause. Furthermore, a node may contain a collection of causes or even another causal graph. That means a
causal model represented as a graph may store other causal sub-models in each node of the causal graph, hence
efficiently representing otherwise complex causal structures.

### Context

Contemporary computational causality assumes that the modeled causal relations are all there is to a model and,
therefore, shifted focus to causal discovery learning to find causal relations in data. Only very recently, researchers
at [Cambridge University started conceptualizing the addition of a temporal context ](https://arxiv.org/abs/2212.00911)
to causality-based deep learning.

DeepCausality already added structure through the hypergeometric representation of causality. Even further,
DeepCausality also supports contextualizing causal models. Specifically, a context may be built from
multiple data sources or live data streams and then be accessed from within the causal model, thus allowing efficient
reasoning over contextualized data. For more advanced use cases,
DeepCausality [supports multiple contexts](https://deepcausality.com/blog/announcement-multiple-contexts/) hence
allowing more comprehensive contextual modelling.

Context in DeepCausality can be either of fixed structure, meaning only values stored in it get updated, or of dynamic
structure, defined dynamically at system runtime. The first case is more memory efficient and ideal when data sources
and structures are known to remain stable. The second case is less efficient and more complex because it requires
regular context pruning (removing values no longer needed) to avoid excessive memory usage, but allows for more dynamic
and self-adaptable designs. A dynamic context is naturally a more complex design but is fundamentally supported by
DeepCausality.

### Contextual causal reasoning

Combined, a causal hypergraph and a contextual hypergraph form the backbone of contextual causal reasoning in
DeepCausality. Additionally, multiple causal models in DeepCausality may share the same context but evaluate different
aspects of it, hence allowing memory-efficient yet powerful system designs.

Contextual causal reasoning allows the exploration of new approaches to existing challenges. For example, transferable
context structures become relevant for allowing the transfer of entire model groups when a context shared across all
models can be transferred into a new area. Consequently, encoding contextual assumption then provides for the automatic
search of novel applications in which a context and all dependent models can be transferred.

Causal model evaluation becomes relatively simple since multiple variations of a causal model can be evaluated side by
side in a shared context to determine which model performs best. Likewise, an existing set of causal models might be
evaluated against multiple contexts to see whether a better context may improve model performance. This might work best
with a high degree of automation to drive continuous model generation, evaluation, and re-deployment.

Another area largely unexplored is the combination of deep learning with deep causality. From a technical perspective,
it is possible to feed the output of multiple contextualized causal models into a deep learning model. Conversely, it is
also technically possible to embed a neuronal network inside a causal model, use data from a context to let the neuronal
network make an inference, and then feed the inference result into a causal function.

Even though neuronal nets are structurally non-deterministic, as long as the neuronal net remains embedded into an
encapsulating causal structure, the final decision calculated by the causal model remains deterministic. This side
effect paves the way to embed neuronal nets in systems that would otherwise not allow the application of deep learning
due to the requirement of deterministic execution.

### End-to-end explainability

Computational causality always supported explainability, and DeepCausality is no exception as it offers a built-in
mechanism to understand the causal reasoning process: the Graph explanation path.
Each cause has a built-in explain function that returns the string description of a cause and how it is evaluated, hence
giving an explanation. For a collection of causes, these strings are combined in the evaluation order. For a graph, the
explanation is constructed based on the graph path taken during the reasoning. Graph path refers to the actual pathway
taken through a hypergraph model.

While deep causality supports standard algorithms such as the shortest path, it also supports reasoning over a custom
path in the sense that you can define the start and end node of a specific sub-graph. For even more detailed control,
you can also retrieve nodes individually and reason over each one separately. As a result, one can see precisely the
complete line of reasoning with the actual evaluation at each stage. While this does not explain why something
unexpected happened, it informs at least exactly where and when it happened and what the actual evaluation at hand was.
That is already a solid starting point to identify the relevant data, which helps to figure out why these were
deviating.

An often-overlooked benefit of full explainability is the understanding of evolving complex systems. Specifically, when
an underlying causal model changes, so does the line of reasoning. That, combined with the supported end-to-end
explicability, allows for deliberate model inquiry under simulated adverse evolution to simulate model robustness in a
changing environment ahead of deployment. For example, in the financial industry, a common question is whether a model
would survive a 2008-like crash. To investigate, the model parameters can be changed, and through different lines of
reasoning from each model, an analyst can better understand the relative importance of each factor used in the model.

### Causal State Machines

Conventionally, causal models are seen as separate from the subsequent intervention mainly for flexibility reasons. The
model-action separation remains valid in many use cases, but there is also a group of use cases where this is
undesirable. Specifically, dynamic control systems require a fixed link to subsequent actions to preserve deterministic
execution. Conventionally, a control system can often be expressed through a finite state machine because the number of
all possible system states is known upfront.

With the advent of cloud-native applications, a new paradigm of control system emerged out of the need to monitor and
supervise software systems that dynamically come online, serve a certain purpose, and then may be taken offline with the
entire process handled programmatically. Conventionally, the process requires the usage of either a cloud provider’s SDK
or an abstraction over multiple cloud systems such as Terraform.
Unlike conventional control systems, the number of known system states is not known until the system is online. This
fact categorically rules out finite state machines because system states are not fully known prior to designing the
state machine. Besides, the same problem occurs when supervising parametric causal models that are programmatically
taken online and offline.

Upon closer examination, a generalized state machine only tests whether a state has been reached and, if so, triggers a
specific action. In causal language, a causal state machine would test whether a particular cause has been identified
and, if so, initiates a subsequent action (intervention) that leads to a desired effect.

DeepCausality comes with a causal state machine that defines states as causes and links each cause to a specific action.
Since both the cause and the action are expressed as regular Rust functions that are stored as function pointers,
virtually any complex action can be expressed through a causal state machine.

Unlike a finite state machine, a causal state machine can be fully generated at runtime by adding or removing causal
states dynamically. Therefore, it is not necessary to know possible system states when designing a causal state machine.
Instead, when a system that requires supervision comes online, the exact states can be provided through the system
metadata, which then configures the causal state machine and assumes automated supervision of the system that came
online. This process equates to the notion of a dynamic control system because it is configured and examines system
control proactively for as long as the originating system operates.

While DeepCausality only provides the fundamental building blocks of a causal state machine, these already enable system
engineers to build dynamic control systems with only moderate effort. The GitHub repository contains a code example (
called CSM) of an industry sensor network expressed as a dynamic control system using only causal state machines.

## What can you do with DeepCausality?

### Contextualized streaming data

There are several categories of applications for which conventional deep learning remains unsuitable but where
DeepCausality may provide an alternative. First, the advent of drones has led to an explosion of various monitoring
solutions across multiple industries. Conventional deep learning may not suit these multi-dimensional data streams from
drones very well because of the lack of contextualization that would give more meaning to the data and inform decisions
in a mode. DeepCausality offers a new direction of streaming multiple complex data feeds into a context that serves as a
single source of truth to various models, regardless of whether these are deep learning or deep causality models.

### Financial modelling

Financial markets are full of scenarios in which conventional deep learning falls short because of its inability to
capture causal relations across temporal-spatial relations in time series data. DeepCausality has been designed to
tackle these problems and allows the formation of an instrument-specific context updated in real-time to inform one or
more models that relate current data to its context to inform decisions. Because of the flexibility in designing a
context, temporal and spatial patterns can be expressed and tested in real time, thus significantly reducing the
complexity and maintainability of financial models.

### Dynamic control systems

Cloud-native applications that require a significant number of dynamic system configurations and monitoring may benefit
from simplifying dynamic control systems via causal state machines. This is of particular interest for application
service providers that offer customized cloud solutions for each client.

Industries subject to safety regulations, such as transportation, avionics, or defence, might see DeepCausality as a
viable alternative in areas where non-deterministic deep learning cannot be deployed for regulatory or safety reasons.
Furthermore, industry monitoring solutions may benefit from the simple and robust design causal state machines provide
in terms of the ease of adding new sensors dynamically.

### Combined deep causality learning

Start-ups aiming to disrupt existing industries may explore any combination of deep learning and DeepCausality to gain a
competitive edge over existing solutions in their industries. From a technical perspective, combining deep causality
with deep learning models via a shared context is possible. Lastly, even fields such as theoretical physics,
advanced science, or avionics may explore deep causality for its ability to express and adjust a complex spacetime
context as part of advanced simulations. DeepCausality is only one part of the larger quest of building intelligent
systems and aims to explore novel concepts along the way.

**Next:** [Architecture](/docs/architecture/)


## About

[DeepCausality](https://deepcausality.com/) is a hyper-geometric computational causality library that enables fast and
deterministic context-aware
causal reasoning in Rust. Please give us a [star on GitHub.](https://github.com/deepcausality-rs/deep_causality)