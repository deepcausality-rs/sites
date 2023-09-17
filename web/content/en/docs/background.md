---
author: Marvin Hansen
title: "Background"
date: 2023-08-27T18:42:55+08:00
draft: false
---

[//]: # (SPDX-License-Identifier: CC-BY-4.0)

{{< toc >}}

## Overview

With the advent of advanced large language models, many new opportunities arise for applied artificial intelligence, but
some challenges are becoming apparent. ChatGPT still hallucinates
by [fabricating text](https://bernardmarr.com/chatgpt-what-are-hallucinations-and-why-are-they-a-problem-for-ai-systems/)
documented in a [growing list of
blunders](https://docs.google.com/spreadsheets/d/1kDSERnROv5FgHbVN8z_bXH9gak2IXRtoqz0nwhrviCw/edit?pli=1#gid=1302320625).
Beyond language models, there is a real discrepancy between the very high accuracy at which deep learning can detect and
classify patterns and its utter incapability of discerning whether a detected pattern has any meaning.

One has to recognize that these problems at the outcome level are universally higher-order effects of some underlying
design decisions. To that end, it is time to take a closer look at the foundation of deep learning. At its very core,
there are three building blocks of deep learning:

1) Neuronal nets
2) The universal approximation theorem
3) Independent and identically distributed data (IID) assumption

## Neuronal Nets

A neuronal net comprises several interconnected artificial neurons. Once the input value exceeds a certain threshold, a
neuron fires a signal to its output. That very simplicity results in a scalable a three-tier architecture:

1) Input layer
2) Hidden layer(s)
3) Output layer

Training a neuronal network means finding a set of thresholds (called weights) for each neuron in the network so that an
output Y can be determined for an input X. Note, there are many different pathways in a large neuronal network. So, for
the same input, different pathways may lead to different outputs. The difference between the actual value of y and the
value suggested by the neuronal network is called the error. Deep learning training aims to minimize the error, and
there are three ways to do that. One way is to train longer until errors are reduced, the second way is to add more
data, and the third way is to add more neurons to the network until either the error shrinks or the marginal value added
by more neurons diminishes. The limit of how many neurons can be added to a neuronal net is hardware-bound by the amount
of memory in a computer system. The industry is currently doing all three: longer training time, adding more data, and
using increasingly  [bigger supercomputers
for larger models](https://news.microsoft.com/source/features/innovation/openai-azure-supercomputer/).

## The universal approximation theorem

Mathematically speaking, a neural network architecture aims at finding a mathematical function y= f(x) that can map
attributes(x) to output(y) with the smallest error. The Universal Approximation Theorem tells us that a neural network
has some kind of universality, i.e., no matter what f(x) is, there is a network that can approximate the function f(x).

The key idea is replicating the function describing the input data.
Judea Pearl, the founding father of computational
causality, [famously said](https://www.quantamagazine.org/to-build-truly-intelligent-machines-teach-them-cause-and-effect-20180515/):
“All the impressive achievements of deep learning amount to just curve fitting.”

There are two central caveats implied by curve fitting: One is that f(x) has to be a continuous function. However,
neuronal nets have demonstrated remarkable resilience when dealing with partially discontinuous functions. The second
caveat is that the data used in the function must follow the IID assumption in training and production.

## Independent and identically distributed data (IID) assumption

Much of deep learning has statistics as its foundation. In statistics, a collection of random variables is independent
and identically distributed if each random variable has the same probability distribution as the others and all are
mutually independent. This means that all data points are independent, so they are not connected to each other in any
way. In short, variables are independent if knowing about X tells us nothing about Y. Identically distributed means that
variables are drawn from the same probability distribution. While there are many more statistical concepts underlying
machine learning, the key takeaway is that data must follow the IID assumption; otherwise, deep learning falls apart, a
problem that
is  [quite apparent in the financial markets](https://www.pm-research.com/content/iijinvest/early/2019/05/10/joi20191090).

One may wonder, is the IID assumption true?

DARPA is unconvinced:

> "… several of the limitations in ML today are a consequence of the inability to incorporate contextual
> and background knowledge and treating each data set as an independent, uncorrelated input.
> In the real world, observations are often correlated and a product of an underlying causal mechanism,
> which can be modeled and understood."
>
> -- [Assured Neuro Symbolic Learning and Reasoning (ANSR) Program](https://www.darpa.mil/program/assured-neuro-symbolic-learning-and-reasoning)

Furthermore, if the IID isn’t necessarily true in the real world, as DARPA stipulates, does the universal
approximation theorem that builds upon the IID preserve its merits? [Dr. Gary Marcus ](http://garymarcus.com/)
and [Dr. Ernest Davis](https://cims.nyu.edu/people/profiles/DAVIS_Ernest.html)
argue vocally against it in the New York Times:

> “…. we need to stop building computer systems that merely get better and better at detecting statistical patterns
> in data sets — often using an approach known as deep learning — and start building computer systems that,
> from the moment of their assembly, innately grasp three basic concepts: time, space, and causality.”
>
> -- [How to Build Artificial Intelligence We Can Trust. Sept 6, 2019](https://www.nytimes.com/2019/09/06/opinion/ai-explainability.html)

Garry Markus points at the lack of conceptualization as the significant shortcoming of deep learning for a particular
reason: If an AI does not have a concept of a black hole, it would possibly advise flying into one.

## Beyond the IID

However, even if we add the concepts of space, time, and causality to the inventory, machines will still be unable to
comprehend the way humans do because, as Dr. John Mark Bishop says, “it is not so much that AI machinery cannot grasp
causality, but that AI machinery - qua computation - cannot understand anything at all.” More precisely, he observes
that:

> Classical multi-layer neural networks are capable of discovering non-linear,
> continuous transformations between objects or events, but nevertheless,
> they are restricted by operating on representations embedded in the linear, continuous structure of Euclidean space.
> […] Furthermore, representing objects in a Euclidean space imposes a serious additional effect
> because Euclidean vectors can be compared to each other by means of metrics,
> enabling data to be compared in spite of any real-life constraints (sensu stricto, metric rankings may be undefined
> for objects and relations of the real-world).
>
> -- [Artificial Intelligence is stupid, and causal reasoning won't fix it](https://arxiv.org/abs/2008.07371)

The profound argument centres around the necessity of representing AI data (i.e., language) in a computable format to
enable large (language) models to work the way they do. The representation itself is not the problem but rather the
choice of the Euclidean space (default for vector embedding used in large language models) that requires partial order.
This presents a profound problem: partial order assumes all objects are comparable to each other, which is not
necessarily the case.  [Even Dr. Bishop himself acknowledges](https://arxiv.org/pdf/2008.07371.pdf) that
“Whilst causal cognition will undoubtedly be helpful in engineering specific solutions to particular human specified
tasks lacking human understanding, the dream of creating an AGI remains as far away as ever.”

An overlooked aspect of applied deep learning revolves around its rapid accumulation of technical debt. Specifically, in
conventional system engineering, complex systems comprise of smaller and simpler modules and, most importantly, explicit
guarantees are attached to each module. Therefore, reasoning over the entire system w.r.t. to correctness or performance
follows a first-principal bottom-up approach. In deep learning, none of this is currently possible because it lacks the
incrementality, composability, transparency, and debuggability of classical programming.

I suggest that for the ambitious quest of AGI, no single technology will do the trick, and it will most likely take a
multi-disciplinary and multi-model approach to get closer to AGI. Instead, I suggest identifying and filling significant
gaps in contemporary deep learning as a first steppingstone to learning more about trustworthy and reliable machine
intelligence.

## The gap

Significant gaps towards trustworthy and reliable machine intelligence have been identified:

1) Lack of context
2) Lack of relations between data
3) Lack of conceptualization of time and space
4) Lack of causal conceptualization
5) Lack of non-Euclidean data representation
6) Lack of transparent composability

### Lack of context

Fundamentally, context is independent of the model, meaning multiple models in the same domain can share the same
context, so there is real utility. However, context is non-trivial because it differs over time, time scale, space, and
sometimes spacetime. It also evolves over time, hence needing regular updates. The definition of context unavoidably
requires a working conceptualization of at least time and space.

### Lack of relations between data

Grasping relations between data is far from trivial either. Data sets may relate to each other in time, meaning previous
data serve as reference points for current data (temporal reference), or in space, meaning locations may serve as a
spatial reference. Again, when combined, space and time form a non-linear and non-Euclidean continuum.

### Lack of conceptualization of time and space

Perhaps the most baffling revelation I ever stumbled across was that there is no scientifically established definition
of time. There is only an operational definition in physics, defined as “what a clock reads” and various standardized
metrics of how to measure time. There is still no established definition of time itself. Digging further, there cannot
be a definition of time until the  [problem of time](https://en.wikipedia.org/wiki/Problem_of_time) has been solved,
which can only become feasible after general relativity and quantum mechanics have been reconciled, which is no small
feat, and I would not bet on this happening anytime soon.

It is hard to conceptualize anything without an established definition, but when you cannot conceptualize anything, how
do you represent it? Luckily, this particularity has proven to be much less of an issue than it seems. Fundamentally,
there are only two possible scenarios:

1) Time is linear, and the arrow assumption is true, meaning inversion is impossible.
2) Time is non-linear, and the arrow assumption is wrong, meaning inversion is possible.

While there is no discernible evidence for the first scenario because no known particle requires time linearity, there
is tentative support for the second scenario through
the [delayed choice quantum eraser experiment](https://en.wikipedia.org/wiki/Delayed-choice_quantum_eraser)
that [fundamentally challenges time linearity](https://www.youtube.com/watch?v=8ORLN_KwAgs).
While the exact interpretation of the experiment
remains [subject to discussion](https://youtu.be/s5yON4Gs3D0?si=Y0laiikHZTZf617S), the reality is that linear structures
can always be expressed through non-linear structures. The other way around would require an absurd number of
approximation workarounds. Hence, it is most sensible to conceptualize time as a non-linear category of unknown
structure with the requirement that it is also linearly expressible to adhere to the common interpretation of linearity
under the time arrow assumption. That way, both scenarios, linear and non-linear time, can be represented regardless of
the solution to the time problem.

Representation of space is more straightforward as there is a [working definition](https://en.wikipedia.org/wiki/Space)
and you only deal with a maximum of three dimensions. Still, the representation of spacetime requires a solid answer to
the issue of time. When time and spacetime require a non-linear representation,
it is worth extending that non-linearity to space itself and then seeking a unified structure for all three: space,
time, and spacetime.

### Lack of structural conceptualization of causation

When correlation fundamentally deals with two or more things occurring simultaneously (rain & umbrella), causality deals
with a directed relationship leading from a cause to an effect. The difference is subtle but important: Correlation can
be inverted, causation cannot. Flipping the order of a correlation does not change the correlation, meaning rain and
umbrella still occur simultaneously, even if you change the order to umbrella and rain. Causation cannot be inverted
under the time arrow assumption because time only progresses forward. Therefore, when smoking in an open petrol tank
causes an explosion, this does not invert to an explosion leading to smoking. The reason for the lack of inversion roots
in the definition of the causal relationship, which is:

> IF (cause) A then (effect) B
>
> AND
>
> IF NOT (cause) A, then NOT (effect) B

As deceptively simple as the definition of causality looks, finding causal mechanisms and structures is an exceptionally
hard problem because of the high degree of complexity that emerges from it. Specifically, causality may come in several
different structures:

* Single cause, single effect.
* Multi-cause, single effect
* Multi-cause, multiple effects
* Multiple stages of multiple causes leading to multiple effects
* And then causality is contextual.

Causation can be represented in one of two ways:

* Algebra: Simple structure but complex arithmetic
* Geometry: Simple arithmetic but complex structure

The trade-off between structure and arithmetic is worth considering. Specifically, the algorithmization of causality
unavoidably leads to formulating algebra to define the scope and shape of operations and transformations. Depending on
the level of abstraction, the result becomes quite complex and then requires algebraic simplification. Alternatively,
the geometrization of causality inverts the trade-off by only requiring a causal function that is certainly subject to
simpler arithmetic than an entire causal algebraic formula but, in turn, requires a geometric representation of causal
relation with the implication of substantial structural complexity.

It is worth exploring the geometric side of the trade-off because algebra has been the staple of computational causality
since its inception. However, I would not be surprised to see a hybrid approach one day that unifies algebraic and
geometric causality through Geometric (Clifford) algebra and thus extends causality into finite-dimensional
non-euclidean spaces.

### Lack of non-Euclidian data representation

Euclidean space representation in deep learning leads to several unnoticeable higher-order effects. For one, the
centrality of metrics demands the partial order requirement, which then requires that all data objects are comparable
along an ordered scale. When data is not comparable, one of two paths can be taken:

1) Exclude the data, leading to a loss of information.
2) Ordering the data somehow leads to a completely random ranking selection, leading to potentially misleading
   information.

The decision comes down to whether loss of information is the lesser evil than potentially misleading information. The
latter is often a lot less of an issue in deep learning because, in feature engineering, it is common practice to form
categories from otherwise unordered attributes. Usually, the number of features is so large that even if some features
are incorrectly represented, the total impact of a single feature is negligible.

A lesser-known issue centers around data that cannot be represented in Euclidean spaces. Four-dimensional quaternions
are one of those structures that lose too much information when reduced to Euclidian spaces, and that is probably the
reason deep learning has not expanded much into non-Euclidian realms.

However, there is an important link between type theory in computer science and formal requirements in mathematics. As
stated above, Euclidian spaces require metrics, and these demand partial order. In a statically typed language like
Rust, it would be equivalent to requiring a trait bound of partial order for all metric types to work in an Euclidian
space. Trait bounds, however, work both ways, meaning that if you add more trait bounds to a type, you gain more
guaranteed functionality at the expense of losing generalizability. Conversely, removing trait bounds does the opposite.
However, type functionality in Rust can be re-introduced through type extensions; lack of generalizability cannot.

Therefore, starting with no trait bounds is equivalent to a non-Euclidean space in which more specialized and restricted
sub-spaces can be embedded. The elegance of beginning with the least restricted space comes from choosing only the most
essential trait bounds for the holding space while preserving the freedom of selecting more specific restrictions via
type extensions.

### Lack of transparent composability

Composability results from structural compatibility, and structural compatibility results from one of two sources. One
source would be agreed-upon interfaces to which all structures adhere to reach compatibility. In practice, the task
reduces to specifying the agreed-upon functional signature in an interface while leaving details to the implementing
type. While this approach is essentially simpler to design, it often comes with a performance penalty because of dynamic
dispatching at runtime.

The second source of structural compatibility would be a uniform structure that is general enough to express all
applicable requirements. This requirement imposes a thorny constraint because it is rarely the case that all system
requirements are known upfront; hence, assessing the necessary level of generalization of a uniform structure is
difficult. Even more profoundly, the level of uniformity is not fully known until later stages in system design;
consequently, balancing necessary generalization to preserve uniformity with specialization to attain functionality
becomes a meaningful challenge. It is possible to overcome these challenges, but careful structural design must balance
expressibility with uniformity and generalization with specialization. However, the more complex structural design often
results in better performance due to preserving static dispatching. That said, with either one in place, transparent
composability becomes practical and serves as a good design principle.


**Next:** [Concepts](/docs/concepts/)


## About

[DeepCausality](https://deepcausality.com/) is a hyper-geometric computational causality library that enables fast and
deterministic context-aware
causal reasoning in Rust. Please give us a [star on GitHub.](https://github.com/deepcausality-rs/deep_causality)