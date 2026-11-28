---
title: Hypothesis Testing
parent: Statistics Foundations
layout: home
nav_order: 4
---

# Hypothesis Testing
Last Edited: 27/11/2026

### 1. The Ground Work

_Has something changed?_ This is the main question that hypothesis testing aims to answer. More specifically, has something changed in our distribution of data? -_Are we sure?_ is another type of important question. Concretely, we ask if some data is distributed in accordance to a particular distribution: Gaussian, Poisson, Binomial and so forth. A very solid application of hypothesis testing is **A/B testing** where we can ask if there is a statisical difference between $A$ and $B$. A specific example is to consider the number of sales of an item before and after marketing campaign. A/B testing will attempt to answer the question of whether or not the campaign had an effect on the sales. Before proceeding with example, it best to define some terminology. The **null hypothesis** $H_0$ is the default or canonical statistical assumption that there is no effect, no difference, or no relationship between variables in the investigation. Conversely, the **alternate hypothesis** $H_{\alpha}$ is the compliment to this; there was an statistically signifcate effect or relationship. These are the only two possibilities. In most problems, computing the probability of the null hypothesis being true $P(H_0)$ is usually much easier than that of the alternate hypothesis $P(H_{\alpha})$.

### 2. A/B Testing Example

Say that the average quantity of a product sold daily is $\mu_Q = 256$ before a marketing campaign. Every day after the campaign begins for a couple weeks $n=14$, the quantity of products sold is recorded. For this duration, the average quantity of products sold is $Q=288$ with a sample variance (unbiased) of $\hat{s}^2 = 1866$. We want to determine if $Q$ is a large enough difference from $\mu_Q$ such that it is statistically significant and the marketing campaign had a positive effect in sales (alternate hypothesis $H_{\alpha}$). The null hypothesis $H_0$ is that the campaign had no effect. Our intuition would be to consider how many standard errors from $\mu_Q$ the difference $Q - \mu_Q$ is,

$$
\hat{Z} = \frac{\hat{Q} - \mu_Q}{\left( \frac{\sigma}{\sqrt{n}} \right)} = \frac{\sqrt{n}(\hat{Q} - \mu_Q)}{\sigma}
$$

where we have remembered that we can approximate the random variable $\hat{Q}$ as being normally distributed such that $\hat{Q} \sim \mathcal{N}(\mu_Q, \sigma^2/n)$ when $n$ is sufficiently large. We divide the difference by the standard error $\sigma/\sqrt{n}$ so that $\hat{Z}$ is distrbuted in accordance with the standard normal $\mathcal{N}(0, 1)$. Because we do not know $\sigma$, we use the estimator from our sample $\hat{s}^2$ to calculate $\hat{Z}$,

$$
\Longrightarrow \hat{Z} = \frac{\sqrt{n}(\hat{Q} - \mu_Q)}{\hat{s}}
$$

Now we can find the probability of $\hat{Z}$ being over the value $q$ which is the standardised version of $Q$,

$$
q = \frac{\sqrt{n}(\hat{Q} - \mu_Q)}{\hat{s}} = \frac{\sqrt{14}(288 - 256)}{\sqrt{1866}} \approx 2.77
$$

$$
\begin{aligned}
&\Longrightarrow P(\hat{Z} \geq q) \\
&= 1 - \phi(q) \\
&\approx 1 - 0.9972 \\
&= 0.0028 \\
&= p
\end{aligned}
$$

When our $p$ value is less than or equal to some value $\alpha$, we accept the alternate hypothesis $H_{\alpha}$ and reject the null $H_0$. Typically, $\alpha=0.05$ and so there is a statistically significant different between $Q=288$ and $\mu_Q=256$ in our case.

### 3. A/B Simulation

We can generalised our case study by writing, 

$$
\hat{Z} = \frac{\sqrt{n}(\hat{Q} - \mu_Q)}{\hat{s}_n} = \frac{R\sqrt{n}}{\lambda}
$$
