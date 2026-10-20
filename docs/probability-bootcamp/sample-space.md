---
title: Sample Space, Events and Probabilities
parent: Probability Bootcamp
layout: home
nav_order: 1
---

# **Sample Space, Events and Probabilities**
Last Edited: 20/09/2026

### 1. Sample Space

In probability theory, we consider **experiments** as an abstraction for a thing that can happen: flipping a coin, rolling a dice, selecting a card from a deck of them, etc. The result, observation or measurement at 
the end of an experiment is called an **outcome**. We define a sample space $\Omega$ as the set of all possible outcomes that can result from an experiment. In other words, $\Omega$ contains all possiblities of an experiment that can occur. 

{: .highlight}
**Example:** Consider the experiment of flipping a coin; it has a two possible outcomes. They are the coin landing on heads $H$ or on tails $L$. In this case, the sample space is simply $\Omega = ( H, T )$.

There are no limits on the cardinality of $\Omega$. However, we will use examples where it is finite. Generally a finite sample space $\Omega$ is defined as,

$\Omega = [ \omega_1, \omega_2, ..., \omega_N ]$

where $\omega_j$ is the $j$-th **elementary outcome**: an indivisible outcome that cannot be broken down into smaller outcomes. Each elementary outcome is equally as likely as the other. This is the foundation of _"classical probability"_ which was developed by Bernoulli and Laplace in the 17th century. 

### 2. Events and Probabilities 

An **event** $A$ is a subset of the sample space such that $A \subset \Omega$. That is, events are a selection of outcomes that have occured. Referring back to the previous example, 
we could say that the event $A$ is the coin landing on heads. We write this as $A = [H]$ where $A$ is simply a subset containing only a single elementary outcome. Events of this type are called **elementary** events. Now that we have defined the notation of an event, it then follows that we should define the **probability** of an event occuring. In classical probability, the probability of an event occuring $P(A)$ is intuitive,

$$
P(A) = \frac{n(A)}{n(\Omega)}
$$

where $n(A)$ is the number of elementray outcomes in event $A$ and $n(\Omega)$ is the total number of possible outcomes. In our case, $A$ can only occur once because we can only obtain a single heads from a coin flip. Likewise, $n(\Omega)=2$ since there are only two possibilities; heads or tails. Thus, $P(A) = 1/2$. It is important to realise that the calculation of $P(A)$ relies on the fact that,

$$
P(\omega_j) = \frac{1}{n(\Omega)}
$$

which is a formal statement of our earlier assumption that all elementary outcomes have equal probability. Since landing heads is an elementary outcome of flipping a coin, we could have used this to calculate that $P(A) = P(H) = 1/2$. However, treating $A$ as a more complicated object allows us to generalise to joint sample spaces. Let us consider a **composite** event, we image rolling a six-sided die. The sample space is $\Omega = [1, 2, 3, 4, 5, 6]$ and we define $A$ to be the event that the die rolls less than $5$. It is easy to see that $A$ must then be the subset $A = [1, 2, 3, 4, 5]$. Using our definition of probability in simple finite sample spaces, we calculate that $P(A) = 5/6$. With this example, it more obvious that,

$$
P(A) = \sum_{\omega \in A}^{\vert A \vert} P(\omega) = \frac{n(A)}{n(\Omega)}
$$

where we are essentially summing the probabilies of each elementary outcome within the event $A$ to find its probability.

### 3. Joint Sample Spaces

In many different experiments we want may want to consider multiple trials. For this purpose, we use joint sample spaces. Say that we have two sample spaces $\Omega_1$ and $\Omega_2$. When the processes that result in these sample spaces occur with each other, the resulting sample space is the Cartesian product $\Omega = \Omega_1 \times \Omega_2$. Each elementary outcome within $\Omega$, denoted as $\omega_k$ is a tuple (ordered pair) such that,

$$
\Omega = [\underbrace{(\omega_i, \omega_j)}_{\omega_k} \ \vert \ \omega_i \in \Omega_1, \omega_j \in \Omega_2]
$$

To make this more concrete, we should consider an example. Again we imagine a coin and decide to flip it again after the first time. We have two sample spaces from each independent roll, $\Omega_1 = [H, T]$ and $\Omega_2 = [H, T]$. The resulting sample space is then $\Omega = [(H, H), (H, T), (T, H), (T, T)]$. Each elementary outcome of our new sample space $\Omega$ is equally likely because both $\Omega_1$ and $\Omega_2$ were simple finite sample spaces. The calculation of probability also remains unchanged. Say that $A$ is the event that at least a single tails is rolled in either trial,

$$
P(A) = \frac{n(A)}{n(\Omega)} =  \frac{3}{4}
$$

where $A = [(H, T), (T, H), (T, T)]$.