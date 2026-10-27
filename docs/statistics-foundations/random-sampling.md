---
title: Random Sampling
parent: Statistics Foundations
layout: home
nav_order: 2
---

# Random Sampling

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
\bar{x}_n = \frac{1}{n} \sum_{i=1}^{n} x_i \quad \sigma_n^2 = \frac{1}{n} \sum_{i=1}^{n} (x_i - \mu)^2
$$

Because we do not know the population statistics, infer them through the calculation of the sample statistics. 