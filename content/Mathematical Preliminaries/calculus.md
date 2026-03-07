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

Given that $x_0 \in \operatorname{int}(U)$, the linear transformation $L$ is unique if it exists, and we call it the **(total) derivative** of $f$ at $x_0$, and denote it as $f'(x_0)$, which can be represented as a matrix $Df(x_0)$(later discussed).

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
\frac{\partial f}{\partial x^i}(x_0) := D_{e_i} f(x_0) = f'(x_0)(e_i) = \lim_{t \to 0^+} \frac{f(x_0 + t e_i) - f(x_0)}{t} = \frac{d}{dt} f(x_0 + t e_i) \bigg|_{t=0} \in \mathbb{R}^m
$$
in which case, the limit is called the **partial derivative** of $f$ with respect to $x_i$ at $x_0$.

This is useful because now we can write directional derivatives as a linear combination of partial derivatives:
$$
\begin{aligned}
D_v f(x_0)
& = f'(x_0)(v) \\
& = f'(x_0) \left( \sum_i v_i e_i \right) \\
& = \sum_i v_i f'(x_0)(e_i) \\
& = \sum_i v_i \frac{\partial f}{\partial x^i}(x_0)
\end{aligned}
$$

(Note: this will be important for tangent spaces of manifolds)

For a scalar function $f: \mathbb{R}^n \overset{\text{open}}{\supset} U \to \mathbb{R}$, this can be simplified down to the so-called **advection term** in fluid mechanics:
$$
D_v f(x_0) = \sum_i v_i \frac{\partial f}{\partial x^i}(x_0) = (v \cdot \nabla) f(x_0)
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
> Since $g$ is differentiable at $f(x_0)$, we have
> $$
> \lim_{y \to f(x_0); y \in V\setminus \{f(x_0)\}} \frac{|| g(y) - [g(f(x_0)) + g'(f(x_0))(y - f(x_0))] ||}{||y - f(x_0)||} = 0
> $$
> Take $y = f(x_0 + tv)$, where $x = x_0 + tv \in U$ for sufficiently small $t$, we have
> $$
> \begin{aligned}
> \lim_{f(x_0 + tv) \to f(x_0); f(x_0 + tv) \in V\setminus \{f(x_0)\}} \frac{|| g(f(x_0 + tv)) - [g(f(x_0)) + g'(f(x_0))(f(x_0 + tv) - f(x_0))] ||}{||f(x_0 + tv) - f(x_0)||} &= 0 \\
> \implies \lim_{f(x_0 + tv) \to f(x_0); f(x_0 + tv) \in V\setminus \{f(x_0)\}}
> \frac{|| g(f(x_0 + tv)) - [g(f(x_0)) + g'(f(x_0))(f(x_0 + tv) - f(x_0))] ||}{|t|} \\
> \times \frac{|t|}{||f(x_0 + tv) - f(x_0)||} &= 0 \\
> \end{aligned}
> $$
> Since $f$ is differentiable at $x_0$, 
> $$
> \lim_{t \to 0, t \neq 0} \frac{f(x_0 + tv) - f(x_0)}{t} = f'(x_0)(v)
> $$
> thus, 
> $$
> \begin{aligned}
> \lim_{t \to 0, t \neq 0} \left\Vert \frac{g(f(x_0 + tv)) - g(f(x_0)) - g'(f(x_0))(f(x_0 + tv) - f(x_0))}{t} \right\Vert \\
> \times\frac{1}{|| Df(x_0)(v) ||} &= 0
> \end{aligned}
> $$


### Leibniz/ Product Rule
