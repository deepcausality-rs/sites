---
author: Marvin Hansen
title: What is a Causal State Machine?
weight: 3
---

[//]: # (SPDX-License-Identifier: CC-BY-4.0)

A causal state machine encodes causal entities as types with the actual constraint represented as a causal function. One
or more causal entities form a collection that is encapsulated in an abstraction called a causaloid. The causaloid
represents the state, which then gets passed into a state machine for evaluation and subsequent action. Unlike a finite
state machine, the causal state machine does not have to know all its causal entities upfront which allows for greater
flexibility.