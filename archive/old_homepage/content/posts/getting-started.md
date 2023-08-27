---
title: "Getting Started"
date: 2023-06-30T15:08:14+08:00
draft: false
tags: ['Rust', 'Tutorial']
---

It takes just steps to get started with DeepCausality:

1) Install
2) Import
3) Code

## Install

Add the following to your Cargo.toml

```toml
deep_causality = { git = "https://github.com/deepcausality/deep_causality.git", tag = "0.2.1" }
```

## Import

```rust
use deep_causality::prelude::*;
```

## Code

```rust
use deep_causality::prelude::*;
use deep_causality::types::reasoning_types;

type AllCauses = Vec<Causaloid>; // type alias for brevity

// Add some sample data
fn get_all_observations() -> Vec<Observation>
{
    let o1 = Observation::new(1, 0.89, 1.0);
    let o2 = Observation::new(2, 0.87, 1.0);
    let o3 = Observation::new(3, 0.78, 1.0);
    let o4 = Observation::new(4, 0.65, 1.0);
    let o5 = Observation::new(5, 0.55, 1.0);
    let o6 = Observation::new(6, 0.45, 0.0);
    let o7 = Observation::new(7, 0.45, 0.0);
    let o8 = Observation::new(8, 0.25, 0.0);
    let o9 = Observation::new(9, 0.15, 0.0);

    Vec::from_iter([o1, o2, o3, o4, o5, o6, o7, o8, o9])
}

// Our causal function tests if the observation is above a threshold of 55%
fn causal_fn( obs: NumericalValue) -> Result<bool, CausalityError>
{
    if obs.is_nan() {
        return Err(CausalityError("Observation is NULL/NAN".into()));
    }

    let threshold: NumericalValue = 0.55;
    if !obs.ge(&threshold) {
        return Ok(false);
    };

    Ok(true)
}

// Buils causaloid
fn build_smoke_tar_causaloid() -> Causaloid
{
    println!();
    let all_obs = get_all_observations();

    let target_threshold = 0.55;
    let target_effect = 1.0; //
    let percent_obs = all_obs.percent_observation(target_threshold, target_effect);
    let percent_non_obs = all_obs.percent_non_observation(target_threshold, target_effect);

    let question = "Do smokers have tar in the lung?".to_string() as DescriptionValue;
    let observation = percent_obs;
    let threshold = 0.55; // Threshold above which the observations is considered an inference.
    let effect = 1.0; // observed effect
    let target = 1.0; // expected effect of the inference once the threshold is reached or exceeded
    let inference = Inference::new(0, question, observation, threshold, effect, target);

    println!(
        "Can we infer from the data that smokers have tar in the lung? : {:?}",
        inference.is_inferable()
    );
    println!();

    let inv_question = "Do NON smokers have NO tar in the lung?".to_string() as DescriptionValue;
    let inv_observation = percent_non_obs;
    let inv_effect = 0.0; // observed effect
    let inv_target = 0.0; // expected effect of the inference once the threshold is reached or exceeded
    let inv_inference = Inference::new(0, inv_question, inv_observation, threshold, inv_effect, inv_target);

    println!(
        "Can we infer from the data that NON smokers have NO tar in the lung? : {:?}",
        inv_inference.is_inverse_inferable()
    );
    println!();

    // 1) Build inference collection
    let inferable_coll: Vec<Inference> = Vec::from_iter([inference]);
    let inverse_inferable_coll: Vec<Inference> = Vec::from_iter([inv_inference]);
    // 2) Describe the causal relation
    let id = 01;
    let description = "Causal relation between smoking and tar in the lung".to_string();
    let data_set_id = "Data set abc from study Homer et al. DOI: 122345 ".to_string();

    //3) Build the causaloid
    build_causaloid(
        id,
        causal_fn,
        description,
        data_set_id,
        &inferable_coll,
        &inverse_inferable_coll,
    ).unwrap()
}

```