---
title: Sample Space, Events and Probabilities
parent: Probability Bootcamp
layout: home
nav_order: 1
---

# 1. Sample Space

In probability theory, we consider **experiments** as an abstraction for a thing that can happen: flipping a coin, rolling a dice, selecting a card from a deck of them, etc. The result, observation or measurement at 
the end of an experiment is called an **outcome**. We define a sample space $\Omega$ as the set of all possible outcomes that can result from an experiment. In other words, $\Omega$ contains all possiblities of an experiment that can occur. 

{: .highlight}
**Example 1.1:** Consider the experiment of flipping a coin; it has a two possible outcomes. They are the coin landing on heads $H$ or on tails $L$. In this case, the sample space is simply $\Omega = ( H, T )$.

There are no limits on the cardinality of $\Omega$. However, we will use examples where it is finite. Generally a finite sample space $\Omega$ is defined as,

$\Omega = ( \omega_1, \omega_2, ..., \omega_N )$

where $\omega_j$ is the $j$-th **elementary outcome**: an indivisible outcome that cannot be broken down into smaller outcomes.

{: .highlight}
**Note:** In this introduction, we set the foundations of what is known as _"classical probability"_ which was developed by Bernoulli and Laplace in the 17th century. 
A key assumption is that all elementary outcomes $\omega_i$ of $\Omega$ are equally likely. 

# 2. Events

An event $A$ is a subset of the sample space such that $A \subset \Omega$. That is, events are a selection of outcomes that have occured. Referring back to _example 1.2_, we define an event $A$ as the event that the coin landed on exactly two heads during the experiment. By listing out all possibilities, we find that,

$A = (HHT, \; HTH, \;THH)$