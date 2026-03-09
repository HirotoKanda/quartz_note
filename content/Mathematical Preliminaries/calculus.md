---
title: "Notes on Calculus"
date: "2026-02-16"
tags: ["Mathematics", "Topology", "Calculus", "Analysis"]
---

# Derivatives

## Differentiability and Derivatives

### Total Derivative

Consider a function $f: \mathbb{R}^n \overset{\text{open}}{\supset} U \to \mathbb{R}^m$.
Take a point $x_0 \in \operatorname{int}(U)$, and a linear transformation $L: \mathbb{R}^n \to \mathbb{R}^m$.

Then, we say that $f$ is **differentiable** at $x_0$ with derivative $L$, if:
$$
\lim_{x \to x_0; x \in U\setminus \{x_0 \}} \frac{|| f(x) - [f(x_0) + L(x - x_0)] ||}{||x - x_0||} = 0
$$

(Note: this is a special case of **Fréchet differentiability** for functions between Banach spaces)

In a sense, this means that $L$ is the best linear approximation of $f(x)$ near $x_0$.
Let us define the error term $\varepsilon_f(h)$:
$$
\varepsilon_f(h) := f(x_0 + h) - [f(x_0) + L(h)]
$$
where we can think of $h = x - x_0$.
Then, the definition of differentiability can be rewritten as
$$
\lim_{h \to 0} \frac{|| \varepsilon_f(h) ||}{||h||} = 0
$$
which gives
$$
f(x_0 + h) = f(x_0) + L(h) + \varepsilon_f(h).
$$

Now, given that $x_0 \in \operatorname{int}(U)$, the linear transformation $L$ is unique if it exists, and we call it the **(total) derivative** of $f$ at $x_0$, and denote it as $f'(x_0)$, which can be represented as a matrix $Df(x_0)$(later discussed).

> [!Proof:]
> Assume that $L_1, L_2: \mathbb{R}^n \to \mathbb{R}^m$ are two derivatives of $f$ at $x_0$.
> Then, we have a vector $v \in \mathbb{R}^n$ such that $L_1 v \neq L_2 v$.
> This means that
> $$
> (L_1 - L_2) v \neq 0 \implies || t (L_1 - L_2) v || > 0
> $$
> for any $t \neq 0$.
> Now, we let $x = x_0 + tv \in U$,
> $$
> t(L_1 - L_2) v = [f(x_0 + tv) - f(x_0) - L_2(tv)] - [f(x_0 + tv) - f(x_0) - L_1(tv)]
> $$
> taking the norm and dividing by $||tv||$, we have
> $$
> \frac{|| t(L_1 - L_2) v ||}{||tv||} = \frac{|| f(x) - [f(x_0) + L_2(x - x_0)] ||}{||x - x_0||} - \frac{|| f(x) - [f(x_0) + L_1(x - x_0)] ||}{||x - x_0||}
> $$
> since both numerator and denominator is an Euclidean norm, they are both positive, and we have
> $$
> 0 < \frac{|| t(L_1 - L_2) v ||}{||tv||} \leq \frac{|| f(x) - [f(x_0) + L_2(x - x_0)] ||}{||x - x_0||} + \frac{|| f(x) - [f(x_0) + L_1(x - x_0)] ||}{||x - x_0||}
> $$
> Taking the limit as $t \to 0 \iff x \to x_0$, because $L_1$ and $L_2$ are both derivatives of $f$ at $x_0$, we have
> $$
> 0 < \lim_{x \to x_0; x \in U\setminus \{x_0 \}} \frac{|| t(L_1 - L_2) v ||}{||tv||} \leq 0
> $$
> which is a contradiction. Therefore, the derivative of $f$ at $x_0$ is unique if it exists.

### Directional Derivative

On the other hand, we have a different notion of derivative, called **directional derivative**.
Given a function $f: \mathbb{R}^n \overset{\text{open}}{\supset} U \to \mathbb{R}^m$, a point $x_0 \in \operatorname{int}(U)$, and a vector $v \in \mathbb{R}^n$,
we say that $f$ is **differentiable in the direction of $v$** at $x_0$ if the following limit exists:
$$
D_v f(x_0) := \lim_{t \to 0^+} \frac{f(x_0 + tv) - f(x_0)}{t} = \frac{d}{dt} f(x_0 + tv) \bigg|_{t=0}
$$
where $x_0 + tv$ is in $U$ for sufficiently small $t$.

Directional derivative can be written using the total derivative:
$$
D_v f(x_0) = f'(x_0) v
$$

> [!Proof]
> Assume that $f: \mathbb{R}^n \overset{\text{open}}{\supset} U \to \mathbb{R}^m$ is differentiable at $x_0$ with derivative $f'(x_0)$, and take a vector $v \in \mathbb{R}^n$.
> Since $f$ is differentiable at $x_0$, we have
> $$
> \lim_{x \to x_0; x \in U\setminus \{x_0 \}} \frac{|| f(x) - [f(x_0) + f'(x_0)(x - x_0)] ||}{||x - x_0||} = 0
> $$
> Let $x = x_0 + tv$, we have
> $$
> \lim_{t \to 0, t \neq 0} \frac{|| f(x_0 + tv) - [f(x_0) + f'(x_0)(tv)] ||}{||tv||} = 0
> $$
> Since $v$ is a fixed vector, $||v||$ is a constant which can be factored out:
> $$
> \lim_{t \to 0, t \neq 0} \frac{|| f(x_0 + tv) - f(x_0) - f'(x_0)(tv) ||}{|t|} = \lim_{t \to 0, t \neq 0} \left\Vert \frac{f(x_0 + tv) - f(x_0) - t f'(x_0)(v)}{t} \right\Vert = 0
> $$
> The inside of the norm is a vector in $\mathbb{R}^m$, and the limit of its norm is $0$, which means that the vector is a zero vector in the limit:
> $$
> \lim_{t \to 0, t \neq 0} \frac{f(x_0 + tv) - f(x_0) - t f'(x_0)(v)}{t} = \mathbf{0}
> $$
> by term wise limit,
> $$
> \lim_{t \to 0, t \neq 0} \frac{f(x_0 + tv) - f(x_0)}{t} = \lim_{t \to 0, t \neq 0} f'(x_0)(v)
> $$
> Since the limit $t \to 0$ exists, the right limit $t \to 0^+$ are equal to the limit:
> $$
> \lim_{t \to 0^+} \frac{f(x_0 + tv) - f(x_0)}{t} = \lim_{t \to 0^+} f'(x_0)(v) = f'(x_0)(v)
> $$
> and the LHS is exactly the definition of the directional derivative $D_v f(x_0)$, we have
> $$
> D_v f(x_0) = f'(x_0)(v)
> $$
> Thus, differentiability is sufficient for the existence of directional derivative. (note that the converse is not true)

### Partial Derivative

A special case of directional derivative is the **partial derivative**.
Remember that the directional derivative can be written as follows:
$$
D_v f(x_0) = \lim_{t \to 0^+} \frac{f(x_0 + tv) - f(x_0)}{t} = \frac{d}{dt} f(x_0 + tv) \bigg|_{t=0}
$$
If we take $v = e_i$, a standard Euclidean basis vector, the direction is along the $i$-th coordinate axis.
So, given a function $f: \mathbb{R}^n \overset{\text{open}}{\supset} U \to \mathbb{R}^m$, a point $x_0 \in \operatorname{int}(U)$, and a standard Euclidean basis vector $e_i$, we say that $f$ is **differentiable in the direction of $e_i$** at $x_0$ if the following limit exists:
$$
\frac{\partial f}{\partial x_i}(x_0) := D_{e_i} f(x_0) = f'(x_0)(e_i) = \lim_{t \to 0^+} \frac{f(x_0 + t e_i) - f(x_0)}{t} = \frac{d}{dt} f(x_0 + t e_i) \bigg|_{t=0} \in \mathbb{R}^m
$$
in which case, the limit is called the **partial derivative** of $f$ with respect to $x_i$ at $x_0$.

This is useful because now we can write directional derivatives as a linear combination of partial derivatives:
$$
\begin{aligned}
D_v f(x_0)
& = f'(x_0)(v) \\
& = f'(x_0) \left( \sum_i v_i e_i \right) \\
& = \sum_i v_i f'(x_0)(e_i) \\
& = \sum_i v_i \frac{\partial f}{\partial x_i}(x_0)
\end{aligned}
$$

(Note: this will be important for tangent spaces of manifolds)

For a scalar function $f: \mathbb{R}^n \overset{\text{open}}{\supset} U \to \mathbb{R}$, the Jacobian matrix is a $1 \times n$ matrix, which can be identified with a row vector, called the **gradient** of $f$ at $x_0$, sometimes denoted as $\nabla f(x_0)$:
$$
D f(x) = \nabla f(x_0) := \pmatrix{\frac{\partial f}{\partial x^1}(x) & \frac{\partial f}{\partial x^2}(x) & \cdots & \frac{\partial f}{\partial x^n}(x)}
$$
which makes the directional derivative $D_v f(x_0)$ a matrix multiplication of the gradient and the vector $v$:
$$
D_v f(x_0) = \nabla f(x_0) v = \sum_i v_i \frac{\partial f}{\partial x_i}(x_0)
$$

If $f$ is vector-valued, i.e. $f: \mathbb{R}^n \overset{\text{open}}{\supset} U \to \mathbb{R}^m$, the total derivative can be represented by **Jacobian matrix** or **derivative matrix** $Df(x_0)$, which is a $m \times n$ matrix:
$$
\begin{aligned}
Df(x_0)
& = \left( \frac{\partial f_i}{\partial x_j}(x_0) \right)^{1 \leq i \leq m}_{1 \leq j \leq n} \\
& = \pmatrix{
\frac{\partial f_1}{\partial x^1}(x_0) & \frac{\partial f_1}{\partial x^2}(x_0) & \cdots & \frac{\partial f_1}{\partial x^n}(x_0) \\
\frac{\partial f_2}{\partial x^1}(x_0) & \frac{\partial f_2}{\partial x^2}(x_0) & \cdots & \frac{\partial f_2}{\partial x^n}(x_0) \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial f_m}{\partial x^1}(x_0) & \frac{\partial f_m}{\partial x^2}(x_0) & \cdots & \frac{\partial f_m}{\partial x^n}(x_0)
}
\end{aligned}
$$
Let us check that it in fact satisfies $Df(x_0)(v) = D_v f(x_0)$, given $v = (v_1, v_2, \cdots, v_n)^T$:
$$
\begin{aligned}
Df(x_0)(v)
& = \pmatrix{
\frac{\partial f_1}{\partial x^1}(x_0) & \frac{\partial f_1}{\partial x^2}(x_0) & \cdots & \frac{\partial f_1}{\partial x^n}(x_0) \\
\frac{\partial f_2}{\partial x^1}(x_0) & \frac{\partial f_2}{\partial x^2}(x_0) & \cdots & \frac{\partial f_2}{\partial x^n}(x_0) \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial f_m}{\partial x^1}(x_0) & \frac{\partial f_m}{\partial x^2}(x_0) & \cdots & \frac{\partial f_m}{\partial x^n}(x_0)
} \pmatrix{
v_1 \\
v_2 \\
\vdots \\
v_n
} \\
& = \left(\sum_j v_j \frac{\partial f_i}{\partial x^j}(x_0) \right)_{1 \leq i \leq m} \\
& = \sum_j v_j \frac{\partial f}{\partial x^j}(x_0)
\end{aligned}
$$

###

## Properties of Derivatives

### Chain Rule

Consider functions $f: \mathbb{R}^n \overset{\text{open}}{\supset} U \to V \overset{\text{open}}{\subset} \mathbb{R}^m$ and $g:V \to \mathbb{R}^l$, and a point $x_0 \in \operatorname{int}(U)$.
Assume that $f$ is differentiable at $x_0$, and $f(x_0) \in \operatorname{int}(V)$, at which $g$ is differentiable.
Then, the composition $g \circ f: U \to \mathbb{R}^l$ is differentiable at $x_0$, and its derivative is given by the composition of the derivatives:
$$
(g \circ f)'(x_0) = g'(f(x_0)) f'(x_0)
$$
This is called the **chain rule**.

Note that this follows the same idea as the chain rule for single variable functions.

> [!Proof]
> Since $g$ is differentiable at $f(x_0)$,
> $$
> g(y_0 + h) = g(y_0) + g'(y_0)(h) + \varepsilon_g (h)
> $$
> where $y_0 = f(x_0)$ and $\varepsilon_g(h)$ is a function such that $\lim_{h \to 0} \frac{||\varepsilon_g(h)||}{||h||} = 0$.
> Now, since $f$ is differentiable at $x_0$, we have
> $$
> f(x_0 + k) = f(x_0) + f'(x_0)(k) + \varepsilon_f(k)
> $$
> where $\varepsilon_f(k)$ is a function such that $\lim_{k \to 0} \frac{||\varepsilon_f(k)||}{||k||} = 0$.
> Take $h$ such that $h = f(x_0 + k) - f(x_0)$, we have
> $$
> h = f'(x_0)(k) + \varepsilon_f(k)
> $$
> Thus,
> $$
> \begin{aligned}
> g(f(x_0 + k))
> &= g(f(x_0)) + g'(f(x_0))[f'(x_0)(k) + \varepsilon_f(k)] + \varepsilon_g[f'(x_0)(k) + \varepsilon_f(k)] \\
> &= g(f(x_0)) + g'(f(x_0)) f'(x_0)(k) + g'(f(x_0)) \varepsilon_f(k) + \varepsilon_g[f'(x_0)(k) + \varepsilon_f(k)]
> \end{aligned}
> $$
> Thus to show that the total derivative of $g \circ f$ at $x_0$ is $g'(f(x_0)) f'(x_0)$, we need to show that
> $$
> \lim_{k \to 0} \frac{|| g'(f(x_0)) \varepsilon_f(k)  + \varepsilon_g(f'(x_0)(k) + \varepsilon_f(k))||}{||k||} = 0.
> $$
> The norm on the numerator can be bounded by the triangle inequality:
> $$
> \begin{aligned}
> || g'(f(x_0)) \varepsilon_f(k)  + \varepsilon_g(f'(x_0)(k) + \varepsilon_f(k))||
> &\leq || g'(f(x_0)) \varepsilon_f(k) || + ||\varepsilon_g(f'(x_0)(k) + \varepsilon_f(k))|| \\
> &\leq M \cdot || \varepsilon_f(k) || + ||\varepsilon_g(f'(x_0)(k) + \varepsilon_f(k))||
> \end{aligned}
> $$
> For the second term,
> $$
> \begin{aligned}
> ||\varepsilon_g(f'(x_0)(k) + \varepsilon_f(k))||
> &= \frac{||\varepsilon_g(f'(x_0)(k) + \varepsilon_f(k))|| }{|| f'(x_0)(k) + \varepsilon_f(k) ||} || f'(x_0)(k) + \varepsilon_f(k) || \\
> & \leq \frac{||\varepsilon_g(f'(x_0)(k) + \varepsilon_f(k))|| }{|| f'(x_0)(k) + \varepsilon_f(k) ||} (||f'(x_0)(k)|| + ||\varepsilon_f(k)||)
> \end{aligned}
> $$
> Notice that the coefficient is of the form
> $$
> \frac{||\varepsilon_g(h)|| }{|| h ||}
> $$
> which goes to $0$ as $h \to 0$, as well as $f'(x_0)(k) + \varepsilon_f(k) \to 0$ as $k \to 0$.
> Substituting back to the limit,
> $$
> \begin{aligned}
> \lim_{k \to 0} \frac{|| g'(f(x_0)) \varepsilon_f(k)  + \varepsilon_g(f'(x_0)(k) + \varepsilon_f(k))||}{||k||}
> & \leq \lim_{k \to 0} M \cdot \frac{||\varepsilon_f(k) ||}{|| k ||} \\
> & \quad + \lim_{k \to 0} \frac{||\varepsilon_g(f'(x_0)(k) + \varepsilon_f(k))|| }{|| f'(x_0)(k) + \varepsilon_f(k) ||}
> \frac{||f'(x_0)(k)|| + ||\varepsilon_f(k)||}{||k||}
> \end{aligned}
> $$
> All the $|| \varepsilon_f(k) || / || k||$ term goes to $0$ by the definition of $\varepsilon_f(k)$, so the whole limit goes to 0, and $f'(x_0)(k)$ term goes to $0$ because of the $\varepsilon_g$ coefficient, thus we have
> $$
> (g \circ f) (x_0 + k) = (g \circ f) (x_0) + g'(f(x_0)) f'(x_0)(k) + \varepsilon_{g \circ f} (k)
> $$
> which shows the chain rule.

### Leibniz/ Product Rule

Now, there is an interesting corollary of the chain rule.

Take two functions $f, g: \mathbb{R}^n \overset{\text{open}}{\supset} U \to \mathbb{R}$, and combine them to make a vector-valued function $F: U \to \mathbb{R}^2$ defined as $F(x) = (f(x), g(x))^T$.
The Jacobian matrix of $F$ is a $2 \times 2$ matrix
$$
DF(x) = \pmatrix{\frac{\partial f}{\partial x^1}(x) & \frac{\partial f}{\partial x^2}(x) & \cdots & \frac{\partial f}{\partial x^n}(x) \\
\frac{\partial g}{\partial x^1}(x) & \frac{\partial g}{\partial x^2}(x) & \cdots & \frac{\partial g}{\partial x^n}(x)} = \pmatrix{Df(x) \\ Dg(x)}
$$

Consider a multiplication map $\mu: \mathbb{R}^2 \to \mathbb{R}$ defined as $\mu(x, y)^T = xy$.
More explicitly, we call this the **pointwise product** of $f$ and $g$:
$$
(f \cdot g)(x) = \mu\pmatrix{f(x) \\ g(x)} = f(x) \cdot g(x)
$$

Here, we notice that $\mu$ is differentiable at any point $(x, y)^T \in \mathbb{R}^2$, and its derivative is a $1 \times 2$ matrix (a row vector):
$$
D \mu \pmatrix{x \\ y} = (y, x)
$$

Thus by chain rule,
$$
\begin{aligned}
D(f \cdot g)(x)
& = D (\mu \circ F )(x) \\
& = D \mu \pmatrix{f(x) \\ g(x)} DF(x) \\
& = (g(x), f(x)) \pmatrix{Df(x) \\ Dg(x)} \\
& = g(x) Df(x) + f(x) Dg(x)
\end{aligned}
$$  
This is called the **Leibniz rule** or **product rule** of derivatives.

## $C^r$-class Functions and Higher Order Derivatives

### $C^r$-class Functions

Now, coming back to the total derivative of a vector-valued function $f: \mathbb{R}^n \overset{\text{open}}{\supset} U \to \mathbb{R}^m$, we have the total derivative $f'(x)$ at each interior point $x \in \operatorname{int}(U)$, which is a linear transformation from $\mathbb{R}^n$ to $\mathbb{R}^m$:
$$
f'(x): \mathbb{R}^n \to \mathbb{R}^m \iff Df(x): \mathbb{R}^n \to \mathbb{R}^m
$$
Notice that the domain of $f'(x)$ and $Df(x)$ is not technically the original $\mathbb{R}^n$, but the tangent space of $\mathbb{R}^n$.
To articulate, remember that $f(x + h)$ can be written as
$$
f(x + h) = f(x) + f'(x)(h) + \varepsilon_f(h)
$$
$h$ is a vector, that does not live in the original $U \in \mathbb{R}^n$ where $x$ lives, but it is rather difference between two nearby points that are in the original $\mathbb{R}^n$, that happens to be a vector in $\mathbb{R}^n$.
We should express this distinction by writing $h \in T_x U$, where $T_x U$ is **the tangent space** of $U$ at $x$ (explained in manifold section later).

Also, in a similar way, while $f'(x) (h)$ looks like a vector in the original range $\mathbb{R}^m$, but in essence is a difference between $f(x)$ and $f(x + h)$, which should also live in the tangent space of $\mathbb{R}^m$ at $f(x)$, denoted as $T_{f(x)} \mathbb{R}^m$:
$$
f'(x): T_x U \to T_{f(x)} \mathbb{R}^m.
$$

As for reasons I explain later in [manifold section](manifold.md), the tangent space of (subsets of) Euclidean space $\mathbb{R}^n$ is **canonically isomorphic** to the original $\mathbb{R}^n$, so we regard $T_x U$ and $T_{f(x)} \mathbb{R}^m$ as $\mathbb{R}^n$ and $\mathbb{R}^m$ respectively, and write
$$
f'(x): \mathbb{R}^n \to \mathbb{R}^m.
$$

This is a linear transformation between two vector spaces, but also it gives another map $f'$, that takes a point $x \in U \subset \mathbb{R}^n$ and produces a linear transformation $f'(x) \in L(\mathbb{R}^n,\mathbb{R}^m)$, where
$$
L(V, W) := \{ A: V \to W | A \text{ is a linear transformation} \}
$$
is the set of all linear transformations from $V$ to $W$.
In short, we now have a (crudely speaking) matrix-valued map $f'$:
$$
f': U \to L(\mathbb{R}^n, \mathbb{R}^m), \quad x \mapsto f'(x).
$$

Now, we define a class of functions, called **$C^r$-class functions**.
Given a function $f: \mathbb{R}^n \overset{\text{open}}{\supset} U \to \mathbb{R}^m$:

- **$C^0$-class function**
  - if it is continuous at every point in $U$.

- **$C^r$-class function** ($r \geq 1$)
  - if the derivative $f': U \to L(\mathbb{R}^n, \mathbb{R}^m)$ is a $C^{r-1}$-class function.

While we have the definition, it would not be as useful without the ability to actually compute actual functions to show that they are $C^r$-class functions.

### Higher Order Derivatives

Now, speaking of canonical isomorphism, there is actually a canonical isomorphism between $L(\mathbb{R}^n, \mathbb{R}^m)$ and $\mathbb{R}^{m \times n}$ ([refer here](vector.md)).
Thus we can identify $f'$ as a map from $U$ to $\mathbb{R}^{m \times n}$, and consider its derivative $(f')'$, which is a map from $U$ to $L(\mathbb{R}^n, \mathbb{R}^{m \times n})$.
Since $L(\mathbb{R}^n, \mathbb{R}^{m \times n})$ is canonically isomorphic to $\mathbb{R}^{(m \times n) \times n}$, we can identify $f'$ as a map:
$$
f': U \to \mathbb{R}^{m \times n}
$$
Since this is an ordinary vector valued map, we can take its derivative again (assuming $f'$ is differentiable) to get $(f')'$:
$$
(f')'(x): T_x U \to T_{f'(x)} \mathbb{R}^{m \times n}
$$
and in a similar manner, we identify the domain and range as
$$
(f')'(x): \mathbb{R}^n \to \mathbb{R}^{m \times n}
$$
