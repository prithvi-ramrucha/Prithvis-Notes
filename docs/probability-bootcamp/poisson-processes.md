---
title: Poisson Processes
parent: Probability Bootcamp
layout: home
nav_order: 6
---

# 1. Counting Processes

Before introducing Poisson processes, we must to talk about a more general idea: **counting processes**. To put it concisely, a counting process defines a counting function
$N(t)$ for $t \geq t$ which represents the number of events that occur by some time $t$. Specifically, if $s > t$ where $s$ and $t$ are times, then $N(t) - N(s)$ is the number of events that occured during the interval $(s, t]$. Following this definition, the counting function has the properties below,

{: .highlight} 
**Properties** 
1. $N(t) \geq 0$ (positive function) 
2. $N(t)$ is always an integer (discrete events). 
3. If $s \leq t$, then $N(s) \leq N(t)$

# 2. Poisson Processes

A Poisson process is a specific type of counting process, arguably the most well-known, where the number of events betweeen initial $t$ and final time $t+\Delta t$, denoted as $n$ is Poisson distributed such that,

$$
P[N(t + \Delta t) - N(t) = n] = \frac{(\lambda \Delta t)^n e^{-\lambda \Delta t}}{n!}
$$

where the expectation of $n$ is $E[n] = \lambda \Delta t$. In contrast to the typical Poisson distribution that is agnostic to the underlying domain, $\lambda$ is the expected number of events per unit time. While $n \sim \text{Po}(\lambda \Delta)$, we can show that the time between these Poisson events is also described by a characteristic and well-known distribution called the **exponential distribution**. Let us assume that $t=0$, $\Delta t = t$ and that no events have occured at the initial time $N(t-0)$=0, we define $T$ to be the time that our first event occurs starting from the initial time. To be explicit, the probability distribution for the number of events in the interval is then,

$$
\boxed{P[N(t)=n] = \frac{(\lambda t)^n e^{-\lambda t}}{n!}}
$$

If $T>t$, then no event has occured in the interval $(0, t]$. The probability of no event occuring in the interval is,

$$
P(T > t) = \int^{\infty}_{t} f_N(t)dt
$$

where we consider the probability density function (PDF) $f_N(t)$ because we are working with continuous random variables. Given that no event has occured in the interval, the counting function must be zero such that $N(t)=0$. Therefore,

$$
P(T>t) = P[N(t)=0] = e^{-\lambda t}
$$

With this insight, we have enough information to derive $f_N(t)$. We simply work backwards and integrate,

$$
\int^{\infty}_{t} f_N(t)dt = e^{-\lambda t} \Longrightarrow f_N(t) = \lambda e^{-\lambda t}
$$

This PDF is the exponential distribution we referred to earlier. To be clear, $f_N(t)$ is the probability density associated with the probability of at least one event occuring in the interval $(t, t+dt]$. Suppose that we want to know the probability of at least a single event occuring between the times of $t=\tau_1$ and $t=\tau_2$, we use the PDF accordingly,

$$
P(\tau_1 < T \leq \tau_2) = \int^{\tau_2}_{\tau_1} \lambda e^{-\lambda t} dt = e^{-\lambda \tau_2} - e^{-\lambda \tau_1}
$$

# 3. Time Between Poisson Events

TBA

# References 

https://www.youtube.com/watch?v=P6qQQXa0r4M
