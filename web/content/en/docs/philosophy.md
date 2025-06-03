---
author: Marvin Hansen
title: "Philosophy"
date: 2025-05-03
draft: false
---

[//]: # (SPDX-License-Identifier: CC-BY-4.0)

{{< toc >}}

## Overview

The study of causality dates back to Aristotle and was later formalized in its commonly known form by Seneca. Seneca’s assumption of a background space and time was later challenged by relationalists like Leibniz and critiqued scientifically by Russell.

However, contemporary research in quantum gravity suggests that spacetime itself might be emergent from the quantum level and causal structures can be indefinite, thus fundamentally challenging the assumption of a background spacetime. While these concepts may sound specific to quantum physics, the underlying problem of a fixed spacetime assumption's conflict with representing causality in non-linear structures also occurs in advanced system engineering.

In response, the author introduces the "Effect Propagation Process" (EPP) framework for post-quantum causality, which departs from the classical notion of causality as inherently time-linear and instead proposes a spacetime agnostic continuous effect propagation process.

The Effect Propagation Process offers a unified philosophical framework of causality that remains compatible with classical causality and conceptually congruent with physics theories of quantum gravity.
Philosophically, the Effect Propagation Process proposes a different epistemology of causality by shifting the focus of causal knowledge derived from observing event sequences to deriving the dynamics of the underlying generative process.

Practical application of the Effect Propagation Process enables the handling of uncertainties, and non-linear complex feedback loops in dynamic system engineering.

Furthermore, the Effect Propagation Process amounts to a new definition of post-quantum causality due to its inherent independence of spacetime in a strictly theoretical sense.
The Effect Propagation Process does not seek to replace the classical notion of causality; instead it seeks to advance and generalize the concept of causality.

## Motivation

What warrants the development of a new philosophy of causality?

The pre-existing philosophy of causality served mankind for millennia, and one might be tempted to conclude that this is all there is to know about cause and effect.

However, the origin of the Effect Propagation Process (EPP) did not start in philosophy, but in advanced machine learning out of an attempt to solve a profound problem.

Language embeddings remain foundational to contemporary large language models (LLMs), but these require a reduction into a vector space because many prevalent LLM architectures operate efficiently in vector spaces, thus making the reduction from non-Euclidean realms (language) into a Euclidean representation (Vector space) mandatory. Instead of advancing LLM architectures to natively handle non-Euclidean representations, the industry has focused on leveraging Vector databases for storing and retrieving embeddings derived from LLMs. Graph neural networks operate on non-Euclidean spaces, but as these are not yet commonly adopted as core components in mainstream LLM architectures, the problem prevails.

However, when generalizing space beyond Euclidean, then another problem emerges: how to represent time? More profoundly, can we separate time and space from data? Out of this insight, the idea emerged to separate space, time, and data into a separate context usable by multiple models. As space and time were elevated from an implicit background into an explicit first-class context representation, then moving beyond correlation towards causality became the next obvious step. At this moment, a profound problem emerged: When space is non-Euclidean, and time might not be a simple linear progression, then how do we establish a causal relationship?

As it turned out, establishing a clear causal relationship became problematic within the classical definition of causality, which fundamentally relies on a linear time-asymmetric ordering (cause preceding effect) within its assumed background spacetime.

One might challenge the presumption of non-linear time progression, but in complex systems with dynamic feedback loops, it’s perfectly possible to see context structures that entail non-linear time regions.

Non-linear time regions can occur when the background time is represented as a temporal hyper-graph that holds multiple time resolutions simultaneously. The simultaneous presence of time units at different scales breaks the simple time-linear assumption (all time has the same unit, and moves therefore at the same rate) that computational causality tools commonly make.

Furthermore, in a temporal hyper-graph, the unit of time is scale dependent which means to compare temporal values 
one must consider the scale to make a valid comparison between equally scaled values i.e. hour X compared to hour Y.

Less obvious, a temporal hyper-graph, by design, holds all past and present temporal values simultaneously within its structure. This co-existence of multiple temporal points simplifies non-trivial temporal arithmetic over hetero-scaled time units, yet it imposes a vexing problem: How do you know if a time value in a node of the graph is current or past?

The problem is non-trivial because, as time progresses, the engulfing context engine continually generates the non-Euclidean temporal hyper-graph representation with the implication that, at one lookup, the value of a temporal node is current, but at the next one, it might be past; however, the exact temporal distance at which a “present” value becomes “past” depends on the node's time scale. A node holding a temporal value “hour” will be valid for 60 minutes; that means a lookup every ten minutes will yield the current hour 6 times, but handling the seventh lookup leads to a fundamental design decision that illustrates the implied complexity.

A “dynamic-position” design means, when a new hour starts, a new node will be added; therefore, the seventh lookup returns a past value. By implication, the index of the new node needs to be looked up to retrieve the value of the new current hour. Therefore, a “dynamic-position” design requires a dynamic index to locate current values.

A “static-position” design means, when a new hour starts, the previous current value will be overwritten with the understanding that the seventh lookup returns the new current value. By implication, the index of the current value always remains static. Therefore, a “static-position” design requires a fixed index, i.e., a lookup table to locate current values.

Use cases exist for both scenarios and in practice, temporal hyper-graphs use a mixture of static and dynamic positioning to handle different types of relative values, i.e., current day, last year, next hour, and similar.

Exacerbating the problem further, feedback loops across different time scales using different relative values may dynamically modify the temporal hyper-graph itself to capture non-regular observations or to add estimations at future time values that have not yet occurred.

At this point, it becomes abundantly clear that the assumption of a simple, unidirectional linear temporal order required for establishing cause-and-effect becomes untenable.

At the same time, causal relations remain valid in those non-linear regions. Additionally, the designation of a cause purely based on strict temporal order feels arbitrary in a temporal hyper-graph in which past, present, and estimated future temporal values across multiple time scales all exist simultaneously. Regardless of static or dynamic location of relative values, the definition of causality had to evolve to match the reality of modeling causal structures across complex multimodal hyper-graphs.

Upon studying Hardy’s work on unified causality for quantum gravity, the author noticed the clear emphasis of operational causality, a sensible choice given the entire field of quantum gravity can be best described as work in progress.

However, the lack of a philosophical foundation became apparent when attempting to bring together Hardy’s unified causality with uniform static and dynamic context over Euclidean and non-Euclidean structures: There was no “big idea” that would help to bring everything together. However, a new idea was much needed to solve the vexing problem of handling causal inference across complex hyper-graph structures.

The presented Effect Propagation Process closes this gap and brings together all the previously disjoint ideas into one coherent philosophical framework of causality that elegantly solves the non-Euclidean representation problem by defining causality as a fundamentally spacetime agnostic process.

It is important to understand that, without something similar to EPP, conventional causality cannot work across complex hyper-graph structures. The foundational work inspired by Quantum Gravity is a direct testament of the problem complexity that EPP solves.

## History of Causality

Plato is believed to be the first who explored the cause (aitia) in the book of Timaeus (c 360 BC). In it, Plato stipulates that multiple indispensable factors, the model, the maker (Demiurge), the material, and the space (receptacle), explain how the physical world with all the things in it are made[^1].
Aristotle (c 350 BC) formalized the notion of causality in his Metaphysics[^2] with the "Four Causes”[^3]. These are:

1) The material cause or that which is given in reply to the question “What is it made out of?”

2) The formal cause or that which is given in reply to the question "What is it?”. What is singled out in the answer is the essence of the what-it-is-to-be something.

3) The efficient cause or that which is given in reply to the question: “Where does change (or motion) come from?”. What is singled out in the answer is the whence of change (or motion).

4) The final cause, the end purpose, is given in reply to the question: “What is its good?”. What is singled out in the answer is that for the sake of which something is done or takes place.

Seneca (c 56 AD) argues in letter 65[^4] that cause and effect operate within a stage (space) and follow an order (time). Remove the stage or the order, and the conventional understanding of 'making something' or 'causing something' breaks down. His argument highlights time and space as indispensable prerequisites for classical causality. His focus on space and time as necessary conditions served as a precursor for physical concepts treating spacetime as a background for causal processes.

The idea of space and time as a background for causality, however, did not remain unchallenged. Gottfried Wilhelm Leibniz (1646-1716) rejected the concept of absolute space and absolute time as independent, fundamental constructs. Instead, Leibniz proposed[^9] a relational view in which space is the simultaneous relation of coexisting things and time is the relational order of successive things.
Through rigorous first principles analysis, Leibniz argued that the concept of absolute space and time was logically untenable.
His relational perspective offered a significant alternative to the preeminent Newtonian worldview of his time.

## The impact of General Relativity on Causality

Albert Einstein (1879 - 1955) departed from Newtonian physics through his theory of General Relativity[^5] (GR) in which he established that space and time are one manifold, spacetime, that is bent by gravitational influence from large masses. General Relativity preserves the prerequisite of a spatiotemporal context for causality, echoing Seneca's key insight. However, the notion of dynamic spacetime requires a dynamic view of causality to fit into the dynamic spacetime manifold.

Bertrand Russell (1872 - 1970) observed that successful physics roots in sophisticated, law-based descriptions of how a system evolves dynamically. In modern physics, the focus is on the state of a system (e.g., position, velocity, field strength across space) and how that entire state evolves continuously and dynamically. Therefore, for Russell, the idea of classic causality, a strict happen-before relation, does not match the reality of modern physics anymore. Consequently, Russell wrote in his 1912 essay "On the Notion of Cause"[^6]:

> "The law of causality, [...], is a relic of a bygone age"
>  Bertrand Russell

Many modern physics laws are time symmetric and that means if state S1 at time t1 is related to state S2 at time t2 by a law, it's equally true that state S2 at time t2 is related to state S1 at time t1. This relationship isn't a simple, linear, one-way street from a necessary "cause" to a dependent "effect." Knowing the state at any time allows you to calculate the state at any other time, past or future. Therefore, which state is the "cause" and which one is the "effect" becomes arbitrary.

## The impact of Quantum Gravity on Causality

Quantum Field Theory[^10] (QFT) stands out as one of the most rigorously tested theories with unparalleled predictive accuracy in the history of science. QFT Predictions in Quantum Electrodynamics have been experimentally verified up to an astonishing accuracy of one part in a billion or better. This experimental success proves that the underlying concepts such as the primacy of fields, the emergence of particles, and inherent indeterminacy used across different areas of QFT indeed result in demonstrably more accurate models.

The physics standard model, built on top of QFT, despite being one of the most successful theories of all time, describes accurately three of the four known fundamental forces in the universe: electromagnetism, the strong nuclear force, and the weak nuclear force. Notably absent remains gravity due to complex discrepancies between Einstein’s (pre-quantum) theory of relativity and Quantum Field Theory. It is important to point out that General Relativity in itself is successful in the sense of high accuracy and strong predictive power, albeit in a non-quantum realm.

The unification of general relativity with quantum field theory would complete the standard physics model, but doing so faces a non-trivial impasse, as Lucian Hardy[^7] formulated: “Quantum theory is a probabilistic theory with fixed causal structure. General relativity is a deterministic theory but where the causal structure is dynamic.” Furthermore, the emergence of Quantum Gravity[^7] directly challenges the traditional separation of causality through the introduction of indefinite causal order with time symmetry[^8].

Indefinite causal order means the order of causal events is not fixed. It might be that A happens before B, or that B happens before A, or a quantum superposition where both orders (A before B, and B before A) coexist simultaneously.

Time symmetry or time reversal symmetry refers to the theoretical symmetry of physical laws under inverted time. That means, the laws of physics remain the same when time is reversed, a property known as T-symmetry. Many laws of physics are formulated in terms of time symmetry thus allowing to calculate previous system states in time using the same set of equations. For example, laws like Newtonian mechanics, Maxwell's equations of electromagnetism, or Einstein's equations for General Relativity are T-symmetric.

The fundamental dynamical laws of quantum physics (excluding the weak nuclear force) are accepted as T-symmetric. However, the transition of a quantum state from a probabilistic T-symmetric state into a definite and time asymmetric state, while observed, isn't well understood and subject to ongoing research in the field of quantum measurement.

Quantum superposition of states, on the other hand, is extremely well-observed, well documented, and as a result, it is accepted as a fundamental building block of quantum physics. Quantum superposition inspires the exploration of concepts like indefinite causal structures in theories aiming to unify quantum mechanics and gravity.

Therefore, the classical conceptualization of cause and effect embedded into a background spacetime might not yet exist at the fundamental level of quantum gravity. In Quantum Gravity, space and time are not external conditions, but potential emergent properties of the internal quantum structure itself.

The problem isn’t anymore whether spacetime is static or dynamic, but that spacetime itself emerges from the quantum level and thus positions itself as a higher-order effect of a generative process.

> Instead of asking "Where and When does this cause operate?", quantum gravity asks "What is the underlying process from which the notions of 'where' and 'when', and thus causal order, emerge?”

Russell saw physics moving towards laws governing states, a view echoed in quantum gravity's search for fundamental rules governing the structure from which spacetime and causal order emerge. At this stage, the understanding of causality evolved from a structure that required the existence of space towards a dynamic generative process from which causality emerges. This emergent causality does not rely on a pre-existing spacetime, but is grounded in a more fundamental level of reality—a set of underlying rules (i.e. conceptualized as a 'generating function') that determine the fundamental manifestation of spatiotemporal properties.

If the 'output' in terms of emergent properties doesn’t include states that resemble classical spacetime, then the conditions Seneca deemed necessary for causality would not appear. From the quantum perspective, 'space and time' that Seneca identified as necessary conditions are not fundamental inputs to causality anymore, but are outputs from the underlying quantum generative process.

The conceptualization of this fundamental level as a "generating function" captures the idea of a quantum process from which the necessary condition of classical causality's spatiotemporal structure arises. It's a shift from asking "What causes X given spacetime?" to "What process generates spacetime (and thus enables X to be caused)?".

## Causality as Effect Propagation Process

The notion of a quantum generative process that underlies the fabric of spacetime leads to the implication that causality has to evolve beyond the strict “before-after” relation towards a spacetime agnostic view. When removing time from causality, it is indeed not possible anymore to discern cause from effect because, in absence of time, there is no “happen-before” relation anymore and therefore, the designation of cause or effect indeed becomes arbitrary, just as Russell hinted at earlier on.
When removing space from causality, the location of a cause or effect in space is not possible anymore because space itself is not available anymore.

> Naturally, the absence of space and time raises then the
> question of: What is the essence of causality?

Logically, the answer comes in three parts:

1) Causality is a process. It always was.\
2) Causality deals with effects. It always did.\
3) Causality describes how effects propagate.

The first one is self-explanatory because causality occurs in dynamic systems that change and therefore, causality must be a process.

The second one is less obvious, because one might think that causality is all about the “cause” that brings the effects into existence. However, I suggest to think the other way around: We know that X is the cause of effect E, because E happens when X happens and because E does not happen when X does not happen either. Therefore, we can describe a cause in terms of its effects. Therefore, it is true that causality deals with effects.

The third one, effect propagation, stretches the imagination and is less obvious. Let’s re-write the previous definition of classical causality in terms of effect propagation to see that there is no loss of information:

> If X happens, then its effect propagates to Effect E.
> If X does not happen, then its effect does not propagate to Effect E.

In this definition, X does not have a designated label and instead is described in terms of its emitting effect. Therefore, X can be seen as a preceding effect, which then propagates its effect further. Therefore, causality becomes an effect propagation process.

The effect propagation process definition is more general and treats the classical happen-before definition of causality as a specialized derived form. When you designate the preceding effect to be a “cause”, then you can re-write the general definition back into the classic definition thus the general and specialized definitions of causality remain congruent. This detail is important because the generalized effect propagation process definition would not be sound if it were unable to express a specialized variation. Framing causality as an effect propagation process leads to several implications:

1) Focus on the transfer of effects: It emphasizes the process by which a change at one point leads to another change at another point. This is less about a discrete "cause A produces effect B" event linked by external space and time, and more about an effect transfer through the underlying fabric regardless of how that fabric might be defined.

2) Detachment from fixed spacetime: In quantum gravity, where spacetime geometry might be in a superposition or non-existent at the fundamental level, "propagation" isn't a movement along a geodesic in a manifold. It's the propagation of effects through a network of states or elements defined by the fundamental structure.

3) Alignment with emergence: When the fundamental structure gives rise to classical spacetime, this fundamental "effect propagation" would then manifest as propagation through spacetime (e.g., waves, particles, forces traveling from one spatiotemporal point to another). Classical cause-and-effect becomes a macroscopic view of this underlying process. This results from the logical congruence between the general effect propagation process definition and the classical definition of causality.

4) Handling indefinite causal order: In situations where the causal structure itself is indefinite (a superposition on the quantum level, a not-yet emerged state in GR), "effect propagation" can be understood as the influence propagating through a superposition of possible pathways through the fundamental structure. The "effect" isn't tied to a single, definite causal link but is a result of the propagation through all possible pathways.

In the Effect Propagation Process framework, due to the detachment from a fixed spacetime, this fundamental temporal order is absent. Consequently, the entire classical concept of causality, where a cause must happen before its effect cannot be fundamentally established. The distinction between a definitive 'Cause' and a definitive 'Effect' becomes untenable as Russell foresaw. When the separation between cause and effect becomes untenable, then the obvious question arises why even preserve an untenable separation?

Therefore, the Effect Propagation Process framework adopts the causaloid, a uniform entity proposed by Hardy[^7], that merges the ‘cause' and 'effect' into one entity. Instead of dealing with two nearly identical concepts discernible from each other by temporal order, the causaloid is one concept that defines causality in terms of its effect transfer without presupposing a fixed spacetime background[^7].

In the post-quantum context, the term "propagation" does not imply movement through a pre-existing space or time in the classical sense. Instead, it refers to the fundamental process by which an effect is transferred within the underlying structure of reality itself. This fundamental process is what gives rise to the appearance of propagation through spacetime in the classical view.

Furthermore, while classical causality relies on a definite temporal order, the Effect Propagation Process treats temporal order as an emergent property, arising from the fundamental process itself.

While the Effect Propagation Process involves the transfer of effects within the fundamental structure, it is crucial to distinguish this from mere accidental correlation. The process reflects the fundamental way the underlying structure of reality establishes dependencies between its components and how it is giving rise to the non-accidental relationships we recognize as observed causal relations.

This fundamental determination, rather than simple co-occurrence, is what the "Effect Propagation Process" captures at the deepest level. Consequently, causality is understood as an effect propagation process that emerges from the fundamental structure or set of rules (akin to a generating function) from which spatiotemporal relationships emerge.

This philosophical concept of the Effect Propagation Process finds support in physical theories that propose fundamental structures underlying spacetime such as Causal Set Theory, and generalizes the idea of effect transfer present in Quantum Field Theory.

Lastly, the Effect Propagation Process offers a philosophical interpretation for mathematical tools that describe non-classical causal behavior such as Process Matrices. However, the Effect Propagation Process remains agnostic of the operational details of any particular physics theory and, instead, it offers a coherent way of thinking about causality that aligns with the absence of finite spacetime in the quantum realm.

### The Teleology of the Effect Propagation Process

Classical teleology seeks to explain why things exist in reference to a purpose. However, this type of explanation does not appear to be a driving force in contemporary physics as currently understood by theories exploring quantum gravity.

The Effect Propagation Process framework focuses instead on describing the fundamental process of effect transfer. This process describes how one state of the fundamental structure relates to and influences subsequent states. It does not, however, inherently explain why that process occurs or for what purpose the process exists.

Teleological descriptions, if applicable, would likely be viewed as emergent properties of organized, complex systems that arise from the fundamental Effect Propagation Process rather than a fundamental aspect of causality. The implications for teleology are thus a strong separation between fundamental causal dynamics (the "how") and questions of ultimate purpose (the "why").

### The Ontology of the Effect Propagation Process

The ontology of classical causality considers spacetime as a fundamental background and individual objects exist embedded within this background spacetime. In the classical sense, causality is then understood as temporal relationships between objects localized within this context. The being of a thing is intimately tied to its existence at a specific place and time. Consequently, the separation of cause-and-effect from space and time is not possible because of the temporal order that requires a cause to happen before its effect.

The Effect Propagation Process suggests that fundamental reality is not spacetime itself, but an underlying quantum process (conceptualized as a 'generating function') that operates in a realm where spacetime has not yet emerged. The Effect Propagation Process is then understood as the dynamic essence of this ontology. It represents how effects propagate, and how fundamental degrees of freedom relate and evolve within this underlying structure, thereby constituting the process of emergence itself.

The implication for ontology is profound: our intuitive sense of "being" or "existing" (classically rooted in existence at a location in time) must be reconceived in terms of emergence from this fundamental, dynamic, and potentially non-spatiotemporal process of effect propagation.

### The Epistemology of the Effect Propagation Process

Classical epistemology of causality is focused on how we acquire knowledge on cause-effect relationships that are perceived within the confines of the space-time continuum. The underlying ideas have been shaped by Enlightenment philosophers such as Hume and Kant.
Hume concludes that our belief in causality is rooted in habit after having examined the empirical observation of constant conjunctions and temporal priority.
Kant characterizes causality as the logical lens through which we interpret our sensory input and, through this lens, he argues, our impressions of the external world are formed into a structured experience of coherent events occurring in space and time.
In both cases, epistemic access to causation depends on our practical engagement with, and organization of, effects under a presumed spatiotemporal order.

The issues raised by quantum gravity, in which spacetime may be emergent and causal order indefinite, remove these classical epistemological presuppositions with the profound implication that classical causality is not applicable anymore.

The Effect Propagation Process framework suggests a different epistemology in which knowledge about fundamental causality leads to understanding the rules and dynamics of the underlying structure from which spacetime and classical causal order emerge.

## Contrast

The classical concept of causality existed for millennia and served mankind well until the dawn of the quantum era. The Effect Propagation Process does not seek to replace the classical notion of causality, but instead seeks to advance and generalize the concept of causality to match the meanwhile more advanced understanding of fundamental science. To that extent, this section contrasts the Effect Propagation Process (EPP) with the classical definition of causality to pinpoint the exact differences:

1) Detachment from fixed spacetime

**Classic causality:** Classical causality assumes an implicit Euclidean context with a fixed spacetime. It’s a direct consequence of Seneca’s definition. The Advent of general relativity changed the notion of a fixed spacetime background towards a dynamic spacetime background with the sole implication that causality became dynamic relative to its engulfing spacetime.

**EPP:** The EPP removes the constraint of spacetime altogether and does not assume any particular fabric in which effects propagate.

**Inversion:** The advancement from a fixed spacetime to no assumed spacetime constitutes a direct inversion of the underlying assumption. Furthermore, this inverts the core capabilities. While classic causality cannot operate in arbitrary, non-spatiotemporal, non-Euclidean structures, EPP, however, can.

2) Agnostic of temporal order

**Classic causality:** Classic causality requires a strict linear temporal order i.e. cause must precede the effect.

**EPP:** As EPP removes spacetime altogether, it does not impose any particular temporal order. By an extension, there is also no imposed spatial order with the understanding that the EPP would require the underlying fabric to define temporal or spatial order if it were to use these orders during effect propagation.

**Inversion:** Moving from a pre-required fixed temporal order towards no particular order implies another layer of inversion. Instead of seeing temporal order as a fixed background, temporal order is seen as an emergent property. This removes the constraint of fitting all causal interactions into a rigid before-after sequence, opening the door to modeling complex systems with feedback loops.

3) Causaloid as uniform building blocks

**Classic causality:** Classic causality discern a cause from an effect merely by the imbued temporal order which stipulates that a cause must happen before its effect.

**EPP:** In absence of a temporal order in EPP, there is no meaningful way to discern a cause from an effect and consequently the EPP does not make this distinction anymore. Instead, the EPP relies on Hardy’s causaloid which folds cause and effect into a single entity of testable effect transfer.

**Inversion:**

Moving from cause-effect definition towards a single causaloid definition is technically a reduction as it reduces complexity in the sense of having one less concern (temporal order) to cover. The inversion, though, is non-trivial because the absence of a temporal order does not imply the absence of time; it means the absence of a strict order. That means, EPP allows the modeling of complex systems with bi-directional causal influence, a feat task is hard to accomplish with the classical definition of causality.

4) Focus on generative function

**Classic causality:** Classic causality tries to simplify reality into tractable causal chains operating on observable states.

**EPP:** EPP does not presume the existence of a linear causal chain. Instead, it assumed the existence of a generating function from which the observable fabric (i.e. spacetime) and causal relationships emerge. The effects then propagate through the observable fabric.

**Inversion:** The transition from a fixed background towards a generative function that materialized both, the fabric (i.e. spacetime) and causal relationships emerge is a clear inversion from a static to a dynamic view.

5) Embracing indefinite causal order

**Classic causality:** Classic causality assumes the existing of a definitive causal structure that, once discovered, can be modeled. This leads directly to the notoriously hard causal discovery problem as it is not yet clear how to find a definitive causal structure assuming it exists.

**EPP:** EPP does not assume the pre-existence of a definitive causal structure. Instead, it embraces indefinite causal order in which it is not yet clear if A happened before B or B happened before A. Conceptually, this mechanism not only allows for the existence of superposed causal pathways, but enables the handling of emergent causal structures.

**Inversion:** While the practicality of superposed causal pathways remains an open topic, there is a clear use case for emergent causal structures in dynamic systems. Moving away from a presumed definitive causal structure towards emergent causal structures in dynamic systems not only inverts the core capability, but also elevates causal modeling to deal with the intricate uncertainty of dynamic systems.

## Validity

Philosophical concepts may not be subject to the same rigor as empirical science, but the author feels that critically assessing the validity of the Effect Propagation Process framework contributes an important step towards a holistic perspective.

In empirical science, internal validity focuses on the extent to which a study accurately establishes a causal relationship between variables whereas external validity considers the extent to which the findings can be generalized.
In absence of empirical evidence, it is appropriate to consider the soundness and consistency as internal validity and consider the boundaries of generalization as a proxy for external validity.

### Internal validity

#### Soundness:

The soundness of EPP derives from the first principled logical progression of the presented argument. The stated problem of inadequacy of classical causality in light of challenges imposed by Quantum Gravity (emergent spacetime, indefinite causal order) is well recognized and documented[^8]. From this recognized problem, the argument for EPP progresses as stated below:

1) Establishes classical causality and its historical critiques.
2) Introduces the challenges from modern physics (GR, QG).
3) Shows why these challenges render classical causality insufficient
4) Proposes EPP as a coherent response to these challenges.
5) Contrasts EPP with classical causality.
6) Discusses its ontological, epistemological, and teleological implications.
7) Acknowledges and addresses threats to its validity.

The soundness is further strengthened by its inspiration from established scientific theories (QFT, GR) and foundational work in quantum gravity. While quantum gravity as a scientific theory remains work in progress, the conceptual challenges that arise from it are valid regardless of how any particular theory may explain the underlying quantum mechanisms.

#### Consistency

The consistency of the EPP framework arises from a handful of carefully stated conclusions.

1) Spacetime Agnosticism & Causaloids

**Premise:** On a quantum level, spacetime may not exist.\
**Conclusion:** Therefore, remove spacetime from EPP.

**Premise:** EPP does not have a defined spacetime.\
**Conclusion:** Cause and effect cannot be separated anymore because there is no a priori temporal order.

**Premise:** Cause and effect cannot be discerned because of missing temporal order.\
**Conclusion:** Fold cause and effect into one entity, the causaloid, that is independent of temporal (and spatial) order.

Note, the last conclusion holds because of the temporal order required for classical causality. The only logical alternative conclusion from the premise of missing temporal order would be to abandon causality altogether. However, this conflicts with the reality in which causal relationships indeed exist, therefore the alternative has been deemed unsound.

2) Effect Propagation as the Essence of Causality

**Premise:** The causaloid, as a building block, is independent of temporal (and spatial) order.\
**Conclusion:** Define causality by what it does (propagate effects) instead of what it was thought to be (a temporal order dependent atomic relationship).

The careful reader may raise a concern over the choice of words i.e. propagate effects since “transferring information” or “transmitting influence” might be equally valid choices. True, that is indeed a fair point. However, the term information has specific meaning in information theory and computer science and, likewise, the term influence has specific meaning in social science so the author settled cautiously on “effect” mainly to prevent conflating different meanings.

3) Compatibility with Classical Causality:

The full logical argument of how classical causality is derived from EPP is the section “Causality as Effect Propagation Process”.

While classical causality can be derived from EPP, the reverse is not true because EPP cannot be derived from classical causality because classical causality requires a background spacetime. That inference proofs that EPP is more abstract in the sense of more general than classical causality.

Therefore, it follows that EPP naturally applies to areas where classical causality cannot be used anymore.

The internal validity of EPP roots in its internal soundness and consistency due to its first principles reasoning. Therefore, ambiguity, contradictory claims, and unjustified leaps in logic are avoided to the extent it’s possible. Minor mistakes might be possible and the author is open for suggestions to improve EPP further.

### External validity

Establishing the boundaries of generalization as a proxy for external validity requires a delicate balance of realistically acknowledging what EPP can address vs avoiding overstating any particular capability. Related to external validity is always the possibility of an alternative interpretation of the underlying premises.

#### Alternative interpretations

Let’s begin with exploring alternative interpretation of the underlying premises.

1) Russell was more right than acknowledged!

One can take the position that, if Russell deemed causality as a relict of a bygone era, then why not openly ask to abandoned causality altogether and focus solely on descriptive and correlation based data science?

DARPA disagrees:

> “In the real world, observations are often correlated and a product of an underlying causal mechanism, which can be modeled and understood.”[^11]

The problem isn’t correlation vs causation as an either-or distinction. Instead, EPP solves the problem of lifting causality into the post-quantum age to model increasingly complex dynamic systems.

2) Pluralism of causal concepts

Instead of a unified framework like EPP, one can argue in favor of the existing pluralistic reality where multiple disjoint concepts of (computational) causality exist for different levels of causal analysis.

As stated before, EPP does not seek to replace classical causality and all tools that are build atop the classical definition of causality. Instead, EPP seeks to advance the core concept of causality to meet increasingly challenging demands. Due to the novelty of this foundational work, a single coherent framework is preferred until it becomes clear which parts may branch out into more specialized applications.

3) Different Interpretations of Quantum Gravity

It is perfectly possible that over time, a different interpretation of quantum gravity may arise because QG is far from settled and further advancement is expected. However, EPP aligns with the general trend of QG research, but isn't rooted in any particular theory of quantum gravity.

The only fundamental work EPP assumes to remain valid is Hardy’s causaloid and, for good reason, because it is the only known attempt to generalize causal order to fit the realm of quantum mechanics and the realm of general relativity. It is important to stress that the causaloid is a necessary stepping stone to establish a foundation for post-quantum causality in absence of empirical validated scientific facts.

If Hardy’s causaloid would ever be invalidated by verified experimental results, EPP would indeed need a revision. The author remains open for suggestions to revise EPP in that case to re-establish a stronger foundation.

#### Boundaries of Generalization

The main boundary to EPP comes down to preventing the application of any quantum principle to macroscopic systems.

EPP does not endorse nor attempt to apply any quantum principle to non-quantum systems. Instead, it takes inspiration from quantum gravity to advance causality. Furthermore, it is crucial to understand that EPP does not propose that macroscopic complex systems are quantum mechanical in the way they physically operate. Instead, EPP attempts to transfer concepts from quantum gravity to advance causality further to model advanced dynamic systems with complex feedback loops that are notoriously hard to model with conventional causality tools.

Another boundary comes to the lower limit of complexity that can be solved with EPP. For example, abandoning the cause-effect distinction via the causaloid is too radical for many applications.

EPP remains compatible with classical causality and therefore can potentially be used where classic causality would apply. However, when a simpler classical causality methodology can solve the problem at hand, it should be preferred over any more complex methodology.

In cases where methods of classical causality and conventional machine learning does not solve the problem at hand, methodologies rooted in EPP might be preferred.

## Conclusion

The Effect Propagation Process framework rethinks causality as a continuous transfer of effects originating from a potentially non-spatiotemporal underlying structure.

The framework navigates the challenges of detachment from fixed spacetime paths, aligns with the concept of emergence, accommodates indefinite causal order, and remains compatible with classical causality.

Furthermore, the notion of an Effect Propagation Process reshapes the ontology of causality by suggesting that the most fundamental reality is not spacetime, but the generative process that materializes the spacetime context though which effects propagate.

The framework provides a robust conceptual grounding for exploring the nature of causal effect propagation in a universe that may fundamentally defy classical intuition while leaving traditional teleology as a likely emergent property.

It redefines the scope and methods of epistemology, shifting the focus of causal knowledge from observing event sequences in spacetime to inferring the rules and dynamics of this deeper process.

In contrast to the classical definition of causality, the Effect Propagation Process framework inverts core capabilities and elevates causality to deal with the intricate uncertainties and complex feedback loops of dynamic systems.

The Effect Propagation Process offers a unified philosophical language of causality that is powerful enough to handle new challenges, remains compatible with classical causality, and conceptually aligns with contemporary theories of quantum gravity.

The Effect Propagation Process amounts to a new definition of post-quantum causality due to its inherent independence of spacetime. While the EPP was motivated in solving causal inference across hyper-graphs with non-linear temporal structures, its inspiration derived from Quantum Gravity has lead to the definition of post-quantum causality.
The practicality of post-quantum causality remains debatable, but the EPP framework has proven itself as a potent foundation for a new category of computational causality.

The DeepCausality project implements the entire Effect Propagation Process framework as a Rust library for context-aware computational causality that reasons uniformly across Euclidean and non-Euclidean hyper-geometric spaces. DeepCausality finds its application in modeling dynamic control systems used in financial markets, advanced analytics, or socio-economic systems.

**Next:** [Getting started](/getting-started/)


## About

[DeepCausality](https://deepcausality.com/) is a hyper-geometric computational causality library that enables fast and
deterministic context-aware
causal reasoning in Rust. Please give us a [star on GitHub.](https://github.com/deepcausality-rs/deep_causality)


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
