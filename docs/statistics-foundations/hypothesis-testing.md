---
title: Hypothesis Testing
parent: Statistics Foundations
layout: home
nav_order: 4
---

# Hypothesis Testing
Last Edited: 26/11/2026

### 1. The Ground Work

_Has something changed?_ This is the main question that hypothesis testing aims to answer. More specifically, has something changed in our distribution of data? -_Are we sure?_ is another type of important question. Concretely, we ask if some data is distributed in accordance to a particular distribution: Gaussian, Poisson, Binomial and so forth. A very solid application of hypothesis testing is **A/B testing** where we can ask if there is a statisical difference between $A$ and $B$. A specific example is to consider the number of sales of an item before and after marketing campaign. A/B testing will attempt to answer the question of whether or not the campaign had an effect on the sales. Before proceeding with example, it best to define some terminology. The **null hypothesis** $H_0$ is the default or canonical statistical assumption that there is no effect, no difference, or no relationship between variables in the investigation. Conversely, the **alternate hypothesis** $H_{\alpha}$ is the compliment to this; there was an statistically signifcate effect or relationship. These are the only two possibilities. In most problems, computing the probability of the null hypothesis being true $P(H_0)$ is usually much easier than that of the alternate hypothesis $P(H_{\alpha})$.

### 2. A/B Testing Example