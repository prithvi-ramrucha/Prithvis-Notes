---
title: The Poisson Distribution
parent: Probability Bootcamp
layout: home
nav_order: 5
---

# 1. Introduction

So far, we have been introduced to the Poisson distribution as the special case of the binomial distribution for small $p$ and in the limit of large $n$. We observed that $X \sim \text{Bi}(n, p)$ is approximated by $X \sim \text{Po}(\lambda = np)$ of which the probability distribution is,

$$
P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}
$$

But what does a Poisson distributed variable $X$ represent? To attach a meaning to the distribution, we must pay close attention as to how it arises from a limiting case of the binomial distribution. This means abandoning the idea of discrete trials in the experiment since we take the limit as $n \rightarrow \infty$. Instead, we imagine observing events that occur randomly throughout a continuous interval of time, space, area, or volume. The Poisson random variable $X$ then counts the number of times the event occurs within the chosen interval. Given that probability $p$ is small, we say that these events are **rare**. From these insights we can write,

{: .highlight}
**Discription:**  The Poisson distribution gives the number of times a rare event randomly occurs $X$ throughout a continuous interval of time, space, area, or volume. It is parameterised by $\lambda=np$ which is the expected number of times for the event to occur $E[X]$ over some specified interval. The Poisson distribution is often used to model rare events that occur independently and at a constant average rate $\lambda$.

# 2. Mean and Variance

From the view that the Poisson distribution is a special case of the binomial distribution, it is natural to see $\lambda$ as $E[X]$ since $\lambda = np$. However, demonstrating this from the definition of $E[X]$ is more involved. Using the Taylor series expansion of $e^x$,

$$
e^x = \sum_{n=0}^{\infty} \frac{x^n}{n!}
$$

It can be shown that $E[X]=\lambda$ via,

$$
E[X] = \sum_{k=0}^{\infty} k P(X=k) = \sum_{k=0}^{\infty} k \frac{\lambda^u e^{-\lambda}}{k!}
$$ 

$$
\vdots
$$

$$
= \lambda e^{-\lambda} \underbrace{\sum_{u=0}^{\infty} \frac{\lambda^u }{u!}}_{e^{+\lambda}} = \lambda
$$

where many steps have been swept under the rug using $\cdots$. For a full derivation see [LINK]. In a similar fashion, by considering $E[X(X+1)]$ and the property $\text{Var}[X] = E[X^2] - (E[X])^2$, it can be shown that the variance of a Poission distributed variable $X$ is also $\lambda$ such that $\text{Var}[X] = \lambda$.

# 3. References

[jbstatistics - 
The Poisson Distribution: Mathematically Deriving the Mean and Variance](https://www.youtube.com/watch?v=65n_v92JZeE)