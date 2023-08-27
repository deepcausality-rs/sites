---
title: "Concepts"
date: 2023-06-30T15:31:43+08:00
draft: false
tags: ['Rust', 'Concepts']
---

# Core Concepts

The core concepts implemented in deep causality derive from "Theoretical Impediments to Machine
Learning" ([Perl,2018](https://arxiv.org/abs/1801.04016))

##  Encoding Causal Assumptions

Explicit assumptions about the underlying data, patterns, and structures enable transparency and testability.
More profoundly, transfer learning is one of the critical advancements in machine learning that allows
relatively easy adoption of existing models without the time-consuming process of re-learning the entire model.

In practice transfer-learning requires model-fitting, which means re-training the outer layers
of a neuronal net because of the absence of verifiable assumptions that would answer whether the
model is even transferable w.r.t. to the underlying data. That is another way of asking whether the data distribution
of the model training data resembles the data distribution of the data of the targeted transfer learning.
Deep causality implements verifiable assumptions in the following way:

## Assumptions

Traits:

* [Assumable](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/protocols/assumable/mod.rs)
* [Assumable Reasoning](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/protocols/assumable/mod.rs)

Extensions:

* [Assumable Array](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/extensions/assumable/mod.rs)
* [Assumable Map](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/extensions/assumable/mod.rs)
* [Assumable Vector](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/extensions/assumable/mod.rs)

Types:

* [Assumption](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/types/reasoning_types/assumable/assumption.rs)
* [EvalFn](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/types/reasoning_types/assumable/mod.rs)

The assumption type explicitly encodes an assumption in a textual description and an eval function that takes a slice of
numerical values as an argument and returns a boolean for which the assumption holds on the given data. Implementing the
assumable trait adds functionality to test the assumption, check if it has already been tested, and if it has already
been valid.

Multiple assumptions are represented in standard collections (array, map, vector), which are extended with
the default implementation of the [AssumableReasoning](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/protocols/assumable/mod.rs) trait
that adds aggregating functionality i.e. how many of the assumptions are valid or tested.

### Observation

Once a set of assumptions has been identified and encoded, the next question is whether some or all assumptions exist in
the data. Deep causality implements observations in the following way:

Traits:

* [Observable](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/protocols/observable/mod.rs)
* [ObservableReasoning](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/protocols/observable/mod.rs)

Extensions:

* [Observable Array](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/extensions/observable/mod.rs)
* [Observable Map](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/extensions/observable/mod.rs)
* [Observable Vector](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/extensions/observable/mod.rs)

Types:

* [Observation](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/types/reasoning_types/observable/observation.rs)

An observation defines an observed value i.e., a measured metric and an observed effect.
The idea is to hold the observation immutable and invariant after the observation.
The assumable protocol then adds a default implementation to determine if a target effect
has been observed relative to the observation in excess of a threshold. Both, the target effect and
target threshold are given as a parameter because it may happen that certain effects may only become
detectable when adjusting the threshold.

Multiple observations are stored in standard collections (array, map, vector) which are extended with
[ObservableReasoning](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/protocols/observable/mod.rs) to identify the number or percent of
observations vs non-observations.

## Control of confounding

Confounding refers to the presence of unobserved causes of two or more variables. In the presence of
confounding, false conclusions can easily be drawn from data. Existing approaches address confounding
through either graphical modeling using the back-door technique or through the application of the do-calculus.
Both methodologies are effective in de-confounding causality models.

Deep Causality adds the concept of inference to discern whether the stipulated cause actually occurs
in tandem with the expected observation to decide whether one can infer the expected effect from that cause.

Traits:

* [Inferable](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/protocols/inferable/mod.rs)
* [InferableReasoning](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/protocols/inferable/mod.rs)

Extensions:

* [Inferable Array](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/extensions/inferable/mod.rs)
* [Inferable Map](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/extensions/inferable/mod.rs)
* [Inferable Vector](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/extensions/inferable/mod.rs)

Types:

* [Inference](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/types/reasoning_types/inferable/inference.rs)

Deep Causality addresses confounding via a third approach called conjoint delta. For a single observation, the conjoint
delta refers to the difference between an expected and observed effect normalized to one. If the expected effect is
present, the conjoint delta of a singular observation is zero because
the stipulated cause occurs together with the expected effect. Conversely, if the cause is present, but the expected
effect is missing, the conjoint delta is one because the cause does not explain the observed effect.

For a collection of observations, the conjoint delta refers to the difference (delta) between all observations and those
where the effect is not observed together with the cause, again normalized to one. For example, suppose a set of ten
observations contains eight observations where the expected effect occurs. In that case, the conjoint delta is .2 or
20%, meaning in 20% of the observed data, an unknown or unobserved cause must cause the observed effect.

In practice, however, one might try to minimize the conjoint delta to reign in confounding. Still, in many applications,
eliminating confounding might not be feasible. Instead, it's sensible to establish a certain threshold at which
reasoning and inference can proceed with the understanding that the conjoint delta captures everything not explained by
the causal model.

## Counterfactuals

Counterfactual analysis deals with behavior of specific individuals, identified by a distinct set of characteristics.
Counterfactuals analysis falls broadly into two categories; the process of determining analytically if the probability
of a factual sentence is estimable from experimental or observational studies, or combination thereof. And, second,
counterfactual questions concerning “causes of effects” as opposed to effects of causes. Lets suppose Joe died
in the water during a swimming exercise, with his death as factual effect, a counterfactual question would be,
would Joe be alive if he would have not taken part of the swimming exercise? In other words,
was the swimming exercise a cause of Joe’s death?

For the first category of counterfactuals, Deep Causality provides the inferable protocol as an alternative to the
established methods to determine if a a factual sentence is estimable from experimental or observational data.

For the second category, however, Deep Causality does not provide a solution as this topic is still subject
to ongoing research.

## Mediation Analysis and the Assessment of Direct and Indirect Effects

Mediation analysis concerns the mechanisms that transmit changes from a cause to its effects.
The identification of such intermediate mechanism is essential for generating explanations.
Typical queries answerable by this analysis are: What fraction of the effect of X on Y is mediated by variable Z.

Deep Causality offers a novel mechanism of mediation analysis called conjoint delta as explained in the previous section
about confounding. The difference between one and the conjoint delta quantifies the exact direct contribution of a cause
to an effect. That means, for a multi-causality, it is decidable how much each cause contributes to the observed effect.
Furthermore, in a multi layer causality, sectional conjoint-delta refers to the relative indirect impact of a cause
on the final effect.

## External Validity and Sample Selection Bias

The validity of every experimental study is challenged by disparities between the experimental and implementation
setups. A machine trained in one environment cannot be expected to perform well when environmental conditions change,
unless the changes are localized and identified. This problem, and its various manifestations are well recognized.

Deep Causality addresses this problem with the encoding of explicit assumption, as elaborated in section 1.

A few implications follow from causality models that are conditional on explicit assumptions:

1) Applicability of a model to a new dataset only requires testing the assumptions required by the model.
2) The relative impact of a change of context can be assessed relative to how the change affects the models assumptions.
3) Transfer learning, from one domain to another, becomes easier in the sense transfer is fundamentally possible
   whenever the assumptions hold true.

In terms of selection bias, the causal model usually is is free of a bias unless explicitly stated in the assumptions.

Currently, Deep Causality cannot verify whether a causal function depends on unstated assumptions but rather relies
on the model designer to make any assumption explicit. This is a tradeoff that follows from the decision to
encode the causal relation as a generic function, which cannot easily be verified w.r.t to implicit assumptions.
This is one of the areas where more work is needed.

## Missing Data

Problems of missing data plague every science project. Respondents do not answer every question,
sensors fade, and patients often drop from a clinical study. The rich literature provides multiple
techniques of dealing with missing data, often applying techniques such as substituting missing values
either with an average value or a certain default value. These techniques assume an unknown causal process
of data generation and therefore an indiscriminate handling of missing data is applied. This is a direct result
of the model blind paradigm prevalent in all statistic based machine learning methods.

Deep Causality, similar to related work, allows the modeling of the data generation process as
a separate causal model with the implication that, within limits, causal relationships can be recovered from incomplete
data.

# Causal Structure

DeepCausality uses the causaloid as its central structure, an idea
borrowed from a [novel causal concept](https://arxiv.org/abs/gr-qc/0608043) pioneered
by [Lucien Hardy](https://perimeterinstitute.ca/people/lucien-hardy) at the [Perimeter Institute](https://perimeterinstitute.ca/)
of [theoretical physics](https://perimeterinstitute.ca/why-theoretical-physics).


## The causaloid

The causaloid encodes a causal relation as a causal function that maps input data to an output decision determining
whether, on the input data, the causal relation, encoded as a function, holds.
Therefore, the causaloid folds cause and effect into one single entity. Causaloids are structurally invariant and,
therefore, temporarily stationary. In the event of a temporal shift, only the order of causal evaluation may shift
following the temporary shift. Still, the causal structure remains intact because there is no conceptual distinction
between cause and effect anymore. Furthermore, algebraic types applied to causaloids enable recursive causal structures.

Traits:

* [Causable](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/protocols/causable/mod.rs)
* [CausableReasoning](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/protocols/causable/mod.rs)

Extensions:

* [Causable Array](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/extensions/causable/mod.rs)
* [Causable Map](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/extensions/causable/mod.rs)
* [Causable Vector](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/src/extensions/causable/mod.rs)

Types:

* [Causaloid](https://github.com/deepcausality-rs/deep_causality/blob/main/deep_causality/src/types/reasoning_types/causable/causaloid.rs)
* [CausaloidGraph](https://github.com/deepcausality-rs/deep_causality/blob/main/deep_causality/src/types/reasoning_types/causable/causaloid_graph.rs)


## Recursive causal data-structures

DeepCausality scales from simple to advanced use cases with complex contextual requirements. To take the idea of
scalable complexity one step further, DeepCausality also offers scalable causal data structure. Fundamentally, a causal
data structure augments an existing data structure with abilities to conduct causal reasoning. Not everybody needs a 4D
hypergraph to solve common problems. Therefore, DeepCausality provides a set of causal data structures that scale causal
reasoning from simple to complex structures:

* Causal Array
* Causal Vector
* Causal HashMap
* Causaloid Graph

The causaloid, however, can be a singleton, a collection, or a graph. The causaloid-graph, however, is a hypergraph with
each node being a causaloid. This recursive structure means a sub-graph can be encapsulated as a causaloid which then
becomes a node of a graph. A HashMap of causes can be encapsulated as a causaloid and embedded into the same graph.
Then, the entire causaloid-graph can be analyzed in a variety of ways, for example:

* Reason over the entire graph
* Reason only over a specific causaloid
* Reason over all causaloid between a start and stop causaloid.
* Reason over the shortest path between two causaloid.

# Context

DeepCausality enables context awareness causality reason across data-like, time-like, space-like, and spacetime-like
entities stored within (multiple) context-hyper-graphs. Fundamentally, this allows scalable contextualization up to four
dimensions.

## Data Context

The most basic form of contextualization adds more data to a model. For example, when modeling GDP for any country,
commodity prices such as oil play a significant role in addition to several national factors. Conventionally, the GDP
model separates internal from external factors to isolate systematic risk. DeepCausality solves this by adding two
distinct data contexts, one for national data, i.e., population growth & manufacturing output, and a second context for
data from external factors, i.e., standard crude oil price.
In a more realistic context, temporal structures become a significant contributing factor. For example, when modeling
volatile markets, the current price action usually operates within a particular micro and macro temporal structure,
often represented as the daily and weekly pivot points and, in some cases, the annual low/high values. For most days,
current price action operates within the temporal microstructure. Still, if, for any reason, the current price
approaches the boundaries set by the relative macro structure, extreme volatility follows.

DeepCausality solves this by adding multiple micro and macro temporal data contexts that provide the model access to
anchoring points representative of the selected temporal resolution. Therefore, modeling market volatility relative to
its intrinsic context becomes relatively easy. Furthermore, for synthetic instruments such as Future Spreads, the
approach can be extended to adding multiple contexts for each future contract used in the spread.

## Temporal and Spatial Context

In a more advanced context, considering temporal and spatial changes becomes a requirement. There is a clear distinction
between stationary context and non-stationary context. The former requires no further adjustment, whereas the latter
does. In the first scenario, consider a sensor array mounted to a drone swarm. In this case, the data stream from the
sensors is subject to positional changes over time because of the drone movement. Note this is a stationary change since
the drone swarm cannot accelerate or move beyond certain limits, so it remains subject to Newtonian physics. Therefore,
the data stream requires contextualization relative to the tempo-spatial position of the drone swarm to provide
meaningful information to the model.

DeepCausality solves this by adding a temporal master context that structures time as a 4-dimensional hyper-graph where
each node encodes a unit of time (A tempoid) which itself contains a link to a sub-node that encodes spatial
information (A spaceoid), which then links to the actual chunk of data through a data object (A dataoid).
That way, multiple drones can stream multiple data to update a 4D context graph that informs the model
and allows for real-time monitoring of complex tempo-spatial patterns.

## Adjustable Temporal and Spatial Context

For non-stationary tempo-spatial processes subject to non-Newtonian changes, the general problem arises that the entire
4D tempo-spatial context structure becomes subject to external changes. This is the case when modeling control systems
subjected to gravitational forces deviating from the terrestrial standard of 9.807 m/s². When that happens, the entire
4D context requires adjustment, for example, when modeling inert navigation for outer-space travel and certainly when
modeling any moving object nearby a black hole.

DeepCausality solves this by activating an optional adjustment mechanism that allows to adjustment of the value of each
element in a context graph before evaluating the attached model. As a result, after primary measurement updated a
context graph, a secondary process may estimate the relative adjustment for time dilation, which results in one of two
scenarios. One, adjustment for all measurements remains constant. In this case, adjusting all measurements might be more
sensible before updating the context graph.
In the second scenario, there is a gradual adjustment for different measurements. Often, this requires the formulation
of an adjustment matrix. The matrix can already be attached to each element of the context graph but may require
periodic updates depending on the change of gravitational force. In this case, the secondary process calculates the new
adjustment matrix for each element of the context graph and then calls the adjustment of the entire context graph,
ensuring all measurements in the context get adjusted relative to the new adjustment matrix that represents the impact
of gravitational change.

The exact adjustment for temporal spatial data depends on the actual structure of the representative structure.
Theoretically, a tensor would be the preferred structure, allowing for multi-dimensional adjustment representation. In
practice, however, tensors occur a non-trivial overhead leading to a non-trivial performance penalty.
Therefore, DeepCausality brings a custom data structure called a Grid that is indexed with a variable PointIndex. The
difference to a tensor is that a tensor remains parametric over N dimensions, thus requiring a complex object
representation. In contrast, a Grid is limited to low dimensions (1 to 4), allowing representations as a scalar, vector,
or matrix, representing all types represented as a static fixed-size array. Fixed-sized arrays allow for several
compiler optimizations, including the complete removal of runtime array boundary checks, since all structural parameters
are known upfront, providing a significant performance boost over tensors. Performance is critical because context
hyper-graphs may grow large with millions of nodes, and obviously, one wants the fastest possible global adjustment in
those cases.
