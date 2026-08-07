---
title: The Laplace Transform
parent: Probability Bootcamp
layout: home
nav_order: 12
---

# **The Laplace Transform I**

## 1. Connection to MGF

As mentioned in the previous chapter, the MGF of a continuous random variable if found by taking the **Laplace transform** of its probability density function $f(x)$ (essentially, but not exactly),

$$
m(t) = \displaystyle\int_{D} e^{tx}f_X(x) dx
$$

Given that the unilateral (one-sided) and bilateral (two-sided) Laplace transforms of a function $f(s)$ are defined as follows,

$$
\begin{array}{cc}
\textbf{Unilateral} & \textbf{Bilateral} \\[0.5em]
F(s) = \mathcal{L} \{f(t)\}(s) = \displaystyle\int_{0}^{\infty} e^{-st}f(t) dt
&
F(s) = \mathcal{L} \{f(t)\}(s) = \displaystyle\int_{-\infty}^{\infty} e^{-st}f(t) dt
\end{array}
$$

Notice that $t$ is a dummy variable used for the integration and is _"integrated out"_ leaving behind $s$. This means that the Laplace transform converts a function $f(t)$ to $F(s)$ by changing its domain. We see that for a continous random variable $X$ which can take on all values $0$ to $\infty$, its MGF $m(t)$ is given by the unilaeral transform of its probability density function evaluated at $-s$ such that $m(s) = \mathcal{L} \{ f_X(x) \} (-s)$. Likewise, if $X$ can take on values from $-\infty$ and $\infty$, $\mathcal{L}$ becomes the bilateral Laplace transform.

$$
\boxed{ m(s) = \mathcal{L} \{ f_X(x) \} (-s) = \displaystyle\int_{0}^{\infty} e^{sx}f_X(x)dx }
$$

When we are working with the 

## 1. Laplace Transform of Common Functions

Now that we have defined the Laplace transform, it is worth working out $F(s)$ for some common functions $f(x)$. A good place to start is with the $n$-th degree monomial $x^n$ where $n$ is a positive integer value. Given that $f(x)=x^n$,

$$
F(s) = \int_{0}^{\infty} e^{sx}x^ndx
$$

Using the tablular method of integration by parts, 

$$
\begin{array}{c|cc}
 & D & I \\ \hline
+ & x^n & e^{-sx} \\
- & nx^{n-1} & -\dfrac{e^{-sx}}{s} \\
+ & n(n-1)x^{n-2} & \dfrac{e^{-sx}}{s^2} \\
- & n(n-1)(n-2)x^{n-3} & -\dfrac{e^{-sx}}{s^3} \\
+ & \vdots & \vdots \\
 & n! & (-1)^n\dfrac{e^{-sx}}{s^{n+1}}
\end{array}
$$

Which allows us to construct the antiderivative as the following finite series,

$$
\Longrightarrow \int_{0}^{\infty} e^{sx}x^ndx = - \left[ \frac{x^n e^{-sx}}{s} + \frac{nx^{n-1} e^{-sx}}{s^2} + \frac{n(n-1)x^{n-2} e^{-sx}}{s^3} + \cdots + \frac{(n!) e^{-sx}}{s^{n+1}}  \right]_{0}^{\infty}
$$

When we evaluate the bounds, only the last term of the series remains such that,

$$
F(s) = \int_{0}^{\infty} e^{sx}x^ndx = \frac{n!}{s^{n+1}}
$$

Hence, the unilateral Laplace transform of the function $f(x) = x^n$ is,

$$
\mathcal{L} \{ f(x) \} (s) = \frac{n!}{s^{n+1}}
$$

Note that the corresponding bilateral Laplce transform does not exist. A more clear way to those unfamiliar with the tabular integration is to consider integration by parts once,

