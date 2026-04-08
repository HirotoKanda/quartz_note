---
title: "Boltzmann Equation"
date: "2026-03-22"
tags: ["Physics", "Statistical Mechanics"]
---

## Properties of Dirac Delta Function

The Dirac delta function $\delta^n(\mathbf{x})$ in $n$-dimensional space is defined as a distribution that satisfies the following property:
$$
\int_{V} \phi(\mathbf{x}) \delta^n(\mathbf{x} - \mathbf{a}) d\mathbf{x} = \phi(\mathbf{a}) \in \mathbb{R}
$$
where $\phi(\mathbf{x})$ is a **test function** that is integrable and continuous at $\mathbf{a}$, and $V$ is any region such that $\mathbf{a} \in \mathrm{int}(V)$, i.e., $\mathbf{a}$ is an interior point of $V$.
If $a \notin V$, then the integral is to be zero.

We can define the derivative of the delta function using integration by parts:
$$
\begin{aligned}
\int_{V} \phi(\mathbf{x}) \nabla \delta^n(\mathbf{x} - \mathbf{a}) d\mathbf{x}
&= \phi(\mathbf{x}) \delta^n(\mathbf{x} - \mathbf{a}) \bigg|_{\partial V} - \int_{V} \nabla \phi(\mathbf{x}) \delta^n(\mathbf{x} - \mathbf{a}) d\mathbf{x} \\
&= - \int_{V} \nabla \phi(\mathbf{x}) \delta^n(\mathbf{x} - \mathbf{a}) d\mathbf{x} \\
& = -\nabla \phi(\mathbf{a})
\end{aligned}
$$

Now, we assume that $\mathbf{a}$ is a trajectory of a particle, i.e., $\mathbf{a} = \mathbf{a}(t)$, then we can write:
$$
\begin{aligned}
\frac{d}{dt} \int_{V} \phi(\mathbf{x}) \delta^n(\mathbf{x} - \mathbf{a}(t)) d\mathbf{x} 
&= \int_{V} \phi(\mathbf{x}) \frac{\partial}{\partial t} \delta^n(\mathbf{x} - \mathbf{a}(t)) d\mathbf{x} \\
&= \int_{V} \phi(\mathbf{x}) \nabla \delta^n(\mathbf{x} - \mathbf{a}(t)) \cdot \frac{d\mathbf{a}(t)}{dt} d\mathbf{x} \\
&= \frac{d\mathbf{a}(t)}{dt} \cdot \nabla \phi(\mathbf{a}(t)) 
\end{aligned}
$$


## Setup

Consider a closed system of $N$ particles in a region $\Omega \subset \mathbb{R}^3$.
Each particle has a position $\mathbf{q}_i$ and a momentum $\mathbf{p}_i$, where $i = 1, 2, \cdots, N$.

Furthermore, assume that the particles are identical and indistinguishable, and they follow the canonical equation of motion:
$$
\begin{cases}
\dot{\mathbf{q}}_i
= \dfrac{\partial H(\{\mathbf{q}_j, \mathbf{p}_j\}, t)}{\partial \mathbf{p}_i} \\
\dot{\mathbf{p}}_i
= -\dfrac{\partial H(\{\mathbf{q}_j, \mathbf{p}_j\}, t)}{\partial \mathbf{q}_i}
\end{cases}
$$

Now, we can define the **phase space** of the system as the $6N$-dimensional space $\Gamma = \Omega^N \times \mathbb{R}^{3N}$, where each point $z \in \Gamma$ represents a state of the system, i.e., a specific configuration of positions and momenta of all particles:
$$
z =
\begin{pmatrix}
\mathbf{q}_1 \\
\vdots \\
\mathbf{q}_N \\
\mathbf{p}_1 \\
\vdots \\
\mathbf{p}_N
\end{pmatrix}
$$

We can write the canonical equation of motion as:
$$
\dot{\gamma}(t)
=
\frac{d}{dt} \begin{pmatrix} \mathbf{q}_1(t) \\ \vdots \\ \mathbf{q}_N(t) \\ \mathbf{p}_1(t) \\ \vdots \\ \mathbf{p}_N(t) \end{pmatrix}
=
\begin{pmatrix}
\dfrac{\partial H(\{\mathbf{q}_j, \mathbf{p}_j\}, t)}{\partial \mathbf{p}_1} \\
\vdots \\
\dfrac{\partial H(\{\mathbf{q}_j, \mathbf{p}_j\}, t)}{\partial \mathbf{p}_N} \\
-\dfrac{\partial H(\{\mathbf{q}_j, \mathbf{p}_j\}, t)}{\partial \mathbf{q}_1} \\
\vdots \\
-\dfrac{\partial H(\{\mathbf{q}_j, \mathbf{p}_j\}, t)}{\partial \mathbf{q}_N}
\end{pmatrix}
$$

## Klimontovich Equation

Now, if we know the initial state of the system $\gamma(0) = (\mathbf{q}_i(0), \mathbf{p}_i(0))$ exactly, then we can determine the state of the system at any time $t$ by solving the equation of motion.
Then, the "density" of the system in the $\Gamma$-space can be represented by Dirac delta functions:
$$
\mathcal{D} (z, t) = \delta^{6N} (z - \gamma(t)) = \prod_{i=1}^N \delta^3(\mathbf{q}_i - \mathbf{q}_i(t)) \delta^3(\mathbf{p}_i - \mathbf{p}_i(t))
$$

This function $\mathcal{D}(z, t)$ is a "density" of the system. For any region $R \subset \Gamma$, we can define the number of states of the system in $R$ at time $t$ as:
$$
\mathcal{N}[\mathcal{D}, R, t] = \int_R \mathcal{D}(z, t) dz
$$
which, for this case gives $1$ if $\gamma(t) \in R$, and $0$ otherwise.

Tracking the time evolution of $\mathcal{D}(z, t)$ is equivalent to tracking the time evolution of the representative point $\gamma(t)$ of the system, so from here, we focus on $\mathcal{D}(z, t)$ with fixed $R$:
$$
\begin{aligned}
\frac{\delta}{\delta t} \mathcal{N}[\mathcal{D}, R, t] = \frac{d}{dt} \int_R \mathcal{D}(z, t) dz
&= \int_R \frac{\partial}{\partial t} \mathcal{D(z, t)} dz \\
&= \int_R \frac{\partial}{\partial t} \delta^{6N} (z - \gamma(t)) dz \\
&= \int_R - \nabla \delta^{6N} (z - \gamma(t)) \cdot \dot{\gamma}(t) dz \\
&= \int_R - \dot{\gamma}(t) \cdot \nabla \mathcal{D}(z, t) dz 
\end{aligned}
$$
Since we can take $R$ to be any region in $\Gamma$, we can write the above equation as:
$$
\frac{\partial}{\partial t} \mathcal{D}(z, t) = - \dot{\gamma}(t) \cdot \nabla \mathcal{D}(z, t)
$$

More explicitly, 
$$
\frac{\partial \mathcal{D}(\{\mathbf{q}_j, \mathbf{p}_j\}, t)}{\partial t}
+ \frac{d \mathbf{q}_j(t)}{d t} \cdot \frac{\partial \mathcal{D}(\{\mathbf{q}_j, \mathbf{p}_j\}, t)}{\partial \mathbf{q}_i}
+ \frac{d \mathbf{p}_i(t)}{d t} \cdot \frac{\partial \mathcal{D}(\{\mathbf{q}_j, \mathbf{p}_j\}, t)}{\partial \mathbf{p}_i} = 0
$$

This is called the **Klimontovich equation**. It describes the time evolution of the "density" $\mathcal{D}(z, t)$ in the phase space $\Gamma$ for a system of $N$ particles.

## Boltzmann Equation

Now, 