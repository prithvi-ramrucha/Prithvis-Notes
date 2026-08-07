---
title: Moment Generating Functions I
parent: Probability Bootcamp
layout: home
nav_order: 11
---

# **Moment Generating Functions I**

## 1. Hidden In Plain View

We have already encountered moments in previous chapters, but in disguise. It turns out that the mean $E[X] = \mu$ of a distribution is its first moment. Moreover, its variance $\text{Var}[X] = E[X^2]-(E[X])^2$ is closely related to its second moment $E[X^2]$. The higher order moments, $E[X^3]$ and $E[X^4]$, are related to the skewness and kurtosis of the distribution respectively. In general, the $n$-th moment is denoted as $E[X^n]$. A useful analogy is to imagine the moments of a distribution as its finger print; a unique identifier. 

## 2. The Moment Generating Function

Facinatingly, all moments of a random variable $E[X^n]$ can be generated from the moment generating function (MGT) denoted as $m(t)$. The MGT can usually be determined analytically from the following formulae, 

$$
\begin{array}{cc}
\textbf{Discrete} & \textbf{Continuous} \\[0.5em]
m(t) = \displaystyle\sum_{\text{all }x} e^{tx} P(X=x)
&
m(t) = \displaystyle\int_{D} e^{tx}f_X(x) dx
\end{array}
$$

The $n$-th momentum is extracted from the MGT via $m^{(n)}(0) = E[X^n]$ (the $n$-th derivative of the MGT evaluated at $t=0$). Even more shockingly, for the continuous $X$, the MGF is the Laplace transform of the probability density function $f_X(x)$. 


## 3. Motivating The MGF

But how can we motivate the formulae given in the last section for the MGF? I do not know about you, but I would enjoy a little backstory before I _shut up and calculate_. Imagine that we want some function $G(t)$ that encodes all moments of $X$. Let us consider the Taylor series expansion of $G(t)$ which gives us its decomposition, 

$$
G(t) = G(a) + G'(a)(t-a) + G''(a)\frac{(t-a)^2}{2!} + \cdots + G^{(n)}(a)\frac{(t-a)^n}{n!}
$$

We centre the expansion at the origin such that $a=0$ and we have a Maclaurin series, 

$$
G(t) = G(0) + G'(0)t + G''(0)\frac{t^2}{2!} + \cdots + G^{(n)}(0)\frac{t^n}{n!}
$$

This choice may not seem clearly motivated just yet. But it is apparent if we suppose that coefficients of the series gives the moments $E[X^n]$,

$$
G(t) = 1 + E[X]t + E[X^2]\frac{t^2}{2!} + \cdots + E[X^n]\frac{t^n}{n!}
$$

To extract the $n$-th moment from $G(t)$, we must differentiate it $n$ times and set $s=0$ (this is why we decided to set $a=0$ in the previous step). Hence, we have the conditions $G^{(n)}(t=0) = E[X^n]$ for all $n$. Using the definition of the moment $E[X^n]$, we can write that, 

$$
G^{(n)}(t=0) = E[X^n] = \int_{D} x^n P(X=x)dx
$$

Notice that the RHS does not involve $t$, but does include $x$. For this reason, we propose a kernel $g(x, t)$ that is a function of both. The idea of the kernel is to yield $x^n$ within the integrad when we differentiate the generating function $n$ number of times and to also disappear when we set $t=0$. Let us say,

$$
G(t) = \int_{D} g(x, t) P(X=x)dx
$$

Taking the $n$-th derivative of our proposed generating function,  

$$
G^{(n)}(t) = \int_{D} \frac{d^n g(x, t)}{dt^n} P(X=x)dx = \int_{D} g^{n}(x, t) P(X=x)dx
$$

where we have assumed differentiation under the integral sign. We see that $g^{(n)}(x, t) = x^n g(x, t)$ and that $g(x, t=0) = 1$. With both of these properties, we ensure that $G(t)$ returns our moments,

$$
G^{(n)}(t=0) = \int_{D} x^n g(x, t=0) P(X=x)dx = \int_{D} x^n P(X=x)dx = E[X^n]
$$  