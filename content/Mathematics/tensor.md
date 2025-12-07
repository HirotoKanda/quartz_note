---
title: What is a Tensor?
author: Jai Nasu
date: 2025-12-04
tags: [tensor, linear algebra, relativity]
---

## What is a tensor?

Very often in a physics context, we see a very abstract definition of a tensor based on coordinate transformation ${x^i} \to {x'^{\, i}}$:
$$
T'^{\, ij} = \frac{\partial x'^i}{\partial x^k} \frac{\partial x'^j}{\partial x^l} T^{kl}
$$

But where does this definition come from?

It may be easier to start with an example:
> [!Example]e.g.) Dot product: **(0, 2) tensor on** $\mathbb{R}$
> For example, consider the dot product of two vectors $\vec{x}, \vec{y} \in \mathbb{R}^n$:
> $$
> D(\vec{x}, \vec{y}) := \vec{x} \cdot \vec{y} = x^i y^i
> $$
> where $x_i, y_i$ are the **components** of $\vec{x}, \vec{y}$ in some basis.
It is called a (0, 2) tensor because it takes two vectors as input and produces a real number, a scalar as output.

Importantly, the dot product is **multilinear**: for $a, b \in \mathbb{R}$ and $\vec{u}, \vec{v}, \vec{x}, \vec{y} \in \mathbb{R}^n$,
$$
\begin{aligned}
D(a \vec{x} + \vec{v}, \vec{y}) &= a D(\vec{x}, \vec{y}) + D(\vec{v}, \vec{y}) \\
D(\vec{x}, b \vec{y} + \vec{u}) &= b D(\vec{x}, \vec{y}) + D(\vec{x}, \vec{u})
\end{aligned}
$$

This is an important part of definition of a tensor: multilinearity.

In general, a $(0, N)$ tensor is a multilinear map that takes $N$ vectors as input and produces a scalar as output.

## Vector Space

Before going further, let's briefly review the definition of a vector space, which is essential to understand tensors in this linear algebraic context.
> [!Definition] Definition: Vector Space
> A vector space $V$ over $\mathbb{R}$ (or $\mathbb{C}$) is a set equipped with two operations:
>
> 1. **Vector Addition**: An operation $\oplus: V \times V \to V$:
> For $\vec{u}, \vec{v} \in V$,
>
> $$
> \vec{u} \oplus \vec{v} \in V
> $$
>
> 2. **Scalar Multiplication**: An operation $\odot: \mathbb{R} \times V \to V$
>
> $$
> a \odot \vec{v} \in V.
> $$
> $(V, \oplus, \odot)$ must satisfy the following axioms for all $\vec{u}, \vec{v}, \vec{w} \in V$ and $a, b \in \mathbb{R}$:
> - **Commutativity** : 
> $$
> \vec{u} \oplus \vec{v} = \vec{v} \oplus \vec{u}
> $$
> - **Associativity** : 
> $$
> (\vec{u} \oplus \vec{v}) \oplus \vec{w} = \vec{u} \oplus (\vec{v} \oplus \vec{w})
> $$
> - **Additive Identity** : There exists an element $\vec{0} \in V$ such that
> $$
> \vec{v} \oplus \vec{0} = \vec{v} 
> $$
> - **Additive Inverse** : $\vec{v}^{-1} \in V$ exists such that
> $$
> \vec{v} \oplus \vec{v}^{-1} = \vec{0}
> $$
> We may also write $\vec{u}^{-1} = -\vec{u}$.
> - **Distributivity (1)** :
> $$ 
> a \odot ( \vec{u} \oplus \vec{v}) = a \odot \vec{u} \oplus a \odot \vec{v}
> $$
> - **Distributivity (2)** :
> $$
> (a + b) \odot \vec{v} = a \odot \vec{v} \oplus b \odot \vec{v}
> $$
> - **Multiplicative Identity** :
> There exists an element $\mathbf{1} \in \mathbb{R}$ such that
> $$
> \mathbf{1} \odot \vec{v} = \vec{v}
> $$


Many things can be vector space. 
Our usual $n$-dimensional $\mathbb{R}^n$ with usual addition and scalar multiplication is a vector space.
The set of all polynomials on $[0, 1] \subset \mathbb{R}$ is also a vector space with pointwise addition and scalar multiplication:
$$
(f \oplus g)(x) := f(x) + g(x), \quad (a \odot f)(x) := a \cdot f(x)
$$
This means that when we add $f$ and $g$ and evaluate at $x$, it is the same as evaluating $f$ and $g$ at $x$ first, then adding the results.

A tensor can be defined on such polynomial vector space as well:
> [!Example] e.g.) Tensor on Polynomial Vector Space
> Consider the vector space $\mathbb{P}$ of all polynomials on $[0, 1]$.
> A (0, 2) tensor $T: \mathbb{P} \times \mathbb{P} \to \mathbb{R}$ can be defined as
> $$
> T(f, g) := \frac{df}{dx}(3) \cdot \frac{dg}{dx}(3)
> $$
> From the linearity of differentiation, it is easy to check that $T$ is multilinear, and hence a (0, 2) tensor on $\mathbb{P}$.
> for example, for $f = x^2, g = x^3$,
> $$
>\begin{aligned}
> T(f, g) &= \frac{df}{dx}(3) \cdot \frac{dg}{dx}(3) \\
>         & = \frac{d(x^2)}{dx}(3) \cdot \frac{d(x^3)}{dx}(3) \\
>        & = 2 (3) \cdot 3 (3^2) = 54 \in \mathbb{R}
> \end{aligned}
> $$
> if we take $h = x^4$, then we can also see that 
> $$
> T (f \oplus h, g) = T(f, g) + T(h, g)
> $$

## Linear Maps

So far, we have seen what a vector is, but we also had another keyword in the definition of a tensor: linear map.
> [!Definition] Definition: Linear Map
> A map $\varphi$ between two vector spaces $V$ and $U$ on $\mathbb{R}$; $\varphi: V \mapsto U$ is called a linear map, if for all $\vec{v_1}, \vec{v_2} \in V$ and $\lambda \in \mathbb{R}$,
>
> - **Additivity** :
>
> $$
> \varphi(\vec{v_1} \oplus_V \vec{v_2}) = \varphi(\vec{v_1}) \oplus_U \varphi(\vec{v_2})
> $$
>
> - **Homogeneity** :
>
> $$
> \varphi(\lambda \odot_V \vec{v}) = \lambda \odot_U \varphi(\vec{v})
> $$
> where $\oplus_V, \odot_V$ and $\oplus_U, \odot_U$ are the addition and scalar multiplication in $V$ and $U$, respectively. Note that $\phi(\vec{v}) \in U$.

This linear map can be defined between any two vector spaces: $\mathbb{R}^n \mapsto \mathbb{P}$, $\mathbb{P} \mapsto \mathbb{R}^m$, or even $\mathbb{P} \mapsto \mathbb{P}$.

## Dual Vector Space

Now, before properly defining tensors, we need one more concept: dual vector space.

Consider a column vector $\vec{v} \in \mathbb{R}^3$:
$$
\vec{v} = \begin{pmatrix}
v_1 \\
v_2 \\
v_3
\end{pmatrix}
$$
A "natural" linear map from $\mathbb{R}^3$ to $\mathbb{R}$ is the dot product with another vector $\vec{u} \in \mathbb{R}^3$:
$$
\varphi_{\vec{u}}: \mathbb{R}^3 \to \mathbb{R}, \quad \varphi_{\vec{u}}(\vec{v}) := \vec{u} \cdot \vec{v} = u_1 v_1 + u_2 v_2 + u_3 v_3
$$
Since $\vec{v}$ is a column vector, one way we can represent $\varphi_{\vec{u}}$ is to use a row vector:
$$ 
\varphi_{\vec{u}} (\vec{v}) = \begin{pmatrix}
u_1 & u_2 & u_3
\end{pmatrix}
\begin{pmatrix}
v_1 \\
v_2 \\
v_3
\end{pmatrix}
$$
so that the linear map can be expressed simply as matrix multiplication.

But since row vectors are also set of 3 real numbers, they also form a vector space.
This vector space formed by such row vectors is a special case of **dual vector space**:
> [!Definition] Definition: Dual Vector Space
> Given a vector space $(V, +, \cdot)$ over $\mathbb{R}$, its dual vector space $V^*$ is the set of all linear maps from $V$ to $\mathbb{R}$:
> $$
> V^* := \{ \varphi: V \to \mathbb{R} \mid \varphi \text{ is a linear map} \}
> $$
> with addition and scalar multiplication $(\oplus, \odot)$.

An element of a dual vector space is called a **covector** or **1-form** or **differential form**.

> [!Example] e.g.) Covector on $\mathbb{P}$
> Consider the vector space $\mathbb{P}$ of all polynomials on $[0, 1]$.
> One example of a linear map is the integral $I$:
> $$
> I: \mathbb{P} \to \mathbb{R} \quad 
> I[f] := \int_0^1 f(x) dx
> $$
> This kind of linear map is also called a **functional**, where the input is a function and the output is a scalar.
> From the linearity of integration, it is easy to check that $I$ is a linear map, and hence an element of the dual vector space $\mathbb{P}^*$, and $I$ is a covector.

Also, gradient of a scalar function is a covector:
> [!Example] e.g.) Gradient as a Covector
> Consider a scalar function $f: \mathbb{R}^3 \to \mathbb{R}$.
> Its gradient $\nabla f$ is defined as
> $$
> \nabla f := \begin{pmatrix}
> \frac{\partial f}{\partial x_1} \\[8pt]
> \frac{\partial f}{\partial x_2} \\[8pt]
> \frac{\partial f}{\partial x_3}
> \end{pmatrix}
> $$
> For a vector $\vec{v} \in \mathbb{R}^3$, the directional derivative of $f$ along $\vec{v}$ is given by
> $$
> D_{\vec{v}} f = \nabla f \cdot \vec{v} \in \mathbb{R}
> $$
> This defines a linear map from $\mathbb{R}^3$ to $\mathbb{R}$, and hence $\nabla f$ can be considered as a covector in the dual vector space $(\mathbb{R}^3)^*$. (More on this later.)
> [!Example] e.g.) Covector on $\mathbb{R}^n$
> Consider $V = \mathbb{R}^n$.
> If we consider a function $f: \mathbb{R}^n \to \mathbb{R}$ defined as
> $$
> f(\vec{x}) := \vec{a} \cdot \vec{x} = \vec{a}^T \vec{x} = a_i x^i, \quad \vec{a} \in \mathbb{R}^n,
> $$
> $f$ is a covector.
> Now, this $f$ is essentially the same as the row vector $\vec{a}^T$, so if we take column vectors as elements of $\mathbb{R}^n$, then the dual vector space $(\mathbb{R}^n)^*$ can be identified with the set of row vectors.

## Definition of Tensor

In the beginning, we defined $(0, N)$ tensors as multilinear maps that take $N$ vectors as input and produce a scalar as output.
With the concept of dual vector space, we can finally fill the 0 slot:
> [!Definition] Definition: (M, N) Tensor
> Given a vector space $V$ over $\mathbb{R}$, an $(M, N)$ tensor $T$ is a multilinear map:
> $$
> T: \underbrace{V^* \times V^* \times \cdots \times V^*}_{M \text{ times}} \times \underbrace{V \times V \times \cdots \times V}_{N \text{ times}} \to \mathbb{R}
> $$
> that takes $M$ covectors and $N$ vectors as input and produces a scalar as output.

## Components of a Vector

Now that we have properly defined tensors, let us try to understand where the "transformation definition" of tensor is coming from.
To do this, it is useful to look back on vectors both geometrically and algebraically.

Geometrically speaking, a vector $\vec{v}$ is an "arrow".
We can give this arrow an algebraic representation by choosing a **coordinate system** and a **basis** of the vector space:
> [!Definition] Definition: Basis
> For $\mathbb{R}^n$, a set of $n$ vectors $\{ \vec{e_1}, \vec{e_2}, \ldots, \vec{e_n} \}$ that are linearly independent and span the whole space is called a basis.
> This means that any vector $\vec{v} \in \mathbb{R}^n$ can be expressed as a linear combination of the basis vectors:
> $$
> \vec{v} = v^i \vec{e_i}
> $$
> where $v_1, v_2, \ldots, v_n \in \mathbb{R}$ are called the **components** of $\vec{v}$ in this basis.

As for coordinate system, we can really take any coordinate system, such as Cartesian, polar, spherical, or even curvilinear coordinates.
For basis, in many situations we work with **orthogonal basis** or **orthonormal basis**

For a vector space $V$ with basis $\{ \vec{e_1}, \vec{e_2}, \ldots, \vec{e_n} \}$, its dual space $V^*$ star can have a corresponding **dual basis** $\{\tilde{\varepsilon}^1, \tilde{\varepsilon}^2, \ldots, \tilde{\varepsilon}^n \}$ defined as:
> [!Definition] Definition: Dual Basis
> Given a basis $\{ \vec{e_1}, \vec{e_2}, \ldots, \vec{e_n} \}$ of a vector space $V$,
> its dual basis $\{\tilde{\varepsilon}^1, \tilde{\varepsilon}^2, \ldots, \tilde{\varepsilon}^n \}$ in the dual vector space $V^*$ is defined such that
> $$
> \tilde{\varepsilon}^i (\vec{e_j}) = \delta^i_j =
> \begin{cases}
> 1 & \text{if } i = j \\
> 0 & \text{if } i \neq j
> \end{cases}
> $$

Using this dual basis, any covector $\varphi \in V^*$ can be expressed as a linear combination of the dual basis vectors:
$$
\tilde{\omega} = \omega_j \tilde{\varepsilon}^{\, j}
$$

Now, consider, as an example, a (1, 1) tensor $T: V^* \times V \to \mathbb{R}$, and $\vec{v} \in V$ and $\tilde{\omega} \in V^*$.
Let us further choose an arbitrary basis $\{\vec{e}_i \}$ for $V$ and its dual basis $\{\tilde{\varepsilon}^i \}$ for $V^*$.
Then, we can express $\vec{v}$ and $\tilde{\omega}$ in terms of the basis and dual basis:
$$
\vec{v} = v^i \vec{e}_i, \quad \tilde{\omega} = \omega_j \tilde{\varepsilon}^j
$$
Then from the multilinearity, the tensor $T$ can be evaluated as:
$$
\begin{aligned}
T(\tilde{\omega}, \vec{v})
& = T(\omega_j \tilde{\varepsilon}^{\, j}, v^i \vec{e}_i) \\
& = \omega_j v^i T(\tilde{\varepsilon}^{\, j}, \vec{e}_i)
\end{aligned}
$$

Here, we can define the **components** of the tensor $T$ in this basis as:
$$
T^i_{j} := T(\tilde{\varepsilon}^{\, i}, \vec{e}_j)
$$
so that we can write the output of the tensor as the linear combination of input vector components and tensor components:
$$
T(\tilde{\omega}, \vec{v}) = \omega_j v^i T^{i}_{j}
$$

A $(0, 1)$ tensor takes a vector $\vec{v} \in V$ as input and produces a scalar as output, which is exactly the definition of a covector/ 1-form:
$$
\tilde{\omega}(\vec{v}) = \omega_i v^i
$$
where we defined the components of the covector as $\omega_i := \tilde{\omega}(\vec{e}_i)$.
Here, we can change the perspective and think of $\vec{v}$ as the linear map from $V^*$ to $\mathbb{R}$, which takes a covector as input and produces a scalar as output:
$$
\vec{v}(\tilde{\omega}) = v^i \omega_i.
$$

Thus, a $(1, 0)$ tensor, that takes a covector $\tilde{\omega} \in V^*$ as input and produces a scalar as output:
$$
\psi(\tilde{\omega}) = \varphi^i \omega_i
$$
is exactly the same as a vector, or $(1, 0)$ tensor.

Now, what happens if we only input a vector to a (1, 1) tensor?
Let us see:
$$
\begin{aligned}
S(\vec{v}) &:= T(\tilde{\omega}, \vec{v}) \\
&= \omega_j v^i T^{i}_{j} \\
&= v^i \left( T^{i}_{j} \omega_j \right)
\end{aligned}
$$
If we set $S^i := T^{i}_{j} \omega_j$, then we can see that $S(\vec{v})$ has the same form as a covector acting on a vector:
$$
S(\vec{v}) = v^i S_i
$$
This means that $S$ is a covector, or a (0, 1) tensor.
Similarly, if we only input a covector to a (1, 1) tensor, that becomes a vector, or a (1, 0) tensor.

Note that we can still choose any coordinate system and basis we like, so this expression is actually independent of the choice of coordinate system and basis, which then must hold for any coordinate system and basis.

So, what happens if we change the coordinate system and basis?
To explain this, we need to take some ideas from differential geometry.

## Tangent Space

Consider $M = \mathbb{R}^3$.
If a particle with position vector $\vec{r}{t}$ is moving in $M$, then its path is a curve in $M$, parametrized by time $t$:
$$
\gamma = \{ \vec{r}(t) \in M \mid t \in \mathbb{R} \}
$$

Roughly speaking, each component of the position vector $\vec{r}$ has units of length (e.g. meters).
In simple mechanics, we consider the velocity vector $\vec{v} = \frac{d\vec{r}}{dt}$, which has units of length/time (e.g. meters/second).

Now, we ask that if these vectors $\vec{r}$ and $\vec{v}$ are really in the same vector space $M$?
Obviously, they have different units, so it may be more natural to think that they belong in different vector spaces.
We know that $\vec{r}$ is in $M = \mathbb{R}^3$, but where does $\vec{v}$ belong to?

The answer is the **tangent space** at point $\vec{r} \in M$, denoted by $T_{\vec{r}} M$.
> [!Definition] Definition: Tangent Space
> Given a manifold $M$ and a point $p \in M$, the tangent space at $p$, denoted by $T_p M$, is the vector space consisting of all tangent vectors at point $p$.

Intuitively, we think that on the curve $\gamma$, the change in position within time $dt$ is given by
$$
d\vec{r}(t) = \vec{v}(t) dt.
$$

At each point on the curve, we can consider the tangent space where the velocity vector lives.
Physically, we may only have 1 velocity vector for each point on the curve $\gamma$, but mathematically, velocity $\vec{v}(t)$ is just a vector with 3 components.
So, at each point $\vec{r} \in M$, we can imagine any velocity vector $\vec{v} \in T_{\vec{r}} M$ (not just the actual, real velocity of the particle at that point).

This is actually not constrained to a single curve.
When we think of, for example, a fluid flow in $M = \mathbb{R}^3$, at each point $\vec{x} \in M$, there is a velocity vector $\vec{u}$, which lives in the tangent space, "attached" to $\vec{x}$.

In electromagnetism, we see electromagnetic field $\vec{E}, \vec{B}$ defined on every point in $M = \mathbb{R}^3$, which by the same logic, also live in the tangent space at each point.

## Tangent Vector Bundle

Now that we have this set of points $\vec{x} \in M$ and its corresponding tangent spaces $T_{\vec{x}} M$, we can combine them together to form the **tangent vector bundle**, or simply the **tangent bundle**.

We denote the tangent bundle by $TM$:
> [!Definition] Definition: Tangent Bundle
> Given a manifold $M$, the tangent bundle $TM$ is the disjoint union of all tangent spaces at every point in $M$:
> $$
> TM := \bigsqcup_{\vec{x} \in M} T_{\vec{x}} M = \bigcup_{\vec{x} \in M} \{ (\vec{x}, v) \mid v \in T_{\vec{x}} M \}
> $$

If you have heard of "configuration space" in classical mechanics, it is essentially the same as the tangent bundle of the position space.
We have every possible pair of position and velocity vectors $(\vec{r}, \vec{v})$ in the configuration space, which is exactly what the tangent bundle $TM$ is.
The collection of pairs are not limited to the actual motion of a particle in our universe, but it also includes all possible and even "impossible" or "imaginary" pairs of position and velocity vectors.

When we want to solve for the motion of a particle, we need to carefully choose the correct pairs of $(\vec{x}, \vec{v})$ that satisfy the equations of motion.
This is called selecting a **section** of the tangent bundle: for every $\vec{x} \in M$, we choose one value of $\vec{v} \in T_{\vec{x}} M$.
> [!Definition] Definition: Section of a Bundle
> Given a tangent bundle $TM$ over a manifold (our physical space) $M$, a section $\sigma$ is a map from the manifold $M$ to the tangent bundle $TM$:
> $$
> \sigma: M \to TM, \quad \sigma(\vec{x}) = (\vec{x}, \vec{v})
> $$

This velocity vector is not limited to the velocity of a particle moving in $M$, but can also be any "vector field" defined on $M$.

In the context of vector fields, a section $\sigma$ is equivalent to assigning a vector $\vec{F}(\vec{x}) \in T_{\vec{x}} M$ to each point $\vec{x} \in M$:
$$
\vec{F}: M \to T_{\vec{x}} M, \quad \vec{F}(\vec{x}) \in T_{\vec{x}} M
$$

## Basis of Tangent Space

Now, coming back to the example of a particle moving in $M = \mathbb{R}^3$, at each point $\vec{r}(t) \in M$, we have the tangent space $T_{\vec{r}} M$.

In the tangent space $T_{\vec{r}} M$, we can choose a basis.
An intuitive choice is the basis vectors for usual Cartesian coordinates:
$$
\vec{v} = v^i \vec{e}_i
$$

It is certainly a valid choice, but in the context of differential geometry, we can introduce a more "natural" or robust choice of basis.

Consider a derivative of a scalar function $f: M \to \mathbb{R}$ along the path of the particle $\gamma$:
$$
\begin{aligned}
\frac{d}{dt} f(\vec{r}(t))
&= \frac{d x^i}{dt} \frac{\partial f}{\partial x^i}  \\
&= v^i \frac{\partial}{\partial x^i} f(\vec{r}(t)) = \vec{v} \cdot \nabla f
\end{aligned}
$$
where the velocity vector $\vec{v} = \frac{d\vec{r}}{dt}$ (tangent of the curve).
Note that velocity vector $\vec{v}$ takes 3 real numbers as components $v^1, v^2, v^3$, which makes the tangent space $T_{\vec{r}} M = \mathbb{R}^3$.

Notice that $\vec{v} \cdot \nabla$ is a differential operator on $f$, but we have 3 scalars that uniquely determine this operator: $v^1, v^2, v^3$ (which follows from the orthogonality of partial derivatives $\frac{\partial}{\partial x^i}$).

This suggests that the set of directional derivative operator
$$
D_{\vec{x}} \mathbb{R}^3 = \{\vec{v} \cdot \nabla | \vec{v} \in \mathbb{R}^3 \}
$$
forms a vector space, with three dimensions, just like $T_{\vec{r}} M$.

This leads to **isomorphism** between the tangent space $T_{\vec{x}} M$ and the vector space formed by the directional derivative operators at point $\vec{x}$(not limited to the particle path).
In short, if we take the basis of $T_{\vec{x}} M$ as
$$
\vec{e}_i := \frac{\partial}{\partial x^i},
$$
the two vector spaces, $T_{\vec{x}} M$ and $D_{\vec{x}} M$, are completely identical in terms of structure.

This isomorphism is very useful, because when we change the basis and coordinate in the tangent space, we can just calculate how the partial derivative operators change using chain rule.

Let us see how this works in a little general case.
Assume that we transform our coordinate from $x^i$ to $x'^{\, i}$.
Further assume that the transformation is bijective and smooth, so that there is an inverse transformation and differentiation is well-defined.
Then, from the chain rule,
$$
\frac{\partial}{\partial x'^{\, i}} = \frac{\partial x^j}{\partial x'^{\, i}} \frac{\partial}{\partial x^j}
$$

Since we can switch between usual basis and the derivative operator basis using this isomorphism, the new basis vectors $\vec{e}'_i$ in the new coordinate system can be expressed in terms of the old basis vectors $\vec{e}_j$ as:
$$
\vec{e}'_i = \frac{\partial x^j}{\partial x'^{\, i}} \vec{e}_j
$$
This is how basis vectors in the tangent space transform under coordinate transformation.

Any vector that has the same transformation property as the basis vectors is called a **covariant vector** (meaning, "transforming together with the basis") and we denote it with lower indices:
> [!Definition] Definition: Covariant Vector
> A vector $\vec{v} \in T_{\vec{x}} M$ is called a **covariant vector** if its components transform under coordinate transformation ${x^i} \to {x'^{\, i}}$ as:
>
> $$
> \begin{aligned}
> v'_{i} = \frac{\partial x^j}{\partial x'^{\, i}} v_{j}
> \end{aligned}
> $$

So, we mentioned that this transformation of basis vectors have inverse transformation:
$$
\frac{\partial}{\partial x^j} = \frac{\partial x'^{\, k}}{\partial x^j} \frac{\partial}{\partial x'^{\, k}}
$$
If we remember that for a coordinate transformation $\phi$, its inverse transformation is denoted by $\phi^{-1}$, which satisfy:
$$
\phi \circ \phi^{-1} = \phi^{-1} \circ \phi = \mathbf{I}
$$
thus if we just combine the two transformations, we must get the identity transformation:
$$
\frac{\partial}{\partial x^i} = \frac{\partial x'^{\, k}}{\partial x^i} \frac{\partial x^j}{\partial x'^{\, k}} \frac{\partial}{\partial x^j}
$$
Let us then compare this with the identity transformation (doing nothing):
$$
\frac{\partial}{\partial x^i} = \delta_i^j \frac{\partial}{\partial x^j}
$$
By comparison, we get our relation between forward and inverse transformation:
$$
\frac{\partial x'^{\, k}}{\partial x^i} \frac{\partial x^j}{\partial x'^{\, k}} = \delta_i^j
$$
The factor $\frac{\partial x'^{\, k}}{\partial x^i}$ is the inverse of the basis vector transformation $\frac{\partial x^j}{\partial x'^{\, k}}$.

We can follow the same logic when we consider the identity transformation for the new coordinates:
$$
\begin{aligned}
\frac{\partial}{\partial x^{\prime \, i}} 
&= \frac{\partial x^{\prime \, j}}{\partial x^{\prime \, i}} \frac{\partial}{\partial x^{\prime \, j}} \\
&= \underbrace{\frac{\partial x^k}{\partial x^{\prime \, i}} \frac{\partial x^{\prime \, j}}{\partial x^k}}_{\delta_i^j} \frac{\partial}{\partial x^{\prime \, j}}
\end{aligned}
$$

Geometrically speaking, vectors are "arrows", independent of basis.
When we change the basis, for two representations of the arrow in different basis to represent the same arrow, their components must also change to compensate:
$$
\begin{aligned}
\vec{v} 
&= v^i \vec{e}_i & &= v'^{\, j} \vec{e}'_j \\
&= v^k \vec{e}_k & &= v'^{\, j} \frac{\partial x^i}{\partial x'^{\, j}} \vec{e}_i
\end{aligned}
$$
By comparison,
$$
\begin{aligned}
    v^k 
    &= v'^{\, j} \frac{\partial x^k}{\partial x'^{\, j}} \\
\implies 
\frac{\partial x'^{\, i}}{\partial x^k} v^k 
&= \frac{\partial x'^{\, i}}{\partial x^k} \frac{\partial x^k}{\partial x'^{\, j}} v'^{\, j}
\end{aligned}
$$
we notice that the partial derivative factors are identical to $\delta_j^i$, so we get the transformation rule for vector components (note we switch $k$ to $j$ as dummy index):
$$
v'^{\, i} = \frac{\partial x'^{\, i}}{\partial x^j} v^j
$$
If we compare this the covariant vector transformation rule:
$$
\frac{\partial }{\partial x'^{\, i}} = \frac{\partial x^j}{\partial x'^{\, i}} \frac{\partial }{\partial x^j}
$$
Again, as we saw, these are inverse of each other. 
When a vector whose components transform like this, it is called a **contravariant vector**:
> [!Definition] Definition: Contravariant Vector
> A vector $\vec{v} \in T_{\vec{x}} M$ is called a **contravariant vector** if its components transform under coordinate transformation ${x^i} \to {x'^{\, i}}$ as:
> $$
> \begin{aligned}
> v'^{\, i} = \frac{\partial x'^{\, i}}{\partial x^j} v^{j}
> \end{aligned}
> $$

## Cotangent Space
Similarily to the linear algebra case, to properly define tensors, we also need the dual space of the tangent space, called the **cotangent space**.

If we take $V = T_{\vec{x}} M$, then its dual space $V^* = (T_{\vec{x}} M)^*$ is called the cotangent space at point $\vec{x}$, denoted by $T^*_{\vec{x}} M$:
> [!Definition] Definition: Cotangent Space
> Given a manifold $M$ and a point $p \in M$, the cotangent space at $p$, denoted by $T^*_p M$, is the dual vector space of the tangent space $T_p M$:
> $$
> T^*_p M := (T_p M)^* = \{ \tilde{\omega}: T_p M \to \mathbb{R} \mid \tilde{\omega} \text{ is a linear map} \}
> $$

Now, let us come back to a vector in the tangent space $\vec{v} \in T_{\vec{x}} M$.
Due to the isomorphism, any vector $\vec{v} \in T_{\vec{x}} M$ is equivalent to a directional derivative operator at point $\vec{x}$.

Given a smooth scalar function $f: M \mapsto \mathbb{R}$, let us denote a directional derivative at point $\vec{x} \in M$ with the direction $\vec{v}$ as $d f_{\vec{x}}(\vec{v})$:
$$
\begin{aligned}
d f_{\vec{x}}(\vec{v}) &:= \hat{\vec{v}} f = \vec{v} \cdot \nabla f(\vec{x}) \\
\end{aligned}
$$

Notice how on the RHS, $\vec{v} \cdot \nabla$ is a linear functional $\vec{v} \cdot \nabla: C^{\infty} \mapsto \mathbb{R}$.
But on the LHS, we can think of $d f_{\vec{x}}(\vec{v})$ as a map from the tangent space $T_{\vec{x}} M$ to $\mathbb{R}$: $df_{\vec{x}}: T_{\vec{x}} M \to \mathbb{R}$, taking a vector $\vec{v} \in T_{\vec{x}} M$ as input and producing a scalar as output.
This is exactly the definition of a covector in the dual space of $T_{\vec{x}} M$, which is the cotangent space $T^*_{\vec{x}} M$.

> [!Definition] Definition: Differential as a Covector
> Given a smooth scalar function $f: M \mapsto \mathbb{R}$, its differential at point $\vec{x} \in M$, denoted by $d f_{\vec{x}}$, is a covector in the cotangent space $T^*_{\vec{x}} M$ defined as:
> $$
> d f_{\vec{x}}: T_{\vec{x}} M \to \mathbb{R}, \quad d f_{\vec{x}}(\vec{v}) := \vec{v} \cdot \nabla f(\vec{x})
> $$

Now we ask, what is a good choice of basis for the cotangent space $T^*_{\vec{x}} M$?

So we just saw that the covectors can be written as directional derivatives as a function of $\vec{v} \in T_{\vec{x}} M$:
$$
d f_{\vec{x}}(\vec{v}) = \vec{v} \cdot \nabla f(\vec{x})
$$

If we take a function $f$ that takes out a single coordinate component, which we might denote by $x^i(\vec{x}) = x^i$ ($x^i: M \to \mathbb{R}$), then its differential at point $\vec{x}$ is:
$$
\begin{gathered}
d f_{\vec{x}} (\vec{v}) = \vec{v} \cdot \nabla x^i = v^j \frac{\partial x^i}{\partial x^j} = v^j \delta^i_j = v^i
\end{gathered}
$$

By the linearity of the directional derivative, 
$$
d f_{\vec{x}} (\vec{v}) = v^j d x^i (\partial_j) = v^j \delta^i_
$$

Which means that $d x^i$ satisfy the dual basis property:
$$
d x^i (\partial_j) = \delta^i_j
$$

## Tensor Field

Now that we have properly defined tangent space and cotangent space, we can finally define "tensor fields".
> [!Definition] Definition: (m, n) Tensor Field
> On $M = \mathbb{R}^n$, an $(m, n)$ tensor field $\mathcal{T}$ is a multilinear map defined at each point $\vec{x} \in M$:
> $$
> \mathcal{T}_{\vec{x}}: 
> \underbrace{
>     T^*_{\vec{x}} M \times T^*_{\vec{x}} M \times \cdots \times T^*_{\vec{x}} M}_{m \text{ times}} 
>     \times 
>     \underbrace{
>     T_{\vec{x}} M \times T_{\vec{x}} M \times \cdots \times T_{\vec{x}} M}_{n \text{ times}} \to \mathbb{R}
> $$
> Where $T_{\vec{x}} M$ and $T^*_{\vec{x}} M$ are the tangent space and cotangent space at point $\vec{x} \in M$, respectively.

With this knowledge, we can finally understand the transformation definition of tensors.

Assume, as before, that we have a (1, 1) tensor field $\mathcal{T}$ on $M = \mathbb{R}^n$.
At each point $\vec{x} \in M$, the tensor field $\mathcal{T}_{\vec{x}}$ takes a covector $\tilde{\omega} \in T^*_{\vec{x}} M$ and a vector $\vec{v} \in T_{\vec{x}} M$ as input and produces a scalar as output:
$$
\mathcal{T}_{\vec{x}} (\tilde{\omega}, \vec{v}) \in \mathbb{R}
$$

We have seen that basis for $T_{\vec{x}} M$ and $T^*_{\vec{x}} M$ transform as:
$$ 
\frac{\partial}{\partial x'^{\, i}} = \frac{\partial x^j}{\partial x'^{\, i}} \frac{\partial}{\partial x^j}, \quad d x'^{\, i} = \frac{\partial x'^{\, i}}{\partial x^j} d x^j
$$

Due to the multilinearity, the tensor components, which takes the basis vectors as input, must transform under the combined transformation:
$$
T^i_j := \mathcal{T}_{\vec{x}} (d x^i, \partial_j) \implies T'^{\, i}_{\, j} = \frac{\partial x'^{\, i}}{\partial x^k} \frac{\partial x^l}{\partial x'^{\, j}} T^k_l
$$
Such tensor that transforms like this under coordinate transformation is called a (1, 1) tensor, or mixed tensor (since it has both covariant and contravariant indices).

Similarly, a (0, 2) tensor takes two vectors as input and produces a scalar as output:
$$
\mathcal{S}_{\vec{x}} (\vec{v_1}, \vec{v_2}) \in \mathbb{R}
$$
Its components transform as:
$$
S_{ij} := \mathcal{S}_{\vec{x}} (\partial_i, \partial_j) \implies S'_{ij} = \frac{\partial x^k}{\partial x'^{\, i}} \frac{\partial x^l}{\partial x'^{\, j}} S_{kl}
$$
this is called a (0, 2) tensor, or 2nd rank covariant tensor, because its transformation has 2 covariant factors.

Similarly, a (2, 0) tensor takes two covectors as input and produces a scalar as output:
$$
\mathcal{R}_{\vec{x}} (\tilde{\omega_1}, \tilde{\omega_2}) \in \mathbb{R}
$$
Its components transform as:
$$
R^{ij} := \mathcal{R}_{\vec{x}} (d x^i, d x^j) \implies R'^{\, ij} = \frac{\partial x'^{\, i}}{\partial x^k} \frac{\partial x'^{\, j}}{\partial x^l} R^{kl}
$$
this is called a (2, 0) tensor, or 2nd rank contravariant tensor, because its transformation has 2 contravariant factors.
