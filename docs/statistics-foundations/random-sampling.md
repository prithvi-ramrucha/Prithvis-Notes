---
title: Random Sampling
parent: Statistics Foundations
layout: home
nav_order: 2
---

# Random Sampling
Last Edited: 11/11/2026

### 1. Population vs Sample
The distinction between the population and the sample is important in statistics. Say that we want to find the average height of all human beings on Earth, to compute this average we would need to measure the height of each person in the entire worldwide population. Say that we have $N$ number of people in the human population, the heights would be the following set $\mathcal{P} = [x_1, x_2, ..., x_N]$. For practical reasons, this is not possible. Therefore, we should consider working with the sample instead. The simple (random) sample randomly draws from the population $\mathcal{S} = [X_1, X_2, ..., X_n]$ where $X_i$ is random variable and $n$ is the number of samples. Generally, the number of measurments in the sample is much smaller than that of the population $n < N$. The value of the random variable $X_i$ is determined from a random draw with replacement from the population $\mathcal{P}$. Mathematically, 

$$
\underbrace{X_1, X_2, ..., X_n}_{\mathcal{S}} \sim^{\text{i.i.d.}} \text{Uniform}(\mathcal{P})
$$

where each sample $X_i$ is independent and identically distributed. When we observe the sample $\mathcal{S}$, by performing the measurments, the result is the set $\mathcal{S} = [x_1, x_2, ..., x_n]$. These are our sample measurements. They are roughly distributed in the same way as our population and can be used to infer properties about it. Note that in reality, random sampling cannot be truly i.i.d. due to bias in the sampling methodology. Another key distinction is that sampling in the real world is without replacement because we do not measure the same person twice (assuming correct methodology).

### 2. Sample Mean and Variance

Our population has the mean $\mu$ and the variance $\sigma^2$,

$$
\mu = \frac{1}{N} \sum_{i=1}^{N} x_i \quad \sigma^2 = \frac{1}{N} \sum_{i=1}^{N} (x_i - \mu)^2
$$

We call this the **population statistics**. Analgous to this is the **sample statistics** which includes the sample mean $\bar{x}_n$ and variance $\sigma_n^2$, 

$$
\bar{x}_n = \frac{1}{n} \sum_{i=1}^{n} x_i \quad \sigma_n^2 = \frac{1}{n} \sum_{i=1}^{n} (x_i - \bar{x}_n)^2
$$

where we have used the set of observed values $\mathcal{S}$ (sample measurements). Because we do not know the population statistics, we infer them through the calculation of the sample statistics. As we take more and more samples where $n \rightarrow N$, we expect the sample mean and variance to converge to that of the population, assuming that $N$ is very large, such that $\bar{x}_n \rightarrow \mu$ and $\sigma_n \rightarrow \sigma$ repectively. Since our measurements $\mathcal{S}$ are randomly sampled from the population $\mathcal{P},$, we have to use **estimators**. This is because the value of $\bar{x}_n$ changes depending on the sample $\mathcal{S}$ generated. The estimator of the sample mean is the random variable $\bar{X}_n$ given by,

$$
\bar{X}_n = \frac{1}{n} \sum_{i=1}^{n} X_i
$$

All random variables have an associated expectation value and variance; our estimator is no exception. Let us work out the expectation value of $\bar{X}_n$,

$$
\begin{aligned}
E[\bar{X}_n] &= E \left[ \frac{1}{n} \sum_{i=1}^{n} X_i \right] \\
&= \frac{1}{n} \sum_{i=1}^{n} E[X_i] \\
&= \frac{1}{n} \sum_{i=1}^{n} \sum_{\text{all} \ x_i} x_i P(X_i = x_i) \\
&= \frac{1}{n} \sum_{i=1}^{n} \sum_{i=1}^n x_i P(X_i = x_i)
\end{aligned}
$$

where we have used the definition of the expectation $E[X_i]$ in the last step. The probability $P(X_i = x_i) = 1/n$ because all $n$ samples in $\mathcal{S}$ are randomly sampled from $\mathcal{P}$. When we plug this,

$$
\begin{aligned}
&= \frac{1}{n} \sum_{i=1}^{n} \sum_{i=1}^{n} \frac{x_i}{n} \\
&= \frac{1}{n} \sum_{i=1}^{n} \left( \frac{1}{n} \sum_{i=1}^{n} x_i \right) \\
&= \frac{1}{n} \sum_{i=1}^{n} \mu = \frac{1}{n} (n\mu) = \mu
\end{aligned}
$$

The result $E[\bar{X}_n] = \mu$ shows that our estimator for the mean is **unbiased**. Hence, we expect the sample mean to truthfully estimate the population mean. Let us also work out the variance $\text{Var}[\bar{X}_n]$,

$$
\begin{aligned}
\text{Var}[\bar{X}_n] &= \text{Var} \left[ \sum_{i=1}^{n} X_i \right] \\
&= \frac{1}{n^2} \text{Var} \left[ \sum_{i=1}^{n} X_i \right] \\
&= \frac{1}{n^2} \sum_{i=1}^{n} \text{Var}[X_i] \quad \text{(a)} \\
&= \frac{1}{n^2} \sum_{i=1}^{n} \sum_{i=1}^{n} (x_i - \mu)^2 P(X_i = x_i) \\
&= \frac{1}{n^2} \sum_{i=1}^{n} \left( \frac{1}{n} \sum_{i=1}^{n} (x_i - \mu)^2 \right) \\
&= \frac{1}{n^2} \sum_{i=1}^{n} \sigma^2 = \frac{1}{n^2} (n\sigma^2) = \frac{\sigma^2}{n}
\end{aligned}
$$

We recover the result $\text{Var}[\bar{X}_n] = \sigma^2/n$ which tells us that our estimate of the population becomes increasingly more accurate from the calculation of the sample mean when we take a larger number of samples. The central limit theorem (CLT) gives a shape to the distribution of $\bar{X}_n$ and tells us that $\bar{X}_n \sim \mathcal{N}(\mu, \sigma/n)$. For larger $n$, the distribution of $\bar{X}_n$ becomes increasing more narrow and peak-like on the population mean $\mu$. The spread of this this normal distribution, its standard deviation, is given by $\sigma/\sqrt{n}$. Before moving on, it is worth discussing the assumption of independence made in step (a). We assume that there is no covariance between all $X_i$; that they are independent random variables. This is true when $n$ is very large and we consider random sampling **with replacement**. However, when we do consider random sampling with replacement, this simplification does not hold. [...].

Another estimator is $\hat{S_n^2}$ for the variance, 

$$
\hat{S} = \frac{1}{n} \sum_{n}^{i=1} (X_i - \bar{X_n})^2
$$

which is directly computed from the sample statistics. Calculating the expected value of this estimator is useful as it provides the bridge between the sample and population statistics.

$$
E[\hat{S_n^2}] = ... = \frac{(n-1) \sigma^2}{n}
$$

### 3. Using The Estimators

Now that we have established unbiased estimators for the mean and variance of the population using the sample data, 

$$
\bar{X_n} = \frac{1}{n} \sum_{i=1}^{n} X_i
$$

$$
\hat{s_n^2} = \frac{1}{n-1} \sum_{i=1}^{n} (X_i - \bar{X_n})^2
$$

