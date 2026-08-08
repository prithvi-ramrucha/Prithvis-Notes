---
title: The Central Limit Theorem
parent: Probability Bootcamp
layout: home
nav_order: 13
---

# **The Central Limit Theorem**
_Last Edit: 08/08/2026_

## 1. Recap

In the section _"The Law of Large Numbers"_ (LLN), we introduced the central limit theorem (CLT) as the more general result to the LLN. To recap, the CLT says that the sample mean $\bar{X_n}$ calculated from $n$ number of independent measurements $x_i$ of a random variable $X$ is normally distributed such that $\bar{X_n} \sim \mathcal{N} \left( \mu, \sigma^2/n \right)$ where $\text{E}[X] = \mu$ and $\text{Var}[X] = \sigma^2$. It also follows that $\bar{X_n} \rightarrow \mu$ in the limit as $n \rightarrow \infty$. It is assumed that each measurement $x_i$ is identically and independently distributed (IID). Instead of simply stating the CLT, we plan to prove it in this section using generating functions. The idea is to normalise $\bar{X_n}$ and demonstrate that its MGF is identical to that of a standard normally distributed random variable with $\mu = 0$ and $\sigma^2 = 1$.

## 2. Problem Setup

A statement of the CLT can be written as follows,

$$
\boxed{ \lim_{n \rightarrow \infty} \text{P} \left[ \underbrace{\frac{\sqrt{n} (\bar{X_n} - \mu)}{\sigma}}_{Z} \leq z \right] = \Phi(z)  }
$$

where $Z$ is the normalised counterpart to the random variable $\bar{X_n}$, $\Phi(z)$ is the cumulative distribution function (CDF) of a standard normal distribution and $z$ is some value that $Z$ can take on. Our first step is to consider the normalisation of $\bar{X_n}$. To normalise our sample mean, we must apply the following transformation,

$$
Z = \frac{\bar{X_n} - \text{E}[\bar{X_n}]}{\text{Var}[\bar{X_n}]}
$$

In doing so, we ensure that $Z$ has mean of zero, $\text{E}[Z]=0$, and a standard variance such that $\text{Var}[Z]=1$. The expectation of our sample mean is simply $\text{E}[\bar{X_n}] = \mu$ (the same as the underlying distribution of $X$). We know this because $x_i$ is identically and independently distributed,

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

where we have defined $n$ number of new scaled measurements $y_i$ (normalised analogues of $x_i$). These measurements are also said to be drawn from the random variable $Y$ which is analogous to $X$ but with a zero mean $\text{E}[Y] = 0$ and standard variance $\text{Var}[Y] = 1$.


### 3. Quod Erat Demonstrandum

Now we can start with proving the CLT. By definition, the MGF $m_{Z}(t)$ of $Z$ is:

$$
\begin{aligned}
m_{Z}(t)
&= \text{E}[e^{-tZ}] \\
&= \text{E} \left[ \text{exp} \left( \frac{-t}{\sqrt{n}} \sum_{i=1}^{n}y_i \right) \right] \quad \\
&= \text{E} \left[ \Pi_{i=1}^n \text{exp} \left( \frac{-t}{\sqrt{n}} y_i \right) \right] \quad \text{(i)} \\
&= \Pi_{i=1}^n \text{E} \left[ \text{exp} \left( \frac{-t}{\sqrt{n}} y_i \right) \right] \quad \text{(ii)}
\end{aligned}
$$

(i). Using the properties of exponents, we can express the sum of powers as a product. (ii). Given that each scaled measurement $y_i$ is independent from one another, the expectation operator can be moved inside the product. The next step is to realise that expectation of each term in the product is identical since all $y_i$ is drawn from the same distribution $Y$. With this in mind,

$$
m_{Z}(t) = \left( \text{E} \left[ \text{exp} \left( \frac{-t}{\sqrt{n}} Y \right) \right]  \right)^n
$$

It looks like we have reached a dead end. However, we know first couple of low order moments of $Y$. Namely, $\text{E}[Y] = 0$ and $\text{E}[Y^2] = \text{Var}[Y] + (\text{E}[Y])^2 = 1$. To expose these moments, we take the Maclaurin expansion of the expontential function and use the linearity of the expectation operator to write the following, 

$$
\begin{aligned}
m_{Z}(t)
&= \left( \text{E} \left[ 1 + \left(\frac{-t}{\sqrt{n}} \right)Y + \frac{1}{2} \left(\frac{-t}{\sqrt{n}}\right)^2 Y^2 + \cdots \right] \right)^n \\
&= \left( 1 + \left(\frac{-t}{\sqrt{n}} \right) \cancel{\text{E}[Y]}_{0} + \frac{1}{2} \left(\frac{-t}{\sqrt{n}}\right)^2 \cancel{\text{E}[Y^2]}_{1} + \cdots \right)^n \\
&= \left( 1 + \frac{1}{2} \left(\frac{-t}{\sqrt{n}}\right)^2 + \cdots \right)^n \\
&= \left( 1 + \frac{t^2}{2n} + \epsilon(n) \right)^n
\end{aligned}
$$

In the last step, we define a function $\epsilon(n)$ to represent the higher order terms of the expansion. We are now at the last stage in our proof. Our final step is to take the limit as $n \rightarrow \infty$. Although we will not show it rigorously here, we can use the Taylor remainder theorem to show that  $\epsilon(n) \rightarrow 0$ as we take the limit. With this in mind, 

$$
\begin{aligned}
\lim_{n \rightarrow \infty} m_{Z}(t)
&= \lim_{n \rightarrow \infty} \left( 1 + \frac{t^2}{2n} + \cancel{\epsilon(n)} \right)^n \\
&= \lim_{n \rightarrow \infty} \left( 1 + \frac{t^2}{2n} \right)^n \\
&= e^{\frac{t^2}{2}}
\end{aligned}
$$

where we have used the definition of the exponential function,

$$
e^x = \lim_{n \rightarrow \infty} \left( 1 + \frac{1}{x} \right)
$$