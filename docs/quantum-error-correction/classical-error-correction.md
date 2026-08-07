---
title: Repetition Codes
layout: home
parent: Basics of Quantum Error Correction
nav_order: 2
---

_Last Edited 31/07/2026_

## Introduction

Before discussing QEC, we should briefly review classical error correction (CEC). The most simple form of classical error correction algorithms involved repetition codes. Say that we want to encode a single bit `0`. Using repetition codes, we code this single bit but replicating it exactly $N_b$ times. Say that we have $N_b=3$ (3-bit repetition code), our single bit is encoded as `000`.

$$
0 \Longrightarrow 000 \quad \text{(encoded)}
$$

But why do we do this? Let us say that by chance, that when we transmit our encoded bits `000`, an error occurs through the flipping of a single bit such that,

$$
000 \Longrightarrow 010 \quad \text{(error)}
$$

where the middle bit has flipped. If we take the majority vote of the bit values, we can recover the original bit: $M(010)=0$. However, if more than a single bit had flipped during transmission, we could not recover the original unencoded bit. Therefore, we say that a 3-bit repetition code can protect up to a single bit flip error. In general, a $N$-bit repetition code can correct up to $k$ number of bit-flip errors where,

$$
k = \frac{N-1}{2}
$$

Note that $N$ must be an odd integer to ensure tie-breaking.

{: .highlight}
**Example:** Consider the following message encoded by a 5-bit repetition code:
`001001101100100`. By decoding the message, we get: `010`.

## Modelling Bit Flips

Error in the form of bit-flips are modelled as a stochastic process with the probability of a given bit flipping being $p$. We let the random variable $X$ denote the number bits that flip during the transmission of the encoded bits. Assuming that each bit-flip is independent, the $X$ follows a Binomial distribution such that $X \sim \text{Bi}(N, p)$. The probability that the original message is recoverable after transmission is therefore $P(X \leq k)$,

$$
P(X \leq k) = \sum^{k}_{j=0} \frac{N!}{(N-j)! j!}p^{j} (1-p)^{N-j}
$$

For a $3$-bit repetition code where $N=3$ and $k=1$ (largest number of encoded bits that can be flipped such that the orginal bit is recoverable) is calculated by,

$$
\begin{aligned}
P(X \leq 1) &= P(X = 0) + P(X = 1)\\
&= (1-p)^3 + 3p(1-p)^2\\
& \vdots\\
&= 1 + 2p^3 - 3p^3
\end{aligned}
$$

Specifically for a 3-bit repetition code, when $p < 0.5$, the probability of the original message being decoded from a transmitted repetition code is greater than $p$. That is, when the probability of an individual bit flip is low enough, it is better to encode the original bit using repetition codes rather than only solely transmitting it. 