---
title: Multi-Layer Peceptrons
parent: Deep Learning From Scratch 
layout: home
nav_order: 1
---

# **Multi-Layer Peceptrons**

### 1. Introduction

Feed forward neural networks are the most simple kind of neural networks where data can only flow in one direction. Of this broad category of neural networks, multi-layer perceptrons (MLPs) are the most elementary type. In MLPs, layers of neurons are fully connected, meaning that each neuron in one layer is connected to every neuron in the subsequent layer. An MLP typically consists of an input layer, one or more hidden layers, and an output layer. Recall that the forward pass of the single layer $l$ can be written as,

$$
\mathbf{A}^{(l)} = \phi_l(\mathbf{A}^{(l-1)}\mathbf{W}^{(l)} + \mathbf{B}^{(l)})
$$

where $\mathbf{A}$ is the output matrix of the layer, $\mathbf{W}$ is its weight matrix, $\mathbf{B}$ is the bias matrix, $\mathbf{A}^{(l-1)}$ is the input matrix (out matrix of the previous layer) and $\phi_l$ is the activation function which is applied element wise on $\mathbf{Z}^{(l)} = \mathbf{A}^{(l-1)}\mathbf{W}^{(t)} + \mathbf{B}^{(t)}$. The entire network can be described as the following composite function $f(\mathbf{X})$, 

$$
f(\mathbf{X}; \Theta) = f_L \circ f_{L-1} \circ \cdots \circ f_2 \circ f_1(\mathbf{X})
$$

where the function $f_l(\mathbf{A^{(l-1)}}) = \phi_l\left( \mathbf{A^{(l-1)}}\mathbf{W}^{(l)} + \mathbf{b}^{(l)} \right)$ represents a single layer and $\mathbf{X}=\mathbf{A^0}$ is the input matrix. More explicitly,

$$
\mathbf{A}^{(L)}
=
\phi_L \left(
\phi_{L-1}\left(
\cdots
\phi_2\left(
\phi_1\left(
\mathbf{A}^{(0)}\mathbf{W}^{(1)}
+
\mathbf{B}^{(1)}
\right)
\mathbf{W}^{(2)}
+
\mathbf{B}^{(2)}
\right)
\cdots
\right)
\mathbf{W}^{(L)}
+
\mathbf{B}^{(L)}
\right)
$$

### 2. Backprogation

Constructing the MLP as a composite function of linear operations with non-linear activations is straight-forward. We know that $f(\mathbf{X})$ acts a universal function approximator and should theoretically map $X \rightarrow \hat{f}(\mathbf{X})$ given a sufficient number of training parameters. The difficult part is to figure out to optimise these training parameters $\Theta$ via backpropagation. Firstly, in this section, we will mathematically formulate backprogation 

See: https://neuralnetworksanddeeplearning.com/chap2?
