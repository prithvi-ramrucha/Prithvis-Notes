---
title: The Central Limit Theorem
parent: Probability Bootcamp
layout: home
nav_order: 13
---

# **The Central Limit Theorem**

## 1. Recap

In the section _"The Law of Large Numbers"_ (LLN), we introduced the central limit theorem (CLT) as the more general result to the LLN. To recap, the CLT says that the sample mean $\bar{X_n}$ calculated from $n$ number of independent measurements $x_i$ of a random variable $X$ is normally distributed such that $\bar{X_n} \sim \mathcal{N} \left( \mu, \sigma^2/n \right)$ where $\text{E}[X] = \mu$ and $\text{Var}[X] = \sigma^2$. It also follows that $\bar{X_n} \rightarrow \mu$ in the limit as $n \rightarrow \infty$. It is assumed that each measurement $x_i$ is identically and independently distributed (IID). Instead of simply stating the CLT, we plan to prove it in this section using generating functions. The idea is to normalise $\bar{X_n}$ and demonstrate that its MGF is identical to that of a normally distributed random variable with $\mu = 0$ and $\sigma^2 = 1$.

## 2. Problem Setup

A statement of the CLT can be written as follows,

$$
\boxed{ \lim_{n \rightarrow \infty} \text{P} \left[ \underbrace{\frac{\sqrt{n} (\bar{X_n} - \mu)}{\sigma}}_{Z} \leq z \right] = \Phi(z)  }
$$

where $Z$ is the normalised counterpart to the random variable $\bar{X_n}$, $\Phi(z)$ is the cumulative distribution function (CDF) of a standard normal distribution and $z$ is some value that $Z$ can take on. Our first step is to consider the normalisation of $\bar{X_n}$. To normalise our sample mean, we must apply the following transformation,

$$
Z = \frac{\bar{X_n} - \text{E}[\bar{X_n}]}{\text{Var}[\bar{X_n}]}
$$

In doing so, we ensure that $Z$ has mean of zero, $\text{E}[Z]=0$, and a variance of one such that $\text{Var}[Z]=1$. The expectation of our sample mean is simply $\text{E}[\bar{X_n}] = \mu$ (the same as underlying distribution of $X$). We know this because $x_i$ is identically and independently distributed,

$$
\text{E}[\bar{X_n}] = \sum_{\text{all} \ x} 
$$

Working out the variance of the sample mean (performed in previous section),

$$
\begin{aligned}
\text{Var}[\bar{X}_n]
&= \text{Var} \left[ \frac{1}{n} \sum_{i=1}^{n} x_i \right] \\
&= \left( \frac{1}{n} \right)^2 \text{Var} \left[ \sum_{i=1}^{n} x_i \right] \\
&= \frac{1}{n^2} \sum_{i=1}^{n} \text{Var}[x_i] \\
&= \frac{1}{n^2} \sum_{i=1}^{n} \sigma^2 = \frac{(n\sigma^2)}{n^2} = \frac{\sigma^2}{n}
\end{aligned}
$$.

Now it is easy to see that, 

$$
Z = \frac{\bar{X_n} - \mu}{\left( \frac{\sigma}{\sqrt{n}} \right)} = \frac{\sqrt{n} (\bar{X_n} - \mu)}{\sigma}
$$

However, we can do some further massaging of $Z$ and write it in a more convenient way,

$$
\begin{aligned}
Z
&= \frac{\sqrt{n} (\bar{X_n} - \mu)}{\sigma} \\
&= \frac{\sqrt{n} [ (\frac{1}{n} \sum_{i=1}^{n} x_i) - \mu]}{\sigma} \\
&= \frac{\sqrt{n} (\frac{1}{n} \sum_{i=1}^{n} x_i - \frac{1}{n} \sum_{i=1}^{n} \mu)}{\sigma} \\
&= \frac{1}{\sqrt{n}} \sum_{i=1}^{n} \underbrace{\left( \frac{x_i - \mu}{\sigma} \right)}_{y_i}
\end{aligned}
$$

where we have defined $n$ number of new scaled measurements $y_i$ (normalised analogues of $x_i$). 