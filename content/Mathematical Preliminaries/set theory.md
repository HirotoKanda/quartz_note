---
title: "Basic Set Theory"
date: "2026-02-16"
tags: ["Mathematics"]
---
Set theory gives us the fundamental way to discuss many mathematical objects used in physics.
We cover the basic concepts that we will need to discuss the mathematical structures in physics, such as groups, vector spaces, and manifolds.

# Sets and Elements

## Sets

A **set** is a collection of mathematical objects, that can be defined rigourously.
Such objects in a set are called **elements** of the set.
 
### Subsets

Take two sets $A$ and $X$, as well as an element of $A$, say $a$.
We denote that $a$ is an element of $A$ by $a \in A$, and that $a$ is not an element of $A$ by $a \notin A$.
If every element of $A$ is also an element of $X$, we say that $A$ is a **subset** of $X$, and denote it by $A \subset X$.
More formally,
$$
^{\forall} a \in A, a \in X \implies A \subset X
$$
If $A$ is a subset of $X$, but $A$ is not equal to $X$, we say that $A$ is a **proper subset** of $X$, and denote it by $A \subsetneq X$.

Also, note that if $A \subset X$ and $X \subset A$, then $A = X$. This means that $X$ is a subset of $X$ itself.

### Complement of a Set

Given a set $X$ and a subset $A \subset X$, we can define the **complement** of $A$ in $X$, denoted by $X \setminus A$, as the set of all elements in $X$ that are not in $A$:
$$
X \setminus A = \{x \in X | x \notin A\}
$$

### Power Set

Given a set $X$, we can define the **power set** of $X$, denoted by $2^X$, as the set of all subsets of $X$:
$$
2^X = \{A | A \subset X\}
$$

Note that the power set of $X$ includes both the empty set $\emptyset$ and the set $X$ itself, since both of them are subsets of $X$.

### Special Sets

There are a few special sets we will encounter in both mathematics and physics.

- The **empty set** $\emptyset$ is the set that has no elements.
- The set of **natural numbers** $\mathbb{N}$ is the set of all positive integers, i.e. $\{1, 2, 3, \cdots\}$.
- The set of **integers** $\mathbb{Z}$ is the set of all integers, i.e. $\{-2, -1, 0, 1, 2, \cdots\}$.
- The set of **rational numbers** $\mathbb{Q}$ is the set of all numbers that can be expressed as a fraction of two integers, i.e. $\{\frac{p}{q} | p \in \mathbb{Z}, q \in \mathbb{Z} \setminus \{0\}\}$.
- The set of **real numbers** $\mathbb{R}$ is the set of all numbers that can be represented on the number line, including both rational and irrational numbers.
- The set of **complex numbers** $\mathbb{C}$ is the set of all numbers that can be expressed in the form $a + bi$, where $a$ and $b$ are real numbers, and $i$ is the imaginary unit satisfying $i^2 = -1$.

## Union and Intersection of Sets

Given two sets $A$ and $B$, we can define the **union** of $A$ and $B$, denoted by $A \cup B$, as the set of all elements that are in $A$ or in $B$ (or in both). Formally,
$$
A \cup B = \{x | x \in A \textbf{ or } x \in B\}
$$

The **intersection** of $A$ and $B$, denoted by $A \cap B$, is the set of all elements that are in both $A$ and $B$. Formally,
$$
A \cap B = \{x | x \in A \textbf{ and } x \in B\}
$$
When the intersection of two sets is empty, we say that the two sets are **disjoint**, then union of two disjoint sets is denoted by $A \sqcup B$.

### (Cartesian/ Direct) Product of Sets

Given multiple sets, we can define the **Cartesian/ direct product** of those sets.
Let $X_i$ be a set for $i = 1, 2, \cdots, n$, then the Cartesian product of those sets is defined as
$$
X_1 \times X_2 \times \cdots \times X_n = \{(x_1, x_2, \cdots, x_n) | x_i \in X_i \text{ for } i = 1, 2, \cdots, n\}
$$
We may also denote this as follows:
$$
\prod_{i \in I} X_i = \{(x_i)_{i \in I} | x_i \in X_i \text{ for all } i \in I\}, \text{ where } I = \{1, 2, \cdots, n\}
$$
In these notations, the set $I$ is called the **index set**, where for each index $i$ in $I$, we have a corresponding set $X_i$.

## Maps

### Definition of Maps

Given two sets $X$ and $Y$, a **map** from $X$ to $Y$ is a relation that assigns to each element of $X$ a unique element of $Y$.
We denote such a map $\varphi$ as follows:
$$
\varphi: X \ni x \mapsto y = \varphi(x) \in Y
$$

Here, $X$ is called the **domain** of the map $\varphi$, and $Y$ is called the **range** of $\varphi$. $\varphi(X)$ is called the **image** of $\varphi$.
When $Y$ is a set of numbers such as $\mathbb{R}$ or $\mathbb{C}$, we may also call $\varphi$ a **function**.

### Images and Inverse Images

Given a map $\varphi: X \to Y$, we can define the **image** of a subset $A \subset X$ under $\varphi$ as follows:
$$
\varphi(A) = \{\varphi(a) | a \in A\} \subset Y
$$
Similarly, we can define the **inverse image** of a subset $B \subset Y$ under $\varphi$ as follows:
$$
\varphi^{-1}(B) = \{x \in X | \varphi(x) \in B\} \subset X
$$

### Injective, Surjective, and Bijective Maps

#### Injective Map

A map $\varphi: X \to Y$ is called **injective** (or one-to-one) if for $x_1, x_2 \in X$,
$$
\varphi(x_1) = \varphi(x_2) \implies x_1 = x_2
$$ 
or equivalently,
$$
x_1 \neq x_2 \implies \varphi(x_1) \neq \varphi(x_2)
$$

#### Surjective Map

A map $\varphi: X \to Y$ is called **surjective** (or onto) if 
$$ 
^{\forall} y \in Y, ^{\exists} x \in X, \varphi(x) = y
$$
or equivalently,
$$
\varphi(X) = Y.
$$

#### Bijective Map

A map $\varphi: X \to Y$ is called **bijective** if it is both injective and surjective.
In that case, we can define the **inverse map** $\varphi^{-1}$:
$$
\varphi^{-1}: Y \ni y \mapsto x \in X, \text{ where } \varphi(x) = y
$$

## Equivalence Relation

### Definition of Equivalence Relation

Given a set $X$, an **equivalence relation** $\sim$ on $X$ is a relation that satisfies the following three properties:

1. **Reflexivity**: For all $x \in X$, $x \sim x$.
2. **Symmetry**: For all $x, y \in X$, if $x \sim y$, then $y \sim x$.
3. **Transitivity**: For all $x, y, z \in X$, if $x \sim y$ and $y \sim z$, then $x \sim z$.

### Equivalence Classes and Quotient Sets

#### Equivalence Class

Given an equivalence relation $\sim$ on a set $X$, we can define the **equivalence class** $\mathcal{P}_x = [x]$ of $x \in X$ as follows:
$$
\mathcal{P}_x = [x] := \{y \in X | y \sim x\}
$$
We say that $x$ **represents** the equivalence class $\mathcal{P}_x = [x]$.

#### Quotient Set

The set of all equivalence classes of $X$ under the equivalence relation $\sim$ is called the **quotient set** of $X$ by $\sim$, denoted by $X / \sim$:
$$
X / \sim = \{\mathcal{P}_x | x \in X\}
$$
