---
author: Marvin Hansen
title: "Causal State Machine"
date: 2023-09-04
draft: true
---
[//]: # (SPDX-License-Identifier: CC-BY-4.0)

{{< toc >}}

## Overview

## Causal State Machine

A causal state machine models a context-free system where each cause maps to a known effect. The example below models a
sensor network that screens an industry site for smoke, fire, and explosions. Because the sensors are reliable, an alert
will be raised whenever the sensor exceeds a certain threshold. You could implement this kind of system in many ways,
but as the example shows, the causal state machine makes the system relatively easy to maintain. New sensors, for
example, from a drone inspection, can be added and evaluated dynamically.

* [CSM](deep_causality/src/types/csm_types/mod.rs)
* [CsmAction](deep_causality/src/types/csm_types/csm_action.rs)
* [Csm CausalState](deep_causality/src/types/csm_types/csm_state.rs)
* [CSM example code](deep_causality/examples/csm)
