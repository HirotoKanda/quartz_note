---
title: "Remarks from Calculus"
date: "2026-02-16"
tags: ["Mathematics", "Calculus", "Analysis"]
---

# Derivatives
## Multivariable Derivatives
### Total Differentiability

Given a real-scalar function $f: \mathbb{R}^n \supset U \mapsto \mathbb{R}$, and a point $\mathbf{a} \in U \in \mathcal{O}$, $f$ is said to be **differentiable** at $\mathbf{a}$ if there is a linear transformation $L$ that satisfies the following limit:
$$
\lim_{\mathbf{x} \to \mathbf{a}} \frac{|| f(\mathbf{x}) - (f(\mathbf{a}) + L(\mathbf{x} - \mathbf{a}))||}{||\mathbf{x} - \mathbf{a}||} = 0
$$
(Remark: this is a special case of Fréchet derivative)

We call $L$ the **derivative** of $f$, and in particular it is unique at interior points of $U$.

# Integration