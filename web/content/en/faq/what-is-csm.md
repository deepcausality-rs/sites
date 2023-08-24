---
title: "What is Causal State Machine?"
---

A causal state machine encodes causal entities as types with the actual constraint represented as a causal function.
One or more causal entities form a collection that is encapsulated in an abstraction called a causaloid. The causaloid
represents the state, which then gets passed into a the state machine for evaluation and subsequent action.
Unlike a finite state machine, the causal state machine may not know all its causal entities
upfront which allows for greater flexibility: