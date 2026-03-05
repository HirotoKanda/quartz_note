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

Now, 