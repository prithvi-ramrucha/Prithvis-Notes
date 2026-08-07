---
title: Variance & Standard Deviation 
parent: Probability Bootcamp
layout: home
nav_order: 3
---

# 1. Introduction

A natural continuation of our discussion on expected values is the subject of the variance of a random variable $\text{Var}[X]$ and, by extention, its standard deviation $\sqrt{\text{Var}[X]}$. Both closely related to each other and said to quantify the _spread_ of the distribution. More spread out distributions tend to have a larger variance and standard deviation in comparision to those which are more narrow or compact. To visualise, we consider the distributions below,

[DIAGRAM]

# 2. Definition

The definition of the variance of a random variable $\text{Var}[X]$ is,

$$
\text{Var}[X] = E \left[ (X-E[X])^2 \right].
$$

It is the expectation of the squared residuals between the mean $E[X]$ and all possible values $X$ may take. Given that the mean can be written as $E[X] = \mu$, we can write out the calculation below for a discrete random variable $X$,

$$
\text{Var}[X] = \sum_{x} (x-\mu)^2P(X=x)
$$

However, the variance is most often not computed this way.


# 3. Key Properties

Arguably most important property of the variance is that, 

$$
\boxed{ \text{Var}[X] = E[X^2] - (E[X])^2 }.
$$

This is extremely useful for computing the variance as only the mean $E[X]$ (first moment of $X$) and the second moment $E[X^2]$ are needed. The property points to a deep connection between the lower-order moments of a distribution and its variance. Demonstrating this property is straight-forward,

$$
\begin{aligned}
\mathrm{Var}[X]
&= E\!\left[(X-E[X])^2\right] \\
&= E\!\left[X^2 - 2X E[X] + (E[X])^2\right] \\
&= E[X^2] - 2E\!\left[XE[X]\right] + E\!\left[(E[X])^2\right] \\
&= E[X^2] - 2E[X\mu] + E[\mu^2] \\
&= E[X^2] - 2\mu E[X] + \mu^2 \\
&= E[X^2] - 2\mu^2 + \mu^2 \\
&= E[X^2] - \mu^2 \\
&= E[X^2] - (E[X])^2.
\end{aligned}
$$

Only two additional ingredients are required. Firsly, the expectation $E[X]$ is a constant $\mu$ and therefore its expectation is itself such that $E[\mu] = \mu$ (tower property). Secondly, we also make use of the linearity property of the expectation value where $E[X_1 + X_2 + ... + X_N] = E[X_1] + E[X_2] +  ... + E[X_N].$ Another important property is that for independent random variables $X$ and $Y$, their variance can be written as,

$$
\text{Var}[X + Y] = \text{Var}[X] + \text{Var}[Y]
$$

This property can be shown using the moment formula $\text{Var}[X] = E[X^2] - (E[X])^2$ in combination with the linearity property of the expectation value. We start from the definition,

$$
\begin{aligned}
\mathrm{Var}[X + Y]
&= E[(X+Y)^2] - (E[X+Y])^2 \\
&= E[X^2 + 2XY + Y^2] - (E[X] + E[Y])^2 \\
&= E[X^2] + 2E[XY] + E[Y^2] - (E[X])^2 - (E[Y])^2 - 2E[X]E[Y] \\
&= E[X^2] - (E[X])^2 + E[Y^2] - (E[Y])^2 + 2E[XY] - 2E[X]E[Y] \\
&= \text{Var}[X] + \text{Var}[Y] + 2 \left( E[XY] - E[X]E[Y] \right)
\end{aligned}.
$$

Now we have a general result for the sum of variances of two random variables $X$ and $Y$,

$$
\mathrm{Var}[X + Y] = \operatorname{Var}[X] + \operatorname{Var}[Y] + \underbrace{2\left( E[XY] - E[X]E[Y] \right)}_{\text{covariance term}}
$$

In this form, it is easy to see that the covariance term disappears if we assume independence $E[XY] = E[X]E[Y]$. Therefore, if $X$ and $Y$ are independent we recover $\text{Var}[X + Y] = \text{Var}[X] + \text{Var}[Y]$ from the general case. The last property we consider is:

$$
\boxed{ \text{Var}[aX + b] = a^2 \text{Var}[X] }
$$

where $a$ and $b$ are constants. This specific property is useful in many derivations and calculations. It can be shown easily using $\text{Var}[X] = E[X^2] - (E[X])^2$ as follows,


$$
\begin{aligned}
\text{Var}[aX + b]
&= \text{E}[(aX + b)^2] - (\text{E}[aX + b])^2 \\
&= \text{E}[a^2 X^2 + 2abX + b^2] - (a\text{E}[X] + b)^2 \\
&= a^2\text{E}[X^2] + 2ab\text{E}[X] + b^2 - a^2(\text{E}[X])^2 - 2ab\text{E}[X] - b^2 \\
&= a^2\text{E}[X^2] \cancel{+ 2ab\text{E}[X]} + \cancel{b^2} - a^2(\text{E}[X])^2 \cancel{- 2ab\text{E}[X]} - \cancel{b^2} \\
&= a^2(\text{E}[X^2] - (\text{E}[X])^2) \\
&= a^2 \text{Var}[X]
\end{aligned}
$$.

In doing so, we remember that $\text{E}[aX] = a\text{E}[X]$.

# References 
