---
title: What is Cauchy Stress Tensor?
author: Jai Nasu
date: 2025-12-04
tags: [tensor, linear algebra, fluid mechanics]
---

## Recap: Tensors and Transformation Properties

As we have seen in [here](../Mathematics/tensor.md), tensors can be defined, in a linear algebraic sense, as multilinear maps that take in vectors and covectors and output scalars:
> [!Definition] Definition: (M, N) Tensor
> An **(M, N) tensor** $\mathcal{T}$ at point $\vec{x} \in \mathbb{R}^n$ is a multilinear map:
> 
> $$
> \mathcal{T}: \underbrace{T^*_{\vec{x}} \mathbb{R}^n \times \cdots \times T^*_{\vec{x}} \mathbb{R}^n}_{M \text{ times}} \times \underbrace{T_{\vec{x}} \mathbb{R}^n \times \cdots \times T_{\vec{x}} \mathbb{R}^n}_{N \text{ times}} \to \mathbb{R}
> $$

Where $T_{\vec{x}} \mathbb{R}^n$ and $T^*_{\vec{x}} \mathbb{R}^n$ are the tangent space and cotangent space at point $\vec{x}$ respectively.

These tangent spaces and cotangent spaces have basis vectors and dual basis that transform in a specific way under coordinate transformations.
For example, if we define $\vec{x}' = \phi(\vec{x})$, then the basis vectors of the tangent space transform as:
$$
\frac{\partial }{\partial x^i} = \frac{\partial x'^{\, j}}{\partial x^i} \frac{\partial }{\partial x'^{\, j}}
$$  
Where $\partial x'^{\, j} / \partial x^k$ is the Jacobian matrix of the transformation $\phi$.

By contrast, the dual basis of the cotangent space transforms as:
$$
d x'^{\, i} = \frac{\partial x'^{\, i}}{\partial x^j} d x^j
$$

Tensors components are transformed according to how their basis vectors and dual basis transform.
For example, a (1, 1) tensor $\mathcal{T}$ can be expressed in components as:
$$
\mathcal{T}(\tilde{\omega}, \vec{v}) = v^i \omega_j \mathcal{T}(d x^j, \frac{\partial }{\partial x^i}) = v^i \omega_j T^j_{i}
$$
Under the coordinate transformation $\vec{x}' = \phi(\vec{x})$, the components transform
