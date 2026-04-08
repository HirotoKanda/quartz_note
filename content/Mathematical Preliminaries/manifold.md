---
title: "Manifolds"
date: "2026-02-16"
tags: ["Mathematics", "Topology", "Manifolds"]
---

# Manifolds

## Introduction

A **manifold** is a convinient mathematical structure for doing calculus: derivatives, integration, etc.
However, to do calculus, we need to introduce coordinates on the space. In short, we want manifolds to be locally like $\mathbb{R}^n$, so that we can introduce coordinates and do calculus on it.

## Definition of Manifolds

A **topological manifold** is a Hausdorff, second-countable topological space that is locally homeomorphic to Euclidean space $\mathbb{R}^n$.

More concretely, when we have a topological manifold $M$, we can take any point $p \in M$ and an open neighborhood $U$ of $p$, and there is a mapping $\varphi: U \mapsto \tilde{U} \subset \mathbb{R}^n$, that "converts" points in $U$ to points in the Euclidean space $\mathbb{R}^n$.
Here, $\varphi$ is called a **coordinate map** of the manifold $M$, and $\tilde{U}$ is an open set in $\mathbb{R}^n$.
![Manifold](pictures/manifold/definition.png)

The pair of open set and the mapping $(U, \varphi)$ is called a **chart** of the manifold $M$.
And specifically for a point $p \in U$, we can write "converted" point $\varphi(p)$ as a coordinate in $\mathbb{R}^n$, i.e. $\varphi(p) = (x^1, x^2, \cdots, x^n)$.
This ordered set of numbers is called the **local coordinate** of $p$ in the chart $(U, \varphi)$.

## Coordinate Transformations

Notice that there are no particular rules for how we choose the coordinate to represent the point $p$.
Any coordinate can be used around $p$, and we can switch between different coordinates by using different coordinate maps.
As to explain, we can take two overlapping charts $(U, \varphi)$ and $(V, \psi)$, where $p \in U \cap V$, and we can use either $\varphi(p)$ or $\psi(p)$ to represent the point $p$:
$$
\varphi(p) = (x^1, x^2, \cdots, x^n), \quad \psi(p) = (y^1, y^2, \cdots, y^n).
$$
![transform](pictures/manifold/transformation.png)

Then, the **coordinate transformation** between $(x^i)$ and $(y^i)$ is given by the composition of the two coordinate maps:
$$
\psi \circ \varphi^{-1}: \tilde{U} \mapsto (M \mapsto) \tilde{V}
$$
First we "pull back" the point $\varphi(p)$ to $M$, and we "push forward" it to $\tilde{V}$, which gives us the coordinate transformation between $(x^i)$ and $(y^i)$:
$$
y^i = \psi \circ \varphi^{-1}(x^j)
$$
The composed map $\psi \circ \varphi^{-1}$ is called the **transition map** between the two charts $(U, \varphi)$ and $(V, \psi)$.
Note that since $\varphi$ and $psi$ are homeomorphisms, the transition map $\psi \circ \varphi^{-1}$ is also a homeomorphism between the two open sets $\tilde{U}$ and $\tilde{V}$ in $\mathbb{R}^n$.

## Differentiable Manifolds

Since the transition map is just a Euclid-to-Euclid map, we can introduce the notion of differentiability.
Take two charts $(U, \varphi)$ and $(V, \psi)$, where $p \in U \cap V$.
If the transition map $\psi \circ \varphi^{-1}$ is a $C^r$-class function from $\mathbb{R}^n \supset \tilde{U} \to \tilde{V} \subset \mathbb{R}^m$, then we say that the two charts are **$C^r$-compatible**.
Note that:

- If $U \cap V = \emptyset$, then the two charts are trivially $C^\infty$-compatible.
- The inverse map $\varphi \circ \psi^{-1}$ is also a $C^r$-class function from $\mathbb{R}^m \supset \tilde{V} \to \tilde{U} \subset \mathbb{R}^n$.

Now, a **$C^r$-class atlas** of a topological manifold $M$ is a collection of charts $\{(U_\alpha, \varphi_\alpha)\}$ such that:

1. The charts are an open covering of the manifold $M$:
   $$
   \bigcup_\alpha U_\alpha = M
   $$
2. Any pair of charts $(U_{\alpha_1}, \varphi_{\alpha_1})$ and $(U_{\alpha_2}, \varphi_{\alpha_2})$ in the atlas are $C^r$-compatible.

![Atlas](pictures/manifold/atlas.png)

For a given manifold $M$, it is possible that more than one atlas can be defined on it, and we can consider the compatibility of different atlases:
given two atlases $\mathcal{A}_1$ and $\mathcal{A}_2$ on the same manifold $M$, if their union $\mathcal{A}_1 \cup \mathcal{A}_2$ is also an atlas, then we say that $\mathcal{A}_1$ and $\mathcal{A}_2$ are **compatible**.

Furthermore, given an atlass $\mathcal{A}$ on a manifold $M$, we can consider the union of all atlases that are compatible with $\mathcal{A}$, and this set is called the **maximal atlas** of $\mathcal{A}$, denoted as $\mathcal{A}_{\text{max}}$ or $\mathcal{A}^+$.

A topological manifold $M$ equipped with a $C^r$-class maximal atlas is called a **$C^r$-class manifold**.

If $M$ has a $C^\infty$-class maximal atlas, then we say that $M$ is a **smooth manifold**.


## $C^r$-class Functions between Manifolds

Consider a map $f: M \to N$ where $M$ and $N$ are two $C^s$-class manifolds, with maximal atlases $\mathcal{A}_M$ and $\mathcal{A}_N$ respectively.
Take a point $p$ in $M$, and a chart $(U_p, \varphi)$ around $p$. Then, we consider a mapped point $f(p)$ in $N$, and a chart $(V_{f(p)}, \psi)$ around $f(p)$.
Note that we take $U$ and $V$ such that $f(U) \subset V$, so that we can write the map $f$ in terms of the coordinates of the two charts.
Then, we can write the map $f$ in terms of the coordinates as:
$$
\psi(f(p)) = \psi (f \circ \varphi^{-1}(x^i))
$$
where $(x^i) = \varphi(p)$.
Note that $\psi(f \circ \varphi^{-1}) = \psi \circ f \circ \varphi^{-1}$ is a map from $\mathbb{R}^n \supset \tilde{U}_p$ to $\mathbb{R}^m \supset \tilde{V}_{f(p)}$.
If the map $\psi \circ f \circ \varphi^{-1}: \mathbb{R}^n \supset \tilde{U}_p \to \mathbb{R}^m \supset \tilde{V}_{f(p)}$ is a $C^s$-class function in the Euclidean space, we say that 


## Tangent Spaces

Consider a $C^r$-class manifold $M$ and a point $p \in M$.
Then, we have a set of parametrized $C^r$-class curves that passes through $p$:
$$
\Gamma_p := \left\{ 
c | \varepsilon >0, c: (-\varepsilon, \varepsilon) \to U_p \subset M, c(0) = p, c \in C^r
\right\}
$$
and a $C^1$-class function $f: U \to \mathbb{R}$, 