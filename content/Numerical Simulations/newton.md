---
title: "Newton-Raphson Method"
date: "2026-04-09"
tags: ["Mathematics", "Numerical Simulation"]
---

## Newton-Raphson Method

Take a vector-valued function $f: \mathbb{R}^n \to \mathbb{R}^n$, and assume that we want to find a root of $f$, that is, we look for $x^* \in \mathbb{R}^n$ such that 
$$
f(x^*) = \mathbf{0}.
$$

The **Newton-Raphson method** is an iterative method to find the root of $f$.
We start from an initial guess $x_0$, and we iteratively update the guess by using the following formula:
$$
x_{k+1} = x_k - Df(x_k)^{-1} f(x_k)
$$
where $Df(x_k)$ is the derivative matrix of $f$ at $x_k$, and $Df(x_k)^{-1}$ is the inverse of the derivative matrix.

If we set $h = x_{k+1} - x_k$, then we can rewrite the update formula as:
$$
Df(x_k) h = -f(x_k)
$$
which can be solved for $h$, and then we can update $x_{k+1} = x_k + h$.

## Convergence 

There are a few conditions for which the Newton-Raphson method converges to the root $x^*$.

1. The derivative has an inverse at the root, i.e., $Df(x^*)$ is invertible.
2. The initial guess $x_0$ is sufficiently close to the root $x^*$.
3. The function $f$ is sufficiently smooth close to the root $x^*$.

At each $k$-th iteration, the error from the real solution is given by:
$$
\varepsilon_k = x_k - x^*
$$
Around the root $x^*$,
$$
f(x_k) = f(x^*) +  Df(x^*) \varepsilon_k + O(\|\varepsilon_k\|^2) = Df(x^*) \varepsilon_k + O(\|\varepsilon_k\|^2)
$$
and 
$$
Df(x_k) = Df(x^*) + O(\|\varepsilon_k\|)
$$
which gives
$$
\begin{aligned}
    \varepsilon_{k+1} 
    &= \varepsilon_k - Df(x_k)^{-1} f(x_k) \\
    &= \varepsilon_k - Df(x_k)^{-1} (Df(x^*) \varepsilon_k + O(\|\varepsilon_k\|^2)) \\
    &= \varepsilon_k - \varepsilon_k + O(\|\varepsilon_k\|^2) \\
    &= O(\|\varepsilon_k\|^2)
\end{aligned}
$$