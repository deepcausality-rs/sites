---
author: Marvin Hansen
title: "Philosophy"
date: 2025-05-03
draft: false
---

[//]: # (SPDX-License-Identifier: CC-BY-4.0)

{{< toc >}}

## Overview: The Effect Propagation Process

The study of causality dates back to Aristotle and was later formalized in its commonly known form by Seneca. Seneca’s assumption of a background space and time was later challenged by relationalists like Leibniz and critiqued scientifically by Russell.

However, contemporary research in quantum gravity suggests that spacetime itself might be emergent from the quantum level and causal structures can be indefinite, thus fundamentally challenging the assumption of a background spacetime. While these concepts may sound specific to quantum physics, the underlying problem of a fixed spacetime assumption's conflict with representing causality in non-linear structures also occurs in advanced system engineering. Three specific problems arise in advanced system engineering that previous methods of causality cannot address anymore: non-Euclidean data representation, non-linear time representation, and emerging causality.

In response, the author introduces the "Effect Propagation Process" (EPP) framework to address these new challenges. The EPP departs from the classical notion of time-linear causality, borrows new concepts from physics, and proposes a view of  causality as a spacetime-agnostic continuous effect propagation process.

The Effect Propagation Process offers a unified philosophical framework of causality that remains compatible with classical causality and conceptually congruent with physics theories of quantum gravity.

Philosophically, the Effect Propagation Process proposes a different epistemology of causality by shifting the focus of causal knowledge derived from observing event sequences to deriving the dynamics of the underlying generative process. The new epistemology lays the groundwork for analyzing the dynamic emergence of causality that results from the application of the EPP.

Practical application of the Effect Propagation Process enables the handling of uncertainties, causal reasoning over non-Euclidean data, and non-linear complex feedback loops in dynamic systems.

The Effect Propagation Process does not seek to replace the classical notion of causality; instead it seeks to advance and generalize the concept of causality to address the new challenges of causal inference over non-Euclidean data, non-linear temporal structures, and handling emergent causality in dynamic systems.

## Motivation

What warrants the development of a new philosophy of causality?

The pre-existing philosophy of causality served mankind for millennia, and one might be tempted to conclude that this is all there is to know about cause and effect. However, the origin of the Effect Propagation Process (EPP) did not start in philosophy, but in three distinct problems. The first problem is related to non-Euclidean data representation, the second problem is rooted in causal inference over non-linear time representations, and the third in handling dynamic causal structures.

### Non-Euclidean representation

The first problem applies equally to computational causality and deep learning; therefore, it is best illustrated with familiar  large language models. Language embeddings remain foundational to contemporary large language models (LLMs), but these require a reduction into a vector space because many prevalent LLM architectures operate efficiently in vector spaces, thus making the reduction from non-Euclidean realms (language) into a Euclidean representation (Vector space) mandatory. Instead of advancing LLM architectures to natively handle non-Euclidean representations, the industry has focused on leveraging Vector databases for storing and retrieving embeddings derived from LLMs. Graph neural networks operate on non-Euclidean spaces, but as these are not yet commonly adopted as core components in mainstream LLM architectures, the problem prevails.

### Non-linear time

However, when generalizing space beyond Euclidean, then the second problem emerges: how to represent time? More profoundly, can we separate time and space from data? Out of this insight, the idea emerged to separate space, time, and data into a separate context usable by multiple models. As space and time were elevated from an implicit background into an explicit first-class context representation, then moving beyond correlation towards causality became the next obvious step. At this moment, a profound problem emerged: When space is non-Euclidean, and time might not be a simple linear progression, then how do we establish a causal relationship?

As it turned out, establishing a clear causal relationship became problematic within the classical definition of causality, which fundamentally relies on a linear time-asymmetric ordering (cause preceding effect) within its assumed background spacetime.

One might challenge the presumption of non-linear time progression, but in complex systems with dynamic feedback loops, it’s perfectly possible to see context structures that entail non-linear time regions.

Non-linear time regions can occur when the background time is represented as a temporal hypergraph that holds multiple time resolutions simultaneously. The simultaneous presence of time units at different scales breaks the simple time-linear assumption (all time has the same unit, and moves therefore at the same rate) that computational causality tools commonly make.

Furthermore, in a temporal hypergraph, the unit of time is scale dependent which means in order to compare temporal values one must consider the scale to make a valid comparison between equally scaled values (hour X compared to hour Y).

Less obvious, a temporal hypergraph, by design, holds all past and present temporal values simultaneously within its structure. This co-existence of multiple temporal points simplifies non-trivial temporal arithmetic over hetero-scaled time units, yet it imposes a vexing problem: How do you know if a time value in a node of the graph is current or past?

The problem is non-trivial because, as time progresses, the engulfing context engine continually generates the non-Euclidean temporal hypergraph representation with the implication that, at one lookup, the value of a temporal node is current, but at the next one, it might be past; however, the exact temporal distance at which a “present” value becomes “past” depends on the node's time scale. A node holding a temporal value “hour” will be valid for 60 minutes; that means a lookup every ten minutes will yield the current hour 6 times, but handling the seventh lookup leads to a fundamental design decision that illustrates the implied complexity.

A “dynamic-position” design means, when a new hour starts, a new node will be added; therefore, the seventh lookup returns a past value. By implication, the index of the new node needs to be looked up to retrieve the value of the new current hour. Therefore, a “dynamic-position” design requires a dynamic index to locate current values.

A “static-position” design means, when a new hour starts, the previous current value will be overwritten with the understanding that the seventh lookup returns the new current value. By implication, the index of the current value always remains static. Therefore, a “static-position” design requires a fixed index, i.e., a lookup table to locate current values.

Use cases exist for both scenarios and in practice, temporal hypergraphs use a mixture of static and dynamic positioning to handle different types of relative values, e.g., current day, last year, next hour, and similar..

Exacerbating the problem further, feedback loops across different time scales using different relative values may dynamically modify the temporal hypergraph itself to capture non-regular observations or to add estimations at future time values that have not yet occurred.   
At this point, it becomes abundantly clear that the assumption of a simple, unidirectional linear temporal order required for establishing cause-and-effect becomes untenable.

At the same time, causal relations remain valid in those non-linear regions. Additionally, the designation of a cause purely based on strict temporal order feels arbitrary in a temporal hypergraph in which past, present, and estimated future temporal values across multiple time scales all exist simultaneously. Regardless of static or dynamic location of relative values, the definition of causality had to evolve to match the reality of modeling causal structures across complex multimodal hypergraphs.

### No a-priori causal structures

When modeling dynamic feedback loops across different time scales, the third problem emerges eventually: Not all causal structures are known upfront. There are cases where the causal structure emerges from the prevalent context predominantly in response to a change in externalities. For example, in the financial industry, a shifting volume imbalance indicates an emerging regime change. The exact cause for the shifting volume imbalance can be attributed to externalities such as breaking news. However, in absence of internal references, the subsequent  causal structure emerges as part of the unfolding regime change. There is no possible way to know the new structure upfront therefore, it cannot reliably be modeled ahead of time. Likewise, in correlation-based methods, a similar phenomenon unfolds because, in absence of internal references, the deep learning model cannot predict correctly anymore because data during an emerging regime change fall outside its training data distribution. The mechanism is different, but the outcome is the same: that previously reliable models crater in novel situations.

The previously identified limitation of temporal order directly applies to dynamic regime changes because, if the new causal structure has not yet emerged, how can we know its temporal structure beforehand?

In short, we cannot know reliably anything about emerging causality up to the moment it emerges.

These three problems, non-Euclidean representation, non-linear temporal structures, and emerging causality deeply interrelate with each other, thus defy overly simplistic solutions. For example, advanced graph neural networks work on non-Euclidean data representation, but fail on non-linear temporal structures. One might be tempted to build non-linear-time graph neural networks, but this does not address the problem of non-Euclidean data representation and emerging causality. There is research to combine methods from computational causality with deep learning, but these approaches are focused on non-Euclidean representation without integrating the challenges of non-linear temporality and emergent causal logic.


### Why Existing Methods Struggle?


The established methods of causal inference remain important milestones and they work well within their defined domain; they were not architected for the challenges imposed by handling non-Euclidean representation, non-linear temporal structures, and emerging causality. Therefore, the subsequent analysis does not criticize any of the existing methods, as they remain valid. Instead, the analysis states how the underlying assumption(s) of each method conflict with the previously established problems.

#### Granger Causality:

Granger Causality[^12] is used for time-series data where past values of one time-series are used to predict values of another time-series. In a strict sense, Granger Causality tests if one variable (say X) predicts another variable (Y) through a series of t-tests and F-tests on lagged values of variable X.

**Assumptions:**

Granger causality assumes a stable causal structure and a linear, uniform time representation with consistent intervals.


**Implications:**

* Non-Linear Time: Granger causality cannot handle non-linear time representation
* Non-Euclidean Representation: Granger causality operates on time-series values within a Euclidean representation. It cannot be applied to a non-Euclidean representation.
* Emergent Causality: Because of the assumption of a stable causal structure, Granger causality cannot operate on emergent causal structures.

**Pearl's Causal DAGs and Structural Causal Models (SCMs):**

Judea Pearl pioneered the formalization of causality that underpins the majority of contemporary methods of computational causality. The framework of Structural Causal Models (SCMs)[^13] rests upon the assumptions of Directed Acyclic Graphs (DAGs).

**Assumptions:**

Pearl's DAG framework is exceptionally powerful for reasoning about interventions given a known or discovered causal model.

Pearl's causal DAG assumes:
* Acyclicity (DAGs): Causal relationships are acyclical in a DAG.
* Static Causal Structure: The causal graph, once defined, is assumed to be static.
* Fixed background spacetime: Variables in the DAG are assumed to be embedded within a fixed background spacetime.


**Implications:**

* Non-Linear Time: The acyclical assumption explicitly prohibits feedback loops and the fixed background spacetime assumption prevents any form of non-linear time.
* Non-Euclidean Representation: The DAG structure could potentially allow for non-Euclidean representation, but existing tooling assumes Euclidean structures and thus does not allow non-Euclidean representation
* Emergent Causality: The assumption of static causal structure prevents any handling of causal emergence.

**Rubin causal model (RCM)**

The Rubin causal model[^14] (RCM) is a statistical framework for estimating causal effects by comparing potential outcomes under different treatment assignments.

**Assumptions:**

RCM assumes stable units, no interference between units (SUTVA), and that treatment assignment is ignorable conditional on observed covariates. RCM also assumes a stable causal structure and a fixed background spacetime.

**Implications:**

* Non-Linear Time: RCM is not designed to handle non-linear or multi-scale time representation.
* Non-Euclidean Representation: RCM is designed for variables representing treatments, outcomes, and covariates, without any mechanism for complex relational types. Therefore, RCM cannot infer across non-Euclidean data representations.
* Emergent Causality: RCM estimates effects within a stable causal structure and therefore cannot handle emergent causality.

**Dynamic Bayesian Networks:**
Dynamic Bayesian Networks[^15] (DBN) extend Bayesian Networks to model temporal processes by defining transition probabilities between states.

**Assumptions:**

Dynamic Bayesian Networks, similar to Granger causality, require a linear and uniform time representation. DBNs model changes in the state of variables over time according to a fixed probabilistic causal structure assumed to be static.

**Implications:**

* Non-Linear Time: DBN cannot handle non-linear time.
* Non-Euclidean Representation: DBNs reason over probabilities of state transition, not non-Euclidean space itself.
* Emergent Causality: DBNs assume a static causal structure and thus cannot handle emergent causality

As stated earlier, all these methods remain valid in their respective domains. Granger causality remains vital in time series forecasting. Pearl’s causal DAG remains relevant, among others, in empirical healthcare. Dynamic Bayesian Networks find applications in healthcare, data mining, and robotics. This analysis, however, shows why each method cannot be applied to the previously established problems. It is important to recognize that there is no shortcoming in any particular methodology since each one remains valid and sound. Instead, as Russell indicated, there is an inadequacy in the classical interpretation of causality itself that warrants fundamental rethinking.

### Why a new philosophy of causality?

Upon studying Hardy’s work on causality for quantum gravity[^7], the author noticed the clear emphasis on operational causality; a sensible choice given the entire field of quantum gravity can be best described as work in progress.

However, the lack of a philosophical foundation became apparent when attempting to combine Hardy’s unified causality with non-linear time, and uniform context over Euclidean and non-Euclidean structures: There was no “big idea” that would help to bring everything together. However, a new idea was much needed to solve the vexing problem of handling causal inference across complex hypergraph structures let alone tackling emergent causality.

The presented Effect Propagation Process closes this foundational gap and brings together previously disjoint ideas into one coherent philosophical framework of causality that elegantly solves the non-Euclidean representation problem by defining causality as a fundamentally spacetime-agnostic process.

It is important to understand that, without something similar to EPP, conventional causality cannot work across complex hypergraph structures and solve new challenges of causal inference over non-Euclidean data, non-linear temporal structures, and handling emergent causality in dynamic systems. The foundational work inspired by Quantum Gravity is a direct testament to the problem complexity that EPP solves.

## History of Causality

Plato is believed to be the first who explored the cause (aitia) in the book of Timaeus (c 360 BC). In it, Plato stipulates that multiple indispensable factors, the model, the maker (Demiurge), the material, and the space (receptacle), explain how the physical world with all the things in it are made[^1]. Aristotle (c 350 BC) formalized the notion of causality in his Metaphysics[^2] with the "Four Causes”[^3]. These are:

1) The material cause or that which is given in reply to the question “What is it made out of?”

2) The formal cause or that which is given in reply to the question "What is it?”. What is singled out in the answer is the essence of the what-it-is-to-be something.

3) The efficient cause or that which is given in reply to the question: “Where does change (or motion) come from?”. What is singled out in the answer is the whence of change (or motion).

4) The final cause, the end purpose, is given in reply to the question: “What is its good?”. What is singled out in the answer is that for the sake of which something is done or takes place.

Seneca (c 56 AD) argues in letter 65[^4] that cause and effect operate within a stage (space) and follow an order (time). Remove the stage or the order, and the conventional understanding of 'making something' or 'causing something' breaks down. His argument highlights time and space as indispensable prerequisites for classical causality. His focus on space and time as necessary conditions served as a precursor for physical concepts treating spacetime as a background for causal processes.

The idea of space and time as a background for causality, however, did not remain unchallenged. Gottfried Wilhelm Leibniz (1646-1716) rejected the concept of absolute space and absolute time as independent, fundamental constructs. Instead, Leibniz proposed[^9] a relational view in which space is the simultaneous relation of coexisting things and time is the relational order of successive things.
Through rigorous first-principles analysis, Leibniz argued that the concept of absolute space and time was logically untenable.
His relational perspective offered a significant alternative to the preeminent Newtonian worldview of his time.

Albert Einstein (1879 - 1955) departed from Newtonian physics through his theory of General Relativity[^5] (GR) in which he established that space and time are one manifold, spacetime, that is bent by gravitational influence from large masses. General Relativity preserves the prerequisite of a spatiotemporal context for causality, echoing Seneca's key insight. However, the notion of dynamic spacetime requires a dynamic view of causality to fit into the dynamic spacetime manifold.

Bertrand Russell (1872 - 1970) observed that successful physics has its roots in sophisticated, law-based descriptions of how a system evolves dynamically. In modern physics, the focus is on the state of a system (e.g., position, velocity, field strength across space) and how that entire state evolves continuously and dynamically. Therefore, for Russell, the idea of classical  causality, a strict happen-before relation, does not match the reality of modern physics anymore. Consequently, Russell wrote in his 1912 essay "On the Notion of Cause"[^6]:

> "The law of causality, [...], is a relic of a bygone age"
>  Bertrand Russell

Many modern physics laws are time symmetric, and that means if state S1 at time t1 is related to state S2 at time t2 by a law, it's equally true that state S2 at time t2 is related to state S1 at time t1. This relationship isn't a simple, linear, one-way street from a necessary "cause" to a dependent "effect." Knowing the state at any time allows you to calculate the state at any other time, past or future. Therefore, which state is the "cause" and which one is the "effect" becomes arbitrary.

Russell was not opposed to causality itself; instead his primary argument was that the traditional philosophical interpretation of causality as a fundamental, temporally asymmetric, and directed link is not what he observed in physics. His critique resonates with challenges encountered in contemporary quantum research.

## The impact of Quantum Gravity on Causality

Quantum Field Theory[^10] (QFT) stands out as one of the most rigorously tested theories with unparalleled predictive accuracy in the history of science. QFT predictions in Quantum Electrodynamics have been experimentally verified up to an astonishing accuracy of one part in a billion or better. This experimental success proves that the underlying concepts such as the primacy of fields, the emergence of particles, and inherent indeterminacy used across different areas of QFT indeed result in demonstrably more accurate models.

The physics standard model, built on top of QFT, despite being one of the most successful theories of all time, accurately describes three of the four known fundamental forces: electromagnetism, the strong nuclear force, and the weak nuclear force. Notably absent remains gravity due to complex discrepancies between Einstein’s (pre-quantum) theory of relativity and Quantum Field Theory. It is important to point out that General Relativity in itself is successful in the sense of high accuracy and strong predictive power, albeit in a non-quantum realm.

The unification of general relativity with quantum field theory would complete the standard physics model, but doing so faces a non-trivial impasse, as Lucian Hardy[^7] formulated: “Quantum theory is a probabilistic theory with fixed causal structure. General relativity is a deterministic theory but where the causal structure is dynamic.” Furthermore, the emergence of Quantum Gravity directly challenges the traditional separation of causality through the introduction of indefinite causal order with time symmetry[^8].

Indefinite causal order means the order of causal events is not fixed. It might be that A happens before B, or that B happens before A, or a quantum superposition where both orders (A before B, and B before A) coexist simultaneously.

Time symmetry or time reversal symmetry refers to the theoretical symmetry of physical laws under inverted time. That means, the laws of physics remain the same when time is reversed, a property known as T-symmetry. Many laws of physics are formulated in terms of time symmetry, thus allowing to calculate previous system states in time using the same set of equations. For example, laws like Newtonian mechanics, Maxwell's equations of electromagnetism, or Einstein's equations for General Relativity are T-symmetric.

The fundamental dynamical laws of quantum physics (excluding the weak nuclear force) are accepted as T-symmetric. However, the transition of a quantum state from a probabilistic T-symmetric state into a definite and time-asymmetric state, while observed, isn't well understood and subject to ongoing research in the field of quantum measurement.

Quantum superposition of states, on the other hand, is extremely well-observed, well-documented, and as a result, it is accepted as a fundamental building block of quantum physics. Quantum superposition inspires the exploration of concepts like indefinite causal structures in theories aiming to unify quantum mechanics and gravity.

Therefore, the classical conceptualization of cause and effect embedded into a background spacetime might not yet exist at the fundamental level of quantum gravity. In Quantum Gravity, space and time are not external conditions, but potential emergent properties of the internal quantum structure itself.

The problem is no longer whether spacetime is static or dynamic, but that spacetime itself emerges from the quantum level and thus positions itself as a higher-order effect of a generative process.

> Instead of asking "Where and When does this cause operate?", quantum gravity asks "What is the underlying process from which the notions of 'where' and 'when', and thus causal order, emerge?”

Russell saw physics moving towards laws governing states, a view echoed in quantum gravity's search for fundamental rules governing the structure from which spacetime and causal order emerge. At this stage, the understanding of causality evolved from a structure that required the existence of space towards a dynamic generative process from which causality emerges. This emergent causality does not rely on a pre-existing spacetime, but is grounded in a more fundamental level of reality—a set of underlying rules (i.e., conceptualized as a 'generating function') that determine the fundamental manifestation of spatiotemporal properties.

If the 'output' in terms of emergent properties doesn’t include states that resemble classical spacetime, then the conditions Seneca deemed necessary for causality would not appear. From the quantum perspective, 'space and time' that Seneca identified as necessary conditions are not fundamental inputs to causality any longer, but are outputs from the underlying quantum generative process.

The conceptualization of this fundamental level as a "generating function" captures the idea of a quantum process from which the necessary condition of classical causality's spatiotemporal structure arises. It's a shift from asking "What causes X given spacetime?" to "What process generates spacetime (and thus enables X to be caused)?".

## Causality as Effect Propagation Process

The notion of a quantum generative process that underlies the fabric of spacetime leads to the implication that causality has to evolve beyond the strict “before-after” relation towards a spacetime-agnostic view. When removing time from causality, it is indeed no longer possible to discern cause from effect because, in the absence of time, there is no “happen-before” relation any longer, and therefore, the designation of cause or effect indeed becomes arbitrary, just as Russell hinted at earlier on.
When removing space from causality, the location of a cause or effect in space is not possible anymore because space itself is no longer available.

> The absence of spacetime raises the question:
> What is the essence of causality?

Logically, the answer comes in three parts:

1) Causality is a process.\
2) Causality deals with effects.\
3) Causality describes how effects propagate.

The first one is self-explanatory because causality occurs in dynamic systems that change and therefore, causality must be a process.

The second one is less obvious, because one might think that causality is all about the “cause” that brings the effects into existence. However, let’s think the other way around: We know that X is the cause of effect E, because E happens when X happens and because E does not happen when X does not happen either. Therefore, we can describe a cause in terms of its effects. Therefore, it is true that causality deals with effects.

The third one, effect propagation, stretches the imagination and is less obvious. When we rewrite the previous definition of classical causality in terms of effect propagation, we see that there is no loss of information:

> If X happens, then its effect propagates to Effect E.
> If X does not happen, then its effect does not propagate to Effect E.

In this definition, X does not have a designated label and instead is described in terms of its emitting effect. Therefore, X can be seen as a preceding effect, which then propagates its effect further. Therefore, causality becomes an effect propagation process.

The effect propagation process definition is more general and treats the classical happen-before definition of causality as a specialized derived form. When you designate the preceding effect to be a “cause”, then you can rewrite the general definition back into the classical definition thus the general and the specialized definition of causality remain congruent. This detail is important because the generalized effect propagation process definition would not be sound if it were unable to express a specialized variation. Framing causality as an effect propagation process leads to several implications:


**Focus on effect propagation:**

In EPP,'effect propagation' denotes the operation of a specific, definable mechanism (via the causaloid) that links states through the underlying fabric regardless of how that fabric might be defined.

The first part, the causaloid, operationalizes effect transfer within a system without relying on any metaphysical causal power. The effect transfer encapsulated in the causaloid is  intrinsic to its mechanistic definition. The identification of relevant causaloids requires explicit modeling and hypothesis testing or (future) discovery processes. EPP provides the formatl structure for representation of Causeloids once discovered.

The second part, the non-defined fabric, through which effects propagate, serves the purpose of externalizing the fabric as a specific, definable context. Instead of assuming an implicit background spacetime, the EPP externalizes the fabric through which effects propagate as a specific context that is defined by a different generative function.
Therefore, EPP fundamentally moves away from invoking a metaphysical causal power towards definable, testable, and verifiable functions (Causaloids) that define the functional relationships describing how a system changes if these functions   are active.

**Operational generative function:**

In EPP, the aforementioned generative function is strictly operational for modeling dynamic systems. EPP, as a philosophical framework, does not entail ontological aspirations to specify the exact ultimate generative function of the universe and instead leaves these questions to fundamental theories of physics. Instead, the generative function serves as a conceptual necessity to get around the static limitations implied in the classical definition of causality.

In practical applications of EPP, the underlying structure refers to the explicit model of the systems fundamental components which then serves as the operational fabric through which effects propagates. Whether this explicit model is static, dynamic, or emergent is secondary for the application of EPP.

**Detachment from fixed spacetime:**

In quantum gravity, where spacetime geometry might be in a superposition or non-existent at the fundamental level, "propagation" isn't a movement along a geodesic in a manifold. It's the propagation of effects through a network of states or elements defined by the fundamental structure. This is a prerequisite for handling indefinite causal order.

**Handling indefinite causal order:**

In situations where the causal structure itself is indefinite (a superposition on the quantum level, a not-yet-emerged state in GR), "effect propagation" can be understood as the influence propagating through a superposition of possible pathways through the fundamental structure. The "effect" isn't tied to a single, definite causal link but is a result of the propagation through all possible pathways.

**Alignment with emergence:**

When the fundamental structure gives rise to classical spacetime, this fundamental "effect propagation" would then manifest as propagation through spacetime (e.g., waves, particles, forces traveling from one spatiotemporal point to another). Classical cause-and-effect becomes a macroscopic view of this underlying process. This results from the logical congruence between the general effect propagation process definition and the classical definition of causality.

In the Effect Propagation Process framework, due to the detachment from a fixed spacetime, this fundamental temporal order is absent. Consequently, the entire classical concept of causality, where a cause must happen before its effect, can no longer be fundamentally established. The distinction between a definitive 'Cause' and a definitive 'Effect' becomes untenable as Russell foresaw. When the separation between cause and effect becomes untenable, then the obvious question arises: why even preserve an untenable separation?

Therefore, the Effect Propagation Process framework adopts the causaloid, a uniform entity proposed by Hardy[^7], that merges the ‘cause' and 'effect' into one entity. Instead of dealing with two nearly identical concepts discernible from each other by temporal order, the causaloid is one concept that defines causality in terms of its effect transfer without presupposing a fixed spacetime background[^7].

In the post-quantum context, the term "propagation" does not imply movement through a pre-existing space or time in the classical sense. Instead, it refers to the fundamental process by which an effect is transferred within the underlying structure of reality itself. This fundamental process is what gives rise to the appearance of propagation through spacetime in the classical view.

Furthermore, while classical causality relies on a definite temporal order, the Effect Propagation Process treats temporal order as an emergent property, arising from the fundamental process itself.

While the Effect Propagation Process involves the transfer of effects within the fundamental structure, it is crucial to distinguish this from mere accidental correlation. The process reflects the fundamental way the underlying structure of reality establishes dependencies between its components and how it is gives rise to the non-accidental relationships we recognize as observed causal relations.

This fundamental determination, rather than simple co-occurrence, is what the "Effect Propagation Process" captures at the deepest level. Consequently, causality is understood as an effect propagation process that emerges from the fundamental structure or set of rules (akin to a generating function) from which spatiotemporal relationships emerge.

This philosophical concept of the Effect Propagation Process finds support in physical theories that propose fundamental structures underlying spacetime, such as Causal Set Theory, and generalizes the idea of effect transfer present in Quantum Field Theory.

Lastly, the Effect Propagation Process offers a philosophical interpretation for mathematical tools that describe non-classical causal behavior, such as Process Matrices. However, the Effect Propagation Process remains agnostic to the operational details of any particular physics theory and, instead, it offers a coherent way of thinking about causality that aligns with the absence of finite spacetime in the quantum realm.

### The Teleology of the Effect Propagation Process

Classical teleology seeks to explain why things exist with  reference to a purpose. However, this type of explanation does not appear to be a driving force in contemporary physics as currently understood by theories exploring quantum gravity.

The Effect Propagation Process framework focuses instead on describing the fundamental process of effect transfer. This process describes how one state of the fundamental structure relates to and influences subsequent states. It does not, however, inherently explain why that process occurs or for what purpose the process exists.

Teleological descriptions, if applicable, would likely be viewed as emergent properties of organized, complex systems that arise from the fundamental Effect Propagation Process rather than a fundamental aspect of causality. The implications for teleology are thus a strong separation between fundamental causal dynamics (the "how") and questions of ultimate purpose (the "why").

### The Ontology of the Effect Propagation Process

The ontology of classical causality considers spacetime as a fundamental background and individual objects exist embedded within this background spacetime. In the classical sense, causality is then understood as temporal relationships between objects localized within this context. The being of a thing is intimately tied to its existence at a specific place and time. Consequently, the separation of cause-and-effect from space and time is not possible because of the temporal order that requires a cause to happen before its effect.

The Effect Propagation Process suggests that fundamental reality is not spacetime itself, but an underlying quantum process (conceptualized as a 'generating function') that operates in a realm where spacetime has not yet emerged. The Effect Propagation Process is then understood as the dynamic essence of this ontology. It represents how effects propagate, and how fundamental degrees of freedom relate and evolve within this underlying structure, thereby constituting the process of emergence itself.

The implication for ontology is profound: our intuitive sense of "being" or "existing" (classically rooted in existence at a location in time) must be reconceived in terms of emergence from this fundamental, dynamic, and potentially non-spatiotemporal process of effect propagation.

### The Epistemology of the Effect Propagation Process

Classical epistemology of causality is focused on how we acquire knowledge about cause-effect relationships that are perceived within the confines of the space-time continuum. The underlying ideas have been shaped by Enlightenment philosophers such as Hume and Kant.
Hume concludes that our belief in causality is rooted in habit after having examined the empirical observation of constant conjunctions and temporal priority.
Kant characterizes causality as the logical lens through which we interpret our sensory input and, through this lens, he argues, our impressions of the external world are formed into a structured experience of coherent events occurring in space and time.
In both cases, epistemic access to causation depends on our practical engagement with, and organization of, effects under a presumed spatiotemporal order.

The issues raised by quantum gravity, in which spacetime may be emergent and causal order indefinite, remove these classical epistemological presuppositions with the profound implication that classical causality is no longer applicable.

The Effect Propagation Process framework suggests a different epistemology in which knowledge about fundamental causality leads to understanding the rules and dynamics of the underlying structure from which spacetime and classical causal order emerge.

## Causal Emergence

The problem of modeling no a-priori causal structures motivates a different view of causality that sets the stage for tackling  causal emergence. The Effect Propagation Process framework's detachment from fixed spacetime and its focus on a generative function establish the foundation" for causal emergence. Static causal discovery, for example Pearl’s DAGs framework, assumes a fixed causal structure and thus cannot handle causal emergence. Granger causality assumes that time-dependent variables change, but the causal structure remains fixed and therefore cannot handle causal emergence either. This argument holds true for any dynamic system with fixed causality because of the inability of the underlying methodology to handle spacetime-agnostic causal structure.

The Effect Propagation Process instead proposes that the causal relationships themselves emerge, change, and may even disappear.  The implications of this approach lead to a fundamental reassessment of how to operationalize causality:

1) Causal discovery

Instead of trying to find a fixed causal structure, EPP models how causal relationships emerge from underlying (dynamic) processes. The existing work on causal discovery remains valid; the EPP, however, takes the idea takes the idea one step further by incorporating a dynamic generative process. Further research will verify the utility of this perspective, but at least it expands the notion of discovering a static structure to describing a dynamic process.

2) Causal transferability

Instead of trying to capture the exact conditions under which a causal relationship holds true, the EPP specifies all presumptions as a generative function, which makes it fundamentally testable and thus transferability can be decided.

3) Causal dynamics

The inspiration from causality in quantum gravity was carefully chosen because of its unique ability to reconcile dynamic and static structures and its handling of deterministic and probabilistic modality. The underlying idea in quantum gravity is that the spacetime fabric of reality itself emerges from an underlying process. While we do not have the scientific methods and technology to verify this idea on the quantum level, we can carefully, within boundaries, transfer the idea to the EPP notion that causality itself emerges from an underlying generative process and, therefore, model the dynamics of causal emergence.

The properties of EPP become apparent when looking from the lens of modeling the dynamics of causal emergence.

* **Temporal order becomes irrelevant**: Because causal relations can emerge from an underlying process
* **Spacetime-agnostic becomes necessary:** Because the generative process is concerned with establishing relations of effect propagation, the exact fabric through which those effects propagate is conceptualized as an external context; therefore, EPP itself has to be spacetime-agnostic.
* **Hardy's causaloids are necessary:** Because the EPP itself is spacetime-agnostic, a different representation of causal relationship that is also spacetime-agnostic becomes necessary and the causaloid proposed by Lucian Hardy has been deemed the best fit.
* **Centrality of the generative function:** Because the EPP can represent causal relations as either static, dynamic, or emergent, the generative function takes on a central role to express those causal relations. Furthermore, a generative function may generate the engulfing context as a specific fabric for the effect propagation process.

The Effect Propagation Process framework constitutes a  foundational shift to viewing causality itself as emergent and thus redefines what causality means in dynamic systems.

Because of its flexibility, EPP can express static causal relationships similar to Pearl’s Causal DAG, it can handle dynamic causal systems similar to Dynamic Bayesian Networks, but then goes further and enables dynamic causal emergence. Dynamic causal emergence has real-world applications:

* **Financial Markets:** Causal relationships between assets change based on market conditions. EPP can be used to model how these relationships emerge and dissolve.
* **Biological Systems:** Gene regulatory networks where modulating relationships emerge based on cellular state.
* **Social Systems:** How influence relationships emerge and change in social networks.


## Contrast

The classical concept of causality existed for millennia and served mankind well until the dawn of the quantum era. The Effect Propagation Process does not seek to replace the classical notion of causality, but instead seeks to advance and generalize the concept of causality to match the now more advanced understanding of fundamental science. To this end, this section contrasts the Effect Propagation Process (EPP) with the classical definition of causality to pinpoint the exact differences:

1) Detachment from Fixed Spacetime

**Classical causality:** Classical causality assumes an implicit Euclidean context with a fixed spacetime. This is a direct consequence of Seneca’s definition. The advent of general relativity changed the notion of a fixed spacetime background towards a dynamic spacetime background with the sole implication that causality became dynamic relative to its engulfing spacetime.

**EPP:** The EPP removes the constraint of spacetime altogether and does not assume any particular fabric in which effects propagate. While classic causality cannot operate in arbitrary, non-spatiotemporal, non-Euclidean structures, EPP  can.

2) Agnostic to Temporal Order

**Classical causality:** Classical causality requires a strict linear temporal order, i.e., a cause must precede its effect.

**EPP:** As EPP removes spacetime altogether, it does not impose any particular temporal order. By extension, there is also no imposed spatial order with the understanding that the EPP would require the underlying fabric to define temporal or spatial order if it were to use these orders during effect propagation.
Instead of seeing temporal order as a fixed background, temporal order is seen as an emergent property. This removes the constraint of fitting all causal interactions into a rigid before-after sequence, opening the door to modeling complex systems with feedback loops.

3) Causaloid as Uniform Building Block

**Classical causality:** Classical causality discern a cause from an effect merely by the imbued temporal order which stipulates that a cause must happen before its effect.

**EPP:** In the absence of a temporal order in EPP, there is no meaningful way to discern a cause from an effect, and consequently, the EPP does not make this distinction any longer. Instead, the EPP relies on Hardy’s causaloid which folds cause and effect into a single entity of testable effect transfer.
The absence of a temporal order does not imply the absence of time; it means the absence of a strict order. That means, EPP allows the modeling of complex systems with bi-directional causal influence, a feat that is hard to accomplish with the classical definition of causality.

4) Focus on the Generative Function

**Classical causality:** Classical causality tries to simplify reality into tractable causal chains operating on observable states.

**EPP:** EPP does not presume the existence of a linear causal chain. Instead, it assumes the existence of a generating function from which the observable fabric (i.e., spacetime) and causal relationships emerge. The effects then propagate through the observable fabric.

5) Embracing Indefinite Causal Order

**Classic causality:** Classical causality assumes the existing of a definitive causal structure that, once discovered, can be modeled. This leads directly to the notoriously hard causal discovery problem as it is not yet clear how to find a definitive causal structure assuming it exists.

**EPP:** EPP does not assume the pre-existence of a definitive causal structure. Instead, it embraces indefinite causal order in which it is not yet clear if A happened before B or B happened before A. Conceptually, this mechanism not only allows for the existence of superposed causal pathways, but enables the handling of emergent causal structures. While the practicality of superposed causal pathways remains an open topic, there is a clear use case for emergent causal structures in dynamic systems. Moving away from a presumed definitive causal structure towards emergent causal structures in dynamic systems elevates causal modeling to deal with the intricate uncertainty of dynamic systems.

## Validity

In empirical science, internal validity focuses on the extent to which a study accurately establishes a causal relationship between variables, whereas external validity considers the extent to which the findings can be generalized.
In the absence of empirical evidence, it is appropriate to consider the soundness and consistency as internal validity and consider the boundaries of generalization as a proxy for external validity.

### Internal validity

#### Soundness:

The soundness of EPP derives from the first principled logical progression of the presented argument. The stated problem of inadequacy of classical causality in light of the challenges imposed by Quantum Gravity (emergent spacetime, indefinite causal order) is well-recognized and documented[^8]. From this recognized problem, the argument for EPP progresses as stated below:

1) Establishes classical causality and its historical critiques.
2) Introduces the challenges from modern physics (GR, QG).
3) Shows why these challenges render classical causality insufficient.
4) Proposes EPP as a coherent response to these challenges.
5) Contrasts EPP with classical causality.
6) Discusses its ontological, epistemological, and teleological implications.
7) Acknowledges and addresses threats to its validity.

The soundness is further strengthened by its inspiration from established scientific theories (QFT, GR) and foundational work in quantum gravity. While quantum gravity as a scientific theory remains a work in progress, the conceptual challenges that arise from it are valid regardless of how any particular theory may explain the underlying quantum mechanisms.

#### Consistency

The consistency of the EPP framework arises from a handful of carefully stated conclusions.

1) spacetime-agnosticism & Causaloids

**Premise:** On a quantum level, spacetime may not exist.\
**Conclusion:** Therefore, remove spacetime from EPP.

**Premise:** EPP does not have a defined spacetime.\
**Conclusion:** Cause and effect cannot be separated any longer because there is no a priori temporal order.

**Premise:** Cause and effect cannot be discerned because of missing temporal order.\
**Conclusion:** Fold cause and effect into one entity, the causaloid, that is independent of temporal (and spatial) order.

Note, the last conclusion holds because of the temporal order required for classical causality. The only logical alternative conclusion from the premise of missing temporal order would be to abandon causality altogether. However, this conflicts with the reality in which causal relationships indeed exist; therefore, the alternative has been deemed unsound.

2) Effect Propagation as the Essence of Causality

**Premise:** The causaloid, as a building block, is independent of temporal (and spatial) order.\
**Conclusion:** Define causality by what it does (propagate effects) instead of what it was thought to be (a temporal-order-dependent atomic relationship).

The careful reader may raise a concern over the choice of words (i.e., propagate effects), since “transferring information” or “transmitting influence” might be equally valid choices. True, that is indeed a fair point. However, the term information has specific meaning in information theory and computer science, and likewise, the term influence has specific meaning in social science; therefore the author settled cautiously on “effect” mainly to prevent conflating different meanings.

3) Compatibility with Classical Causality:

The full logical argument of how classical causality is derived from EPP is in the section “Causality as Effect Propagation Process”.

While classical causality can be derived from EPP, the reverse is not true because EPP cannot be derived from classical causality because classical causality requires a background spacetime. That deduction proves that EPP is more abstract in the sense of more general than classical causality.

Therefore, it follows that EPP naturally applies to areas where classical causality cannot be used any longer.

The internal validity of EPP roots in its internal soundness and consistency that stems from its first-principles reasoning. Therefore, ambiguity, contradictory claims, and unjustified leaps in logic are avoided to the extent it is possible. Minor mistakes might be possible and the author is open to suggestions  to improve EPP further.

### External validity

Establishing the boundaries of generalization as a proxy for external validity requires a delicate balance of realistically acknowledging what EPP can address versus avoiding overstating  any particular capability. Related to external validity is always the possibility of an alternative interpretation of the underlying premises.

#### Alternative interpretations

There are several potential alternative interpretations of the premises underlying the Effect Propagation Process framework.

1) Russell was more right than acknowledged

One can take the position that, if Russell deemed causality as a relict of a bygone era, then why not openly ask to abandon causality altogether and focus solely on descriptive and correlation-based data science?

DARPA disagrees:

> “In the real world, observations are often correlated and a product of an underlying causal mechanism, which can be modeled and understood.”[^11]

The problem is not correlation versus causation as an either-or distinction. Instead, EPP solves the problem of lifting causality into a spacetime-agonistic generalization that is required to model increasingly complex dynamic systems that do not longer adhere to a fixed background spacetime.

2) Pluralism of causal concepts

Instead of a unified framework like EPP, one can argue in favor of the existing pluralistic reality where multiple disjoint concepts of (computational) causality exist for different levels of causal analysis.

As stated before, EPP does not seek to replace classical causality and all tools that are built atop the classical definition. Instead, EPP seeks to advance the core concept of causality to meet increasingly challenging demands. Due to the novelty of this foundational work, a single coherent framework is preferred until it becomes clear which parts may branch out into more specialized applications.

3) Different Interpretations of Quantum Gravity

It is perfectly possible that over time, a different interpretation of quantum gravity may arise because QG is far from settled and further advancement is expected. However, EPP aligns with the general trend of QG research, but isn't rooted in any particular theory of quantum gravity.

The only fundamental work EPP assumes to remain valid is Hardy’s causaloid and, for good reason, because it is the only known attempt to generalize causality to fit into the realm of quantum mechanics and the realm of general relativity. It is important to stress that the causaloid is a necessary stepping stone to establish a foundation for post-quantum causality in the absence of empirical validated scientific facts.

If Hardy’s causaloid would ever be invalidated by verified experimental results, EPP would indeed need a revision. The author remains open to suggestions to revise EPP in that case to re-establish a stronger foundation.

#### Boundaries of Generalization

The main boundary to EPP comes down to preventing the application of any quantum principle to macroscopic systems.

EPP does not endorse nor attempt to apply any quantum principle to non-quantum systems. Instead, it takes inspiration from quantum gravity to advance causality. Furthermore, it is crucial to understand that EPP does not propose that macroscopic complex systems are quantum mechanical in the way they physically operate. Instead, EPP attempts to transfer concepts from quantum gravity to advance causality further to model advanced dynamic systems with complex feedback loops that are notoriously hard to model with conventional causality tools.

Another boundary relates to the lower limit of complexity that can be solved with EPP. For example, abandoning the cause-effect distinction via the causaloid is too radical for many applications. EPP remains compatible with classical causality and therefore can potentially be used where classical causality would apply. However, when a simpler classical causality methodology can solve the problem at hand, it should be preferred over any more complex methodology.

To prevent conceptual overreach, the author does not claim to have invented post-quantum causality even though its inherent independence of spacetime would suggest this view. Furthermore, the author does not claim that the Effect Propagation Process framework would solve open questions in quantum physics or quantum gravity. However, because of the early stage of quantum gravity research, it is far from settled how causality fits into the suggested conceptualization of emergent spacetime.
Instead, the Effect Propagation Process, as a philosophical framework inspired by concepts of quantum gravity, is defined as a spacetime-agnostic continuous effect propagation process.


#### Method Selection Criteria: Classical Causality vs. EPP

In cases where methods of classical causality and conventional machine learning do not solve the problem at hand, methodologies rooted in EPP might be preferred. The following decision matrix supports the assessment of when to use which methods.

This matrix provides guidance on selecting an appropriate causal modeling approach based on the temporal and spatial complexity of the system under investigation.

| Feature Assessed          | System Characteristic                                       | Classical Methods | EPP Consideration     | EPP Recommended/Required |
| :------------------------ | :-------------------------------------------------------- | :---------------- | :-------------------- | :----------------------- |
| **Temporal Complexity**   |                                                           |                   |                       |                          |
|                           | Single time scale + linear progression                    | Sufficient        |                       |                          |
|                           | Multiple time scales OR non-linear temporal relationships | May struggle      | **Consider EPP**      |                          |
|                           | Multiple time scales AND non-linear temporal relationships  | Likely Insufficient |                       | **EPP Required**         |
| **Spatial Structure**     |                                                           |                   |                       |                          |
|                           | Euclidean space with fixed coordinates                      | Sufficient        |                       |                          |
|                           | Non-Euclidean OR dynamic spatial relationships              | Limited/Difficult | **EPP Advantageous**  |                          |
|                           | Non-Euclidean AND dynamic spatial relationships             | Very Limited      |                       | **EPP Likely Required**  |
| **Combined Complexity**   |                                                           |                   |                       |                          |
| _Scenario 1_              | Linear Time & Simple Euclidean Space                      | **Preferred**     |                       |                          |
| _Scenario 2_              | Non-Linear Time OR Complex Spatial                        | May struggle      | **Strongly Consider** |                          |
| _Scenario 3_              | Non-Linear Time AND Complex Spatial                       | Insufficient      |                       | **EPP Essential**        |


**Emergent Causality:** If the problem involves emergent causal structures (where the causal graph itself is not fixed and changes dynamically based on context, i.e., dynamic regime shifts), PP-based methodologies become the only viable option.


## Conclusion

The Effect Propagation Process framework rethinks causality as a continuous transfer of effects originating from a potentially non-spatiotemporal underlying structure.

The framework navigates the challenges of detachment from fixed spacetime paths, aligns with the concept of emergence, accommodates indefinite causal order, and remains compatible with classical causality.

Furthermore, the notion of an Effect Propagation Process reshapes the ontology of causality by suggesting that the most fundamental reality is not spacetime, but the generative process that materializes the spacetime context through which effects propagate.

The framework provides a robust conceptual grounding for exploring the nature of causal effect propagation in a universe that may fundamentally defy classical intuition while leaving traditional teleology as a likely emergent property.

It redefines the scope and methods of epistemology, shifting the focus of causal knowledge from observing event sequences in spacetime to inferring the rules and dynamics of this deeper process.

In contrast to the classical definition of causality, the Effect Propagation Process framework inverts core capabilities and elevates causality to deal with the intricate uncertainties and complex feedback loops of dynamic systems.

The Effect Propagation Process offers a unified philosophical language of causality that is powerful enough to handle new challenges, remains compatible with classical causality, and conceptually aligns with contemporary theories of quantum gravity.

The EPP framework has proven itself as a potent foundation for a new category of computational causality. The [DeepCausality](https://deepcausality.com) project implements the Effect Propagation Process framework as a Rust library for context-aware computational causality that reasons uniformly across Euclidean and non-Euclidean hypergeometric spaces. DeepCausality finds its application in modeling dynamic control systems used in financial markets, advanced analytics, and complex control systems.

## About

[DeepCausality](https://deepcausality.com/) is a hyper-geometric computational causality library that enables fast and
deterministic context-aware
causal reasoning in Rust. Please give us a [star on GitHub.](https://github.com/deepcausality-rs/deep_causality)

**Next:** [Getting started](/getting-started/)

[^1]: Plato’s Timaeus, Stanford Encyclopedia of Philosophy.\
plato.stanford.edu/entries/plato-timaeus
[^2]: Aristotle’s Metaphysics, Stanford Encyclopedia of Philosophy. \
plato.stanford.edu/entries/aristotle-metaphysics
[^3]: Aristotle on Causality, Stanford Encyclopedia of Philosophy.\
https://plato.stanford.edu/entries/aristotle-causality/#FourCaus
[^4]: Seneca, Lucius Annaeus. Seneca: Selected Philosophical Letters: Translated with Introduction and Commentary. OUP Oxford, 2007.\
global.oup.com/academic/product/seneca-selected-philosophical-letters-9780198238942
[^5]: Nov 1915 The four Einstein's papers.\
https://einsteinrelativelyeasy.com/index.php/einstein/83-the-einstein-field-equations-series \
[^6]: Russell, Bertrand, 1912, “On the Notion of Cause”, Proceedings of the Aristotelian Society, 13: 1–26. doi:10.1093/aristotelian/13.1.1
[^7]: Hardy, Lucien. "Probability theories with dynamic causal structure: a new framework for quantum gravity." arXiv preprint gr-qc/0509120 (2005).\
[^8]: Mrini, L., & Hardy, L. (2024). Indefinite Causal Structure and Causal Inequalities with Time-Symmetry. arXiv preprint arXiv:2406.18489.\
[^9]: Leibniz’s Philosophy of Physics, Stanford Encyclopedia of Philosophy.\
https://plato.stanford.edu/entries/leibniz-physics/
[^10]: Peskin, Michael E. An Introduction to quantum field theory. CRC press, 2018.
[^11]: DARPA, ANSR: Assured Neuro Symbolic Learning and Reasoning\
https://www.darpa.mil/research/programs/assured-neuro-symbolic-learning-and-reasoning
[^12]: Granger, C. W. J. (1969). "Investigating Causal Relations by Econometric Models and Cross-spectral Methods". Econometrica. 37 (3): 424–438. doi:10.2307/1912791. JSTOR 1912791.
[^13]: Pearl, Judea (2000). Causality: Models, Reasoning, and Inference. Cambridge University Press.
[^14]:Rubin, Donald (2005). "Causal Inference Using Potential Outcomes". J. Amer. Statist. Assoc. 100 (469): 322–331. doi:10.1198/016214504000001880. S2CID 842793.
[^15]: Paul Dagum; Adam Galper; Eric Horvitz (1992). "Dynamic Network Models for Forecasting". Proceedings of the Eighth Conference on Uncertainty in Artificial Intelligence. AUAI Press: 41–48.
