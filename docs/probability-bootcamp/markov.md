---
title: Markov's Inequality
parent: Probability Bootcamp
layout: home
nav_order: 7
---

# 1. An Important Foundation

Markov's inequality is a simple but powerful upper bound on tail probabilities of non-negative random variables. It helps form the basis for more sophisticated upper bounds and important theorems that arise from the law of large numbers. According to Markov's inequality, 

$$
\boxed{P(X \geq a) \leq \frac{E[X]}{a}}
$$

where the random varible $X$ is non-negative such that $X \geq 0 $. We see that an upper bound is assigned to the probability such that the random variable $X$ takes on a value equal or greater to $a$. Notice that the inequality makes no other assumptions on how $X$ is distributed. Let us consider the following example where $E[X] = 1$ and $a=2$ such that, 

$$
P(X \geq 2) \leq \frac{1}{2}
$$

This means that at least half the _probability mass_ (in the discrete case) of the distribution must be located before $a=2$ regardless of the shape of the distribution. The alternate viewpoint is that there can be no more than half the probability beyond $a=2$. In this sense, Markov's inequality provides a distribution-free constraint on tail behaviour.

[DIAGRAM]

# 2. Derivation

Now let us derive Markov's inequality. We start by working from the definition of the expectation $E[X]$,

$$
\begin{aligned}
E[X]
&= \sum_{\text{all} \ x} xP(X=x) \\
&\geq \sum_{x \geq a} xP(X=x) \quad \text{(i).} \\
&\geq \sum_{x \geq a} aP(X=x) = a\sum_{x \geq a} P(X=x) = aP(X \geq a ) \quad \text{(ii).} \\
\end{aligned}
$$

$$
\Longrightarrow P(X \geq a) \leq \frac{E[X]}{a}
$$

In the first step (i), we strict the sum to all $x \geq a$. Thus the new sum must be smaller or equal to the original because we are no longer summing over all values of $x$. The second step (ii) is less obvious. Within the summation, we replace $x$ with $a$ and because $x \geq a$ for all $x$, the resulting sum must be smaller. Since $a$ is constant, it can be taken out of the sum. The remaining sum is then the definition of $P(X \geq a)$. A simple rearrangment of the inequality yields our desired result.