---
title: The Normal Distribution
parent: Probability Bootcamp
layout: home
nav_order: 7
---

# **The Normal Distribution**
Last Edited: 17/08/2026

### 1. Introduction

In the last few sections, we saw that a binomially distributed variable $X \sim \text{Bi} (n, p)$ becomes Poisson distributed in the limit $n \rightarrow \infty$ with small $p$. Although we will not show it in this section, it turns out that if $p$ (the probability of success) is not small, $X$ tends to the **normal distribution**. The visual shape of the normal distribution is well known and it often described as a _"bell-curve"_ (it is also often referred to as the Gaussian distribution)n

![1786306153287](image/normal-distribution/1786306153287.png)

A variable $X$ that is normally distributed is denoted as $X \sim \mathcal{N} (\mu, \sigma^2)$ where the distribution parameters are the mean $\text{E}[X] = \mu$ and variance $\text{Var}[X]= \sigma^2$. Note that unlike a binomially distributed variable, $X$ is a continuous random variable and has the following probability density function, 

$$
\boxed{ f_X(x) = \frac{1}{\sigma \sqrt{2 \pi}}e^{-\frac{(x - \mu)^2}{2\sigma^2}}}
$$

The probability that random variable $X$ takes on a value between $a$ and $b$ where $b > a$ is then, 

$$
\text{P}(a \leq x \leq b) =  \int_{a}^{b} f_X(x) dx = -\frac{1}{\sigma \sqrt{2 \pi}} \int_{a}^{b} e^{\frac{(x - \mu)^2}{2\sigma^2}} dx
$$

Graphically, 

![1786306669473](image/normal-distribution/1786306669473.png)

### 2. The Standard Normal Distribution

The calculation of $\text{P}(a \leq x \leq b)$ for a generic normal distribution $X \sim \mathcal{N} (\mu, \sigma^2)$ involves an integral that does not have an elementary closed-form solution. For this reason, we define the unit normal or standard distribution $X \sim \mathcal{N} (0, 1)$ with a zero mean $\mu=0$ and a standard variance $\sigma^2=1$. In this case, the probability becomes,

$$
\text{P}(a \leq x \leq b) = \frac{1}{\sigma \sqrt{2 \pi}} \int_{a}^{b} e^{-\frac{x^2}{2}} dx
$$

Altough, this integral still does not have an elementary closed-form. The key is to define the cumulative distribution function (CDF),

$$
\boxed{ \Phi(x) =  \int_{-\infty}^{x} f_X(x) dx = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{x} e^{-\frac{t^2}{2}}dt}
$$

The CDF tells us the probability of $X$ having a value in the interval $]-\infty, x]$. That is, we integrate the PDF for all values smaller than some $x$. Visually, we can imagine $\Phi(x)$ as giving the area under the PDF up to said $x$. Using the CDF we can work out the probabilities, 

$$
\begin{aligned}
\text{P}(a \leq x \leq b) &= \Phi(b) - \Phi(a) \\[1em]
\text{P}(x < a) &= \Phi(a) \\[1em]
\text{P}(x > a) &= 1 - \Phi(a)
\end{aligned}
$$

The standard normal distribution is particularly useful because any normal distribution can be transformed into the standard normal distribution. This transformation is known as **standardisation**. Suppose that $X \sim \mathcal{N}(\mu,\sigma^2)$, we define a new random variable $Z$ by subtracting the mean and dividing by the standard deviation:

$$
Z = \frac{X-\mu}{\sigma}
$$

This is called the **z-score** of $X$. It measures how many standard deviations $\sigma$ a particular value of $X$ lies from the mean $\mu$. Although we won't show it here, this transformation converts a generic normal distribution $\mathcal{N}(\mu,\sigma^2)$ to a standard normal $\mathcal{N}(0 ,1)$. Hence, rather than needing a separate probability function for every possible normal distribution, we can transform any normal distribution into the standard normal distribution and use the same function $\Phi$ for the calculation of probabilities. $\text{P}(a \leq x \leq b)$. Tables, calculators, and statistical software can then be used to evaluate $\Phi(z)$. 

$$ 
X \sim \mathcal{N}(\mu,\sigma^2) \Longrightarrow Z = \frac{X-\mu}{\sigma} \sim \mathcal{N}(0, 1)
$$

### 3. Symmetry 

Visually, it is apparent the the normal distribution is symmetric. This fact lends itself from the PDF being an even function such that, 

$$
f_X(-x) = f_X(x)
$$

Using this observation, we may also derive some key properties of the CDF. Say that we want to evaluate $\phi(-x)$ given that $\phi(x)$ is known for some $x$ where $x>0$. By graphing $f_X(x)$ we may see that the area underneath the curve for values larger than $x$ is identical to the area where the values are less than $-x$

[Diagram]

Hence, we reason that,

$$
\begin{aligned}
\phi(-x)
&= \int^{-x}_{-\infty} f_X(x)dx \\
&= \int^{\infty}_{x} f_X(x)dx \\
&= 1 - \underbrace{\int^{x}_{-\infty} f_X(x)dx}_{\phi(x)}
\end{aligned}
$$

$$
\Longrightarrow \phi(-x) = 1 - \phi(x)
$$

Using the same logic, we may also work out the probability $\text{P}(\vert x \vert > a)$,

$$
\begin{aligned}
\text{P}(\vert x \vert > a)
&= \text{P}(x < -a) + P(x > a)\\
&= 2\text{P}(x > a) \\
&= 2 \left[ 1 - \phi(a) \right]
\end{aligned}
$$

$$
\Longrightarrow \text{P}(\vert x \vert > a) = 2 \left[ 1 - \phi(a) \right]
$$

### 4. Standardisation

### 5. The Three Sigma Rule

A key property of the normal distribution $X \sim \mathcal{N}(\mu,\sigma^2)$ is the **68–95–99.7** or _Three Sigma_ rule. According to the rule, there is an approximately 68% probability that $X$ will take on a value $x$ within a single standard derivation $\sigma$ of the mean $\mu$ in the interval $[\mu - \sigma, \mu + \sigma]$. For $2\sigma$, there is a 95% probability finding $x$ within the interval $[\mu - 2\sigma, \mu + 2\sigma]$ and 99.7% inside $3\sigma$ interval. Demontrating this property requires some work. We start by performing standardisation so that $X \rightarrow Z \sim \mathcal{N}(\mu=0,\sigma^2=1)$. We then use the Maclaurin expansion of the exponential function to rewrite the PDF as the following,

$$
\begin{aligned}
\text{P}(z_1 \leq z \leq z_2)
&= \frac{1}{ \sqrt{2 \pi}} \int_{z_1}^{z_2} e^{-\frac{z^2}{2}} dz \\
&= \frac{1}{\sqrt{2 \pi}} \int_{z_1}^{z_2} \sum^{\infty}_{n=0} \frac{\left( -\frac{z^2}{2} \right)^n}{n!} dz \\
&= \frac{1}{\sqrt{2 \pi}} \int_{z_1}^{z_2} \sum^{\infty}_{n=0} \frac{(-1)^n z^{2n}}{2^n n!} dz \\
&= \frac{1}{\sqrt{2 \pi}} \sum^{\infty}_{n=0} \frac{(-1)^n}{2^n n!} \left( \int_{z_1}^{z_2}z^{2n}dz \right)
\end{aligned}
$$

In the last step, we have made the assumption that the summation and integration symbol can interchange places without rigourous proof. Now we define the bounds of integration. Since we are working with z-scores and they are, by definition, the number of standard deviations from the mean, we choose the bounds $z_1 = -z$ and $z_2 = z$. These bounds consider the interval $[-z, z]$ so that when $z=1$ we have a $1\sigma$ interval. When $z=2$ we have $2\sigma$ interval, $z=3$ for $3\sigma$ and so forth. Evaluating the integral,

$$
\int_{-z}^{z}z^{2n}dz = 2\int_{0}^{z}z^{2n}dz = 2 \left[ \frac{z^{2n+1}}{(2n+1)} \right]_{0}^{z} = \frac{2z^{2n+1}}{(2n+1)}
$$

Because $z^{2n}$ is an even function ($2n$ is always an even power) and we have symmetric interval $[-z, z]$, integration is straight-forward. Now we have, 

$$
\begin{aligned}
\text{P}([-z, z])
&= \frac{1}{\sqrt{2 \pi}} \sum^{\infty}_{n=0} \frac{(-1)^n}{2^n n!} \left( \frac{2z^{2n+1}}{(2n+1)} \right) \\
&= \frac{2}{\sqrt{2 \pi}} \sum^{\infty}_{n=0} \frac{(-1)^n z^{2n+1}}{2^n (2n+1) n!}
\end{aligned}

\Longrightarrow \boxed{ \text{P}([-z, z]) = \sqrt{\frac{2}{\pi}} \sum^{\infty}_{n=0} \frac{(-1)^n z^{2n+1}}{2^n (2n+1) n!} }
$$

Python can be used to compute this series expansion formula for $z=1$, $z=2$ and $z=3$, 

### References

Continuous Probability Distributions: The Normal Distribution (STAT I – Full Lecture). JBStatistics (2016). URL: https://www.youtube.com/watch?v=lqczxjR6MbA