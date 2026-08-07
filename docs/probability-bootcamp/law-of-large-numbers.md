---
title: The Law of Large Numbers 
parent: Probability Bootcamp
layout: home
nav_order: 9
---

# The Law of Large Numbers

## 1. Solidifying Intuition

Numerous times throught the notes, we have mentioned or alluded to the idea that when we repeatedly take measurements of a random variable $X$, the average of the measurements approaches the mean $E[X] = \mu$. This makes intuitive sense: the more measurements we take, the closer the average of the measurements should be to the true mean of the distribution. In this section, we more formally express this observation. Let the **sample mean** $\bar{X}$ be the average of all Independently identically distributed (I.I.D.) measurements $x_1, x_2, \cdots, x_n$, 

$$
\bar{X} = \sum_{i=1}^{n} x_i
$$

We say that as $n \rightarrow \infty$, the sample mean converges to the mean of the distribution such that $\bar{X} \rightarrow \mu$. This is known as **the law of large numbers** (LLN). It is straight-forward to show this via a simulation. Simply define a well-known distribution for $X$ and then randomly draw measurements while calculating the sample mean each time a new measurement is drawn. More formally, we can state the LLN as:

$$
\boxed{ \lim_{n \rightarrow \infty} \text{P} \left( \vert \bar{X} - \mu \vert \geq \epsilon \right) \rightarrow 0 }
$$

where the probability that the difference between the mean and the sample mean $\vert \bar{X} - \mu \vert$ is less than some small number $\epsilon$ approaches zero as we take infintely many measurements. We purposefully formulate the LLN is this way to make use of Markov's inequality. 

## 2. LLN & Markov's Inequality 

As hinted in the last section, we can use Markov's inequality to construct a convincing enough proof for the LLN. According to the inequality, we may write,

$$
\text{P} \left( \vert \bar{X} - \mu \vert \geq \epsilon \right) \leq \frac{\text{Var}[X]}{\epsilon}
$$

We must now show that as $n \rightarrow \infty$, the upper bound $\text{Var}[\bar{X}]/\epsilon$ tends to zero. Therefore, we must find an expression for $\text{Var}[X]$ which involves $n$ such that we can take the limit. Computing the variance, 

$$
\begin{aligned}
\text{Var}[\bar{X}]
&= \text{Var} \left[ \frac{1}{n} \sum_{i=1}^{n} x_i \right] \\
&= \left( \frac{1}{n} \right)^2 \text{Var} \left[ \sum_{i=1}^{n} x_i \right] \\
&= \frac{1}{n^2} \sum_{i=1}^{n} \text{Var}[x_i] \\
&= \frac{1}{n^2} \sum_{i=1}^{n} \sigma^2 = \frac{(n\sigma^2)}{n^2} = \frac{\sigma^2}{n}
\end{aligned}
$$

where we have used the well-known property $\text{Var}[aX] = a^2{Var}[X]$ and that the variance operator is linear in this case because $x_i$ are independent of each other. With this we can write,

$$
\text{P} \left( \vert \bar{X} - \mu \vert \geq \epsilon \right) \leq \frac{\sigma^2}{n \epsilon}
$$

It is now clear that the upper bound tends to zero, $\sigma^2 / n \epsilon \rightarrow 0$, as $n \rightarrow \infty$. Hence, we have demonstrated the LLN using Markov's inequality.

## 3. The Central Limit Theorem

The LLN is one of the most important results in probability and statistics, because it forms the basis of experimental measurement. However, an even more powerful result is the **central limit theorem** (CLT). We can view the LLN as simply a special case of the CLT. For now, a quick statement of the CLT:

{: .highlight}
According to the central limit theorem, the sample mean $\bar{X_n}$ calculated from $n$ number of independent measurements $x_i$ of $X$ is normally distributed such that $\bar{X_n} \sim \mathcal{N} \left( \mu, \sigma^2/n \right)$ where $\text{E}[X] = \mu$ and $\text{Var}[X] = \sigma^2$. It also follows that $\bar{X_n} \rightarrow \mu$ as $n \rightarrow \infty$.