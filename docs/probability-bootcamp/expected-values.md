---
title: Expected Values
parent: Probability Bootcamp
layout: home
nav_order: 2
---

# 1. Introduction

The idea of taking the expected value of some random variable $X$, most often written as $E[X]$ is quite intuitive. We ask ourselves the question: _If we were going to sample values of the random variable $X$, what would expect its average value to be?_. In many cases, $X$ is distributed in such a way that its expectation $E[X]$ feels instinctive. A good example is the normal distribution where $X \sim \mathcal{N}(\mu, \sigma^2)$. The shape of the probability density function is a bell-curve with a characteristic peak at the centre at $X=\mu$ where the majority of "probability mass" is situated. Without a formal definition of $E[X]$, one may (correctly) suggest that that $E[X]=\mu$. However, for other distributions this intuition falls apart.

[See _The Expected Value (Mean) of a Probability Distribution_]

# 2. Definition

Informally speaking, the expectation value of a random variable $E[X]$ can be thought of as the _centre of mass_ of its distribution. For a discrete random variable $X$, its expectation is the sum of all its possible values weighted by their respective probabilities of occuring,

$$
E[X] = \sum_{\text{all x}} x P(X=x)
$$

where $x$ represents a possible value that $X$ may take on. Analogously, for a continous random variable,

$$
E[X] = \int_{D} xf_X(x)dx
$$

$f_X(x)$ is the probability density functon of $X$ and $D$ is its support. The support, $\text{supp}(X) = D$ of $X$, is the set of all values that $X$ can take with non-zero probability density. While these are not the most rigorous set out by measurement theory, they provide a clean and useful foundation for higher-level probability theory.

{: .highlight} 
**Note:** The sample mean $\bar{X}$ from $n$ measurements of a random variable $X$ approaches converges to the expectation $E[X]$ in the limit of large $n$ such that, $\lim_{n \rightarrow \infty} \bar{X}_n \Longrightarrow E[X]$. This is a consequence of the law of large numbers.

# 2. Key Properties

Now let us consider some general properties of the expecation value. Before we do so, it is useful to imagine the expectation as an operator which acts upon a random variable. Regardless of if a random variable is continous or discrete, the following holds:

$$
E[aX + bY] = aE[X] + bE[Y]
$$

In which, $X$ and $Y$ are random variables while $a$ and $b$ are real constants. The expecation is a **linear operator** and no constraints have been imposed upon $X$ or $Y$; this is the most general property will discuss. If and only if $X$ or $Y$ are independent of each other then, 

$$
E[XY] = E[X]E[Y]
$$

Let us say that we have a random variable $Z$ that is a function of $X$ such that $Z = g(X)$. For the discrete case, the expectation of $Z$ is given by,

$$
\begin{array}{cc}
\textbf{Discrete} & \textbf{Continuous} \\[0.5em]
E[g(X)] = \displaystyle\sum_{\text{all }x} g(x)\,P(X=x)
&
E[g(X)] = \displaystyle\int_{D} g(x)\,f_X(x)\,dx
\end{array}
$$

The rest of this section will be dedicated to offering hand-wavey proofs to these properties. We start with the linearity property,

$$
\begin{aligned}
\text{E}[aX + b]
&= \sum_{\text{all x}} (ax + b) P(X=x) \\
&= a \sum_{\text{all x}} xP(X=x) + b \cancel{ \sum_{\text{all x}} P(X=x) }_{1} \\
&= a \text{E}[X] + b
\end{aligned}
$$

# References 
