---
title: Multi-layer Peceptrons
parent: Deep Learning From Scratch 
layout: home
nav_order: 1
---

# **Multi-layer Peceptrons**

### Introduction

Feed forward neural networks are the most simple kind of neural networks where data can only flow in one direction. Of this broad category of neural networks, multi-layer perceptrons (MLPs) are the most elementary type. In MLPs, layers of neurons are fully connected, meaning that each neuron in one layer is connected to every neuron in the subsequent layer. An MLP typically consists of an input layer, one or more hidden layers, and an output layer. Recall that the forward \pass of the single layer $l$ can be written as,

$$
\mathbf{A}^{(l)} = \phi(\mathbf{A}^{(l-1)}\mathbf{W}^{(t)} + \mathbf{B}^{(t)})
$$

where $\mathbf{A}$ is the output matrix of the layer, $\mathbf{W}$ is its weight matrix, $\mathbf{B}$ is the bias matrix, $\mathbf{A}^{(l-1)}$ is the input matrix (out matrix of the previous layer) and $\phi$ is the activation function which is applied element wise on $\mathbf{Z}^{(l)} = \mathbf{A}^{(l-1)}\mathbf{W}^{(t)} + \mathbf{B}^{(t)}$.

