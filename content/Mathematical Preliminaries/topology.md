---
title: "Topological Spaces"
date: "2026-02-16"
tags: ["Mathematics", "Topology"]
---

# Topological Space

## Definition

Given a set $X$, a pair of sets $(X, \mathcal{O})$ is called a **topological space** if $\mathcal{O}$ is a **family**/ **collection** of subsets of $X$ that satisfies the following properties:

1. $\emptyset \in \mathcal{O}$ and $X \in \mathcal{O}$.

2. The union of any collection of sets in $\mathcal{O}$ is also in $\mathcal{O}$.

$$
O_\lambda \in \mathcal{O}, \lambda \in \Lambda \implies \bigcup_{\lambda \in \Lambda} O_\lambda \in \mathcal{O}
$$

1. The intersection of any finite collection of sets in $\mathcal{O}$ is also in $\mathcal{O}$.

If $O_1, O_2, \cdots, O_n \in \mathcal{O}$, then
$$
\bigcap_{i=1}^n O_i \in \mathcal{O}
$$

in which case, we say that $\mathcal{O}$ is a **topology** on $X$, and the sets in $\mathcal{O}$ are called **open sets** of the topological space $(X, \mathcal{O})$.

## Euclid Space as a Topological Space

### Euclidean Metric

The Euclid space $\mathbb{R}^n$ can be regarded as a topological space by defining the topology $\mathcal{O}$ using **open balls**, which is defined using the **Euclidean metric** $d$ on $\mathbb{R}^n$.

Given two points in $\mathbb{R}^n$, say $x = (x_1, x_2, \cdots, x_n)$ and $y = (y_1, y_2, \cdots, y_n)$, the **Euclidean metric** $d$ is defined as
$$
d(x, y) = \sqrt{\sum_{i=1}^n (x_i - y_i)^2}.
$$

Note that this makes $\mathbb{R}^n$ a **metric space**, which is a special type of topological space, where distance between points is explicitly defined.

### Open Balls

Now, given a point $x \in \mathbb{R}^n$ and a positive real number $r > 0$, we can define the **open ball** centered at $x$ with radius $r$ as:
$$
B(x, r) = \{y \in \mathbb{R}^n | d(x, y) < r\}.
$$
which is the set of all points in $\mathbb{R}^n$ that are within a distance $r$ from the point $x$.

### Open Sets in $\mathbb{R}^n$

Using open balls, we can define an open set in $\mathbb{R}^n$ as follows:
A set $O \subset \mathbb{R}^n$ is an **open set**, if
$$
^{\forall} x \in O, ^{\exists} r > 0, \text{ s.t } B(x, r) \subset O
$$

## Important Notions

### Closed Sets

A set $C \subset X$ is called a **closed set** if its complement in $X$, denoted by $X \setminus C$, is an open set:
$$
C \text{ is closed} \iff X \setminus C \text{ is open}
$$

### Neighborhoods

Given a topological space $(X, \mathcal{O})$, A set $N \subset X$ is called a **neighborhood** of a point $x \in X$ if
$$
^{\exists} O \in \mathcal{O}, \text{ s.t } x \in O \subset N. \iff x \in \operatorname{Int}(N).
$$
where $\operatorname{Int}(N)$ is the **interior** of $N$.
Note that if neighborhood $N$ of $x$ is an open set, then $N$ is called an **open neighborhood** of $x$. If neighborhood $N$ of $x$ is a closed set, then $N$ is called a **closed neighborhood** of $x$.

## Base/ Basis of a Topology

Given a topological space $(X, \mathcal{O})$, a sub-family $\mathcal{B} \subset \mathcal{O}$ is called an open **base** of the topology $\mathcal{O}$, if
$$
^{\forall} O \in \mathcal{O} \text{ and } ^{\forall} p \in O, ^{\exists} B \in \mathcal{B}, \text{ s.t } p \in B \subset O
$$
Or equivalently, if every open set in $\mathcal{O}$ can be expressed as a union of sets in $\mathcal{B}$:
$$
^{\forall} O \in \mathcal{O}, ^{\exists} \{B_\lambda \}_{\lambda \in \Lambda} \subset \mathcal{B}, \text{ s.t } O = \bigcup_{\lambda \in \Lambda} B_\lambda
$$

Note that there could be more than one base for a given topological space $(X, \mathcal{O})$.
However, if one of them happens to be a countable set, then we say that the topological space $(X, \mathcal{O})$ is **second-countable**.

## Example: Euclidean Space $\mathbb{R}^n$ as a Topological Space

Given a point $p$ in an open set $U \subset \mathbb{R}^n$, we can always find an open ball $B(p, r)$ centered at $p$ with radius $r \in \mathbb{Q}^+ $ such that $B(p, r) \subset U$ ([by definition](#open-sets-in) and any open set in $\mathbb{R}^n$ contain a rational point).
Then, fix a point $q \in B(p, r/2)$ ($\iff p \in B(q, r/2)$).
Also, take any point $x \in B(q, r/2)$.
From the triangle inequality, we have
$$
d(p, x) \leq d(p, q) + d(q, x) < \frac{r}{2} + \frac{r}{2} = r
$$
which means that $x \in B(p, r)$, and thus $B(q, r/2) \subset B(p, r) \subset U$.
In summary,
$$
^{\forall} U \in \mathcal{O} \text{ and } ^{\forall} p \in U, \, ^{\exists} B \left(q, \frac{r}{2}\right) \in \mathcal{B}_{\text{rat}}, \text{ s.t } p \in B(q, \frac{r}{2}) \subset U
$$
where
$$
\mathcal{B}_{\text{rat}} := \{B(q, s) | q \in \mathbb{Q}^n, s \in \mathbb{Q}^+\}
$$

This means that $\mathcal{B}_{\text{rat}}$ is a countable base for $(\mathbb{R}^n, \mathcal{O})$, and thus $\mathbb{R}^n$ is a second-countable topological space.

## Hausdoff space

A topological space $(X, \mathcal{O})$ is called a **Hausdorff space** , if for any two distinct points $x, y \in X$, there exists two disjoint open sets $U, V \in \mathcal{O}$ such that $x \in U$ and $y \in V$.
We say that these two points are **separated** by the two open sets $U$ and $V$.
A **regular** Hausdorff space is for any closed sets $C, D \subset X$, there exists two disjoint open sets $U, V \in \mathcal{O}$ such that $C \subset U$ and $D \subset V$.

Again, notice that Euclidean space $\mathbb{R}^n$ is a Hausdorff space, since for any two distinct points $x, y \in \mathbb{R}^n$, we can always find two disjoint open balls $B(x, r)$ and $B(y, r)$ with radius $r < \frac{d(x, y)}{2}$ such that $x \in B(x, r)$ and $y \in B(y, r)$.

## Maps between Topological Spaces

### Continuous Maps

Given two topological spaces $(X, \mathcal{O}_X)$ and $(Y, \mathcal{O}_Y)$, a map $f: X \mapsto Y$ is called **continuous** if
$$
^{\forall} O \in \mathcal{O}_Y, f^{-1}(O) \in \mathcal{O}_X
$$

Equivalently, we can define continuity in terms of neighborhoods:
$$
^{\forall} x \in X, ^{\forall} N_{f(x)} \ni f(x), \, x \in f^{-1}(N_{f(x)})
$$

This reduces to the usual definition of continuity for $f: I \subset\mathbb{R} \mapsto \mathbb{R}$ at a point $x_0 \in I \subset \mathbb{R}$:
$$
^{\forall} \varepsilon > 0, ^{\exists} \delta > 0 \text{ s.t } ^{\forall} x \in I, |x - x_0| < \delta \implies |f(x) - f(x_0)| < \varepsilon
$$

This is because $a \in A \implies f(x) \in B$ is equivalent to $x \in f^{-1}(B) \subset A$.
By extension,
$$
| x - x_0 | < \delta \implies | f(x) - f(x_0) | < \varepsilon \\
\iff f^{-1}(B(f(x_0), \varepsilon)) \subset B(x_0, \delta)
$$
which satisfies the definition of continuity in terms of neighborhoods.

### Properties of Continuous Maps

1. Composition of continous maps is continous.

Given three topological spaces $(X, \mathcal{O}_X)$, $(Y, \mathcal{O}_Y)$ and $(Z, \mathcal{O}_Z)$, and continous maps $f, g$ between them, $f: X \mapsto Y$ and $g: Y \mapsto Z$, the composition of $f$ and $g$, denoted by $g \circ f: X \mapsto Z$, is also continuous:
$$
(g \circ f)^{-1} = f^{-1} \circ g^{-1} \implies ^{\forall} O \in \mathcal{O}_Z, (g \circ f)^{-1}(O) = f^{-1}(g^{-1}(O)) \in \mathcal{O}_X
$$

### Homeomorphisms

Given two topological spaces $(X, \mathcal{O}_X)$ and $(Y, \mathcal{O}_Y)$, a map $f: X \mapsto Y$ is called a **homeomorphism** if:

1. $f$ is bijective
2. $f$ is continuous
3. its inverse map $f^{-1}$ is also continuous.

In this case, we say that $X$ and $Y$ are **homeomorphic**, and denote as:
$$
X \cong Y,
$$

Now, notice that if $f$ is a homeomorphism, $f^{-1}$ is also a homeomorphism.
Similarly to the composition of continuous maps, the composition of homeomorphisms is also a homeomorphism.
