---
author: Marvin Hansen
title: "Getting Started"
description: "Getting Started with DeepCausality"
---

[//]: # (SPDX-License-Identifier: CC-BY-4.0)

It takes just steps to get started with DeepCausality:

## Install

Add DeepCausality to your project using cargo:

```bash
cargo add deep_causality
```

## Import

```rust
use deep_causality::prelude::*;
```

## Code

### Build a causaloid

A causaloid encodes a single causal relation over some data. The API defines two kinds of causaloids:
The regular causaloid requires five generic parameters. See
the [implementation](https://github.com/deepcausality-rs/deep_causality/blob/main/deep_causality/src/types/reasoning_types/causaloid/mod.rs)
for details. The
simpler [BaseCausaloid](https://github.com/deepcausality-rs/deep_causality/blob/main/deep_causality/src/types/alias_types/mod.rs)
is pre-configured with default generic parameters so you don't have to deal with generics. This is helpful for simpler
applications or testing things out. The starter code example shown below uses the BaseCausaloid. The BaseCausaloid
constructor takes three parameters:

1) id: IdentificationValue (alias for u64)
2) causal_fn: CausalFn,
3) description: &'l str

ID and description are self explanatory, though its worth mentioning that many types in DeepCausality are defined as
type aliases to give developers choice to redefine them easily. For example, u64 as ID type was chosen since certain
graphs grow very large. However, for embedded or IoT applications, you may redefine the ID type to a smaller integer
type to conserve memory.

The causal function is a function type that returns a boolean value indicating whether the codified cause has been observed in the data given as an argument. There are two different kinds of 
causal functions, one with context and another one without context. 
The contextual causal function also takes an immutable reference to a context as argument.
Therefore, the causal function can access data from a context to determine whether the 
codified cause has been observed. For an introduction to context in
DeepCausality, [see this blog post.](https://deepcausality.com/blog/announcement-multiple-contexts/) In this starter example, no context is used and, instead, only the data given as an argument is analyzed.


```rust
use deep_causality::prelude::*;

fn get_test_causaloid<'l>(id: IdentificationValue) -> BaseCausaloid<'l> {
    let description = "tests whether data exceeds threshold of 0.55";
    
    fn causal_fn(obs: NumericalValue) -> Result<bool, CausalityError> {
        if obs.is_sign_negative() {
            return Err(CausalityError("Observation is negative".into()));
        }

        let threshold: NumericalValue = 0.55;
        if !obs.ge(&threshold) {
            Ok(false)
        } else {
            Ok(true)
        }
    }

    Causaloid::new(id, causal_fn, description)
}
```

The causal function was adopted because it gives the most freedom to express a singular cause and therefore allows a straightforward implementation. Note, the wrapping function get_test_causaloid needs a lifetime because the Causaloid requires a lifetime to handle references. Please bel mindful to propagate all lifetimes accordingly. Also, the ID is given as an argument because the function is called multiple times to create multiple causaloids in the causal graph shown below.

### Build a multi cause graph

Similar to the causaloid, the CausalGraph also has a BaseCausalGraph already pre-configured with default generic parameters. The API is straightforward in what you would typically expect from workiing with a graph datta structure. You add some nodes, in this case instances of the causaloid previously defined, and you add edges between those nodes according to your requirements.



```rust
use deep_causality::prelude::*;

fn get_multi_cause_graph<'l>() -> BaseCausalGraph<'l> {
    // Builds a multi cause graph:
    //  root
    //  / \
    //  A B
    //  \ /
    //   C

    // Create a new causaloid graph
    let mut g = CausaloidGraph::new();

    // Add root causaloid
    let root_causaloid = get_test_causaloid(0);
    let root_index = g.add_root_causaloid(root_causaloid);

    // Add causaloid A
    let causaloid = get_test_causaloid(1);
    let idx_a = g.add_causaloid(causaloid);

    // Link causaloid A to root causaloid
    g.add_edge(root_index, idx_a)
        .expect("Failed to add edge between root and A");

    // Add causaloid B
    let causaloid = get_test_causaloid(2);
    let idx_b = g.add_causaloid(causaloid);

    // Link causaloid B to root causaloid
    g.add_edge(root_index, idx_b)
        .expect("Failed to add edge between root and B");

    // Add causaloid C
    let causaloid = get_test_causaloid(3);
    let idx_c = g.add_causaloid(causaloid);

    // Link causaloid C to A
    g.add_edge(idx_a, idx_c)
        .expect("Failed to add edge between A and C");

    // Link causaloid C to B
    g.add_edge(idx_b, idx_c)
        .expect("Failed to add edge between C and B");

    g
}

```


See:

* [Starter example](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/examples/starter/src/main.rs).
* [Code examples](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/examples)
* [Tests](https://github.com/deepcausality-rs/deep_causality/tree/main/deep_causality/tests)