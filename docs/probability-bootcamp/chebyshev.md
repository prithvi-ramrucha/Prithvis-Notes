---
title: Chebyshev's Inequality 
parent: Probability Bootcamp
layout: home
nav_order: 8
---

# 1. The Bigger Brother

Compared to Markov's inequality, Chebyshev's inequality is slightly more involved and powerful. It states that for a random variable $X$, there exists the upper bound:

$$
\boxed{P(\vert X - E[X] \vert \geq a) \leq \frac{\text{Var}[X]}{a}}
$$

where $a > 0$. It is useful to interpret Chebyshev's inequality as an upper bound on the probability that a measurement $X$ deviates significately from its mean $E[X] = \mu$. No matter the nature of the distribution, there is a fundamental limit on how much of the probability mass can be away from the mean. Via the inequality, the absolute error between the mean and the measurement $\vert X - \mu \vert$ is linked to the variance via an upper bound.

[DIAGRAM]

# 2. Derivation

Let us now derive Chebyshev's inequality. We start by considering the event that the absolute error between the measurement $X$ and the mean $\mu$, given by $\vert X - \mu \vert$, is larger than $a$. We write this event as $\vert X - \mu \vert \geq a$. We can show that this event is equivalent to $(X - E[X])^2 \geq a^2$ using the fact that the absolute error squared is the same as squared error such that $\vert X - \mu \vert^2 = (X-\mu)^2$. With this in mind,

$$
\begin{aligned}
& \vert X - \mu \vert \geq a  \\
& \vert X - \mu \vert^2 \geq a^2 \\
& (X - \mu)^2 \geq a^2
\end{aligned}
$$

Using this we may write that,

$$
P(\vert X - \mu \vert \geq a) = P\left[ (X - \mu)^2 \geq a^2 \right]
$$

The rest of the derivation then follows,

$$
\begin{aligned}
P(\vert X - \mu \vert \geq a)
&= P\left[ (X - \mu)^2 \geq a^2 \right] \\
&=P(Z \geq b) \\
&\leq \frac{E[Z]}{b} \quad \text{(markov).}  \\
&= \frac{E[(X - \mu)^2]}{a^2}
\end{aligned}
$$

$$
\Longrightarrow P(\vert X - \mu \vert \geq a) \leq \frac{\text{Var}[X]}{a^2}
$$

where we have introduced the new random variable $Z = (X - \mu)^2$ along with the constant $b=a^2$. This allowed us to make the application of Markov's inequality explicit. Note that in the final step, we use the definition of the variance $\text{Var}[X] = E[(X - \mu)^2$.
