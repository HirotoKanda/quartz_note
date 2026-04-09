---
title: "Boltzmann Equation"
date: "2026-03-22"
tags: ["Physics", "Statistical Mechanics"]
---

<!-- ## Properties of Dirac Delta Function

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
&= - \int_{V} \phi(\mathbf{x}) \frac{\partial}{\partial t} \delta^n(\mathbf{x} - \mathbf{a}(t)) d\mathbf{x} \\
&= \int_{V} \phi(\mathbf{x}) \nabla \delta^n(\mathbf{x} - \mathbf{a}(t)) \cdot \frac{d\mathbf{a}(t)}{dt} d\mathbf{x} \\
&= \frac{d\mathbf{a}(t)}{dt} \cdot \nabla \phi(\mathbf{a}(t))
\end{aligned}
$$ -->

## Setup

### Phase Space: $\Gamma$-Space and $\mu$-Space

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

Now, we define the **phase space**, (to be more precise, the $\mu$-space) as the $ 6$-dimensional space of position and momentum, i.e., $ \mu := \Omega \times \mathbb{R}^3$.

The state of the system at time $t$ is represented as a set of $N$ points in $\mu$-space, i.e., $\{(\mathbf{q}_i(t), \mathbf{p}_i(t))\}_{i=1}^N$.

Instead of tracking $N$ individual particles (of which there could be more than $10^{30}$), which should track a single function that has all the information of the system.

We can also use the $\Gamma$-space, which is the $6N$-dimensional space of all the positions and momenta of the $N$ particles, i.e., $\gamma = (\mathbf{q}_1, \mathbf{q}_2, \ldots, \mathbf{q}_N, \mathbf{p}_1, \mathbf{p}_2, \cdots, \mathbf{p}_N)$.
In $\Gamma$-space, the state of the system at time $t$ is represented as a single point $\gamma(t) = (\mathbf{q}_1(t), \mathbf{p}_1(t), \ldots, \mathbf{q}_N(t), \mathbf{p}_N(t)) \in \mu^N$.
For simplicity, we may denote $\Gamma = \mu^N$, as $\Gamma$-space.

### Klimontovich Distribution Function

In the hypothetical case that we know the exact position and momentum of each particle at each time $t$, we can define the **Klimontovich distribution function** as:
$$
\mathcal{D}(\{\mathbf{q}_i , \mathbf{p}_i \};\{\mathbf{q}_i(t), \mathbf{p}_i(t)\}) = \sum_{i = 1}^N \delta^3(\mathbf{q} - \mathbf{q}_i(t)) \delta^3(\mathbf{p} - \mathbf{p}_i(t))
$$
The integral of $\mathcal{D}$ over a region $V$ in $\mu$-space gives the number of particles in that region at time $t$:
$$
\mathcal{N}(V, t) = \int_{V} \mathcal{D}(\{\mathbf{q}_i , \mathbf{p}_i \};\{\mathbf{q}_i(t), \mathbf{p}_i(t)\}) d\mathbf{q} d\mathbf{p}
$$
<!-- Since $(\mathbf{q}_i(t), \mathbf{p}_i(t))$ moves in the $\mu$-space according to the canonical equation of motion, as time passes, there are points that flow in and out of the region $V$, which changes the number of particles in $V$:
$$
\begin{aligned}
\frac{\delta \mathcal{N}(V, t)}{\delta t}
&= \int_V \frac{\partial \mathcal{D}}{\partial t} d\mathbf{q} d\mathbf{p} \\
&= \int_V \frac{\partial}{\partial t} \sum_{i = 1}^N \delta^3(\mathbf{q} - \mathbf{q}_i(t)) \delta^3(\mathbf{p} - \mathbf{p}_i(t)) d\mathbf{q} d\mathbf{p} \\
&= \int_V \sum_{i = 1}^N 
\begin{aligned}[t]
& \left[
    \frac{\partial \delta^3(\mathbf{q} - \mathbf{q}_i(t))}{\partial t} \cdot \delta^3(\mathbf{p} - \mathbf{p}_i(t))  \right. \\
    &\left. \qquad  + \delta^3(\mathbf{q} - \mathbf{q}_i(t)) \cdot \frac{\partial \delta^3(\mathbf{p} - \mathbf{p}_i(t))}{\partial t}
            \right] d\mathbf{q} d\mathbf{p} \\
\end{aligned} \\
&= \int_V \sum_{i = 1}^N
    \begin{aligned}[t]
    & \left[
        -\dot{\mathbf{q}}_i(t) \cdot \frac{\partial \delta^3(\mathbf{q} - \mathbf{q}_i(t))}{\partial \mathbf{q}} \cdot \delta^3(\mathbf{p} - \mathbf{p}_i(t)) \right.\\
    &\left. \qquad - \dot{\mathbf{p}}_i(t) \cdot \frac{\partial \delta^3(\mathbf{p} - \mathbf{p}_i(t))}{\partial \mathbf{p}} \cdot \delta^3(\mathbf{q} - \mathbf{q}_i(t))
    \right] d\mathbf{q} d\mathbf{p}
    \end{aligned}\\
\end{aligned}
$$
Here,
$$
\begin{aligned}
&\quad \int \sum_{i=1}^N \dot{\mathbf{q}}_i(t) \cdot \frac{\delta^3(\mathbf{q} - \mathbf{q}_i(t))}{\partial \mathbf{q}} \cdot \delta^3(\mathbf{p} - \mathbf{p}_i(t)) \\
&= \int \sum_{i=1}^N \dot{\mathbf{q}}_i(t) \cdot \frac{\partial}{\partial \mathbf{q}} \left[
    \delta^3(\mathbf{q} - \mathbf{q}_i(t)) \cdot \delta^3(\mathbf{p} - \mathbf{p}_i(t))
    \right] - \delta^3(\mathbf{q} - \mathbf{q}_i(t)) \cdot \dot{\mathbf{q}_i(t)} \cdot \frac{\partial}{\partial \mathbf{q}} \delta^3(\mathbf{p} - \mathbf{p}_i(t)) \\
\end{aligned}
$$
Since we take $\mathbf{q}$ and $\mathbf{p}$ as independent variables, $\frac{\partial}{\partial \mathbf{q}} \delta^3(\mathbf{p} - \mathbf{p}_i(t)) = 0$, and we have
$$
\begin{aligned}
&\quad \int \sum_{i=1}^N \dot{\mathbf{q}}_i(t) \cdot \frac{\delta^3(\mathbf{q} - \mathbf{q}_i(t))}{\partial \mathbf{q}} \cdot \delta^3(\mathbf{p} - \mathbf{p}_i(t)) \\
&= \int \sum_{i=1}^N \dot{\mathbf{q}}_i(t) \cdot \frac{\partial}{\partial \mathbf{q}} \left[
    \delta^3(\mathbf{q} - \mathbf{q}_i(t)) \cdot \delta^3(\mathbf{p} - \mathbf{p}_i(t)) 
    \right] 
\end{aligned}
$$
Inside the integral, due to the Dirac delta, we can take $\mathbf{q} = \mathbf{q}_i(t)$
$$
\begin{aligned}
&= \int \dot{\mathbf{q}} \cdot \sum_{i=1}^N \frac{\partial}{\partial \mathbf{q}} \left[
    \delta^3(\mathbf{q} - \mathbf{q}_i(t)) \cdot \delta^3(\mathbf{p} - \mathbf{p}_i(t))
    \right] \\
    &= \int \dot{\mathbf{q}} \cdot \frac{\partial \mathcal{D}}{\partial \mathbf{q}}
\end{aligned}
$$
Similarly, we can show that
$$
\int \sum_{i=1}^N \dot{\mathbf{p}}_i(t) \cdot \frac{\delta^3(\mathbf{p} - \mathbf{p}_i(t))}{\partial \mathbf{p}} \cdot \delta^3(\mathbf{q} - \mathbf{q}_i(t)) = \int \dot{\mathbf{p}} \cdot \frac{\partial \mathcal{D}}{\partial \mathbf{p}}
$$
Therefore, we have, for any $V \subset \Omega \times \mathbb{R}^3$,
$$
\frac{\delta \mathcal{N}(V, t)}{\delta t} = -\int_V \left[
    \dot{\mathbf{q}} \cdot \frac{\partial \mathcal{D}}{\partial \mathbf{q}} + \dot{\mathbf{p}} \cdot \frac{\partial \mathcal{D}}{\partial \mathbf{p}}
\right] d\mathbf{q} d\mathbf{p} = \int_V \frac{\partial \mathcal{D}}{\partial t} d\mathbf{q} d\mathbf{p}
$$
which, in the differential form, gives the **Klimontovich equation**:
$$
\frac{\partial \mathcal{D}}{\partial t} + \dot{\mathbf{q}} \cdot \frac{\partial \mathcal{D}}{\partial \mathbf{q}} + \dot{\mathbf{p}} \cdot \frac{\partial \mathcal{D}}{\partial \mathbf{p}} = 0
$$ -->

## One-Particle Distribution Function

### Ensemble Average

Given a set of macroscopic physical quantities such as temperature, pressure, etc., the **ensemble** is a collection of virtual systems (called **microstates**) that share the same macroscopic physical quantities, but differ in the microscopic details, i.e., the exact position and momentum of each particle.

Each microstate can be represented as an ordered set of position and momentum of each particle, which correponds to a point in $\Gamma$-space, i.e., $\gamma = (\mathbf{q}_1, \mathbf{q}_2, \ldots, \mathbf{q}_N, \mathbf{p}_1, \mathbf{p}_2, \cdots, \mathbf{p}_N)$.
This point is called the representative point of the microstate in $\Gamma$-space.

At each point, we can assign the likelihood of the system being in that microstate, which gives us a probability density function $\rho_\Gamma(\gamma, t)$ on $\Gamma$-space.
For example, if the temperature is high, the system is more likely to be spread in the momentum space, rather than near the origin of them momentum space.
We call this assignment of likelihood the **probability density** $\rho_\Gamma$ such that at time $t$, the probability of a region $R$ in $\Gamma$-space is given by
$$
\mathbb{P}(R, t) = \int_{R} \rho_\Gamma(\gamma, t) dv
$$
which is the probability that systems in $R$ can be observed at time $t$, given the macroscopic quantities.

Now, we can define the **ensemble average** of a microscopic quantity $A(\gamma)$ (a quantity that depends on the microscopic details of the system) as:
$$
\langle A \rangle_t = \int_{\Gamma} A(\gamma) \rho_\Gamma(\gamma, t) dv
$$

### Conservation of Probability Density and Liouville's Theorem

Since any microstate just keeps evolving, and no microstate can be created or destroyed,
$$
\begin{aligned}
    \frac{d\mathbb{P}(R, t)}{dt} & = \int_R \frac{\partial \rho_\Gamma (\gamma, t)}{\partial t} dv = - \int_R \nabla_\gamma \cdot (\rho_\Gamma u_\gamma) dv
\end{aligned}
$$
where $\rho_\Gamma u_\gamma$ is the outflow of probability from $R$ at time $t$.
Since the probability of $R$ should be conserved, we have $\frac{d\mathbb{P}(R, t)}{dt} = 0$, which gives us the conservation of probability density:
$$
\frac{\partial \rho_\Gamma}{\partial t} + \nabla_\gamma \cdot (\rho_\Gamma u_\gamma) = 0
$$

Also,
$$
\nabla_\gamma \cdot u_\gamma(\gamma, t) = \sum_{i=1}^N \left[
    \frac{\partial}{\partial \mathbf{q}_i} \cdot \dot{\mathbf{q}}_i + \frac{\partial}{\partial \mathbf{p}_i} \cdot \dot{\mathbf{p}}_i
\right],
$$
by the equation of motion,
$$
\begin{aligned}
\sum_{i=1}^N \left[
    \frac{\partial}{\partial \mathbf{q}_i} \cdot \dot{\mathbf{q}}_i + \frac{\partial}{\partial \mathbf{p}_i} \cdot \dot{\mathbf{p}}_i
\right]
= \sum_{i=1}^N \left[
    \frac{\partial}{\partial \mathbf{q}_i} \cdot \frac{\partial H}{\partial \mathbf{p}_i} - \frac{\partial}{\partial \mathbf{p}_i} \cdot \frac{\partial H}{\partial \mathbf{q}_i}
\right]
= 0
\end{aligned}
$$
which gives us **Liouville's theorem**:
$$
\nabla_\gamma \cdot u_\gamma(\gamma, t) = 0
$$

### One-Particle Distribution Function

Now, the Klimontovich distribution function $\mathcal{D}(\{\mathbf{q}_i , \mathbf{p}_i \};\{\mathbf{q}_i(t), \mathbf{p}_i(t)\})$ is a function on the $\mu$-space, given a microstate and its trajectory $\{(\mathbf{q}_i(t), \mathbf{p}_i(t))\}_{i=1}^N$.
In another perspective, we can also view $\mathcal{D}$ as a function on $\Gamma$-space, given a point in $\mu$-space:
$$
\mathcal{D}(\mathbf{q}, \mathbf{p}; \gamma)
$$
which gives us the freedom to move $\gamma$ around for a fixed $(\mathbf{q}, \mathbf{p})$.

Now we can take the ensemble average of $\mathcal{D}$:
$$
\langle \mathcal{D}(\mathbf{q}, \mathbf{p}; \gamma) \rangle_t = \int_{\Gamma} \mathcal{D}(\mathbf{q}, \mathbf{p}; \gamma) \rho_\Gamma(\gamma, t) dv
$$

Physically, this means that we take the $\Gamma$-space density to be moving with time

Note that the $\mathbf{q}_i(t)$ and $\mathbf{p}_i(t)$ in $\mathcal{D}$ are replaced by the $\mathbf{q}_i$ and $\mathbf{p}_i$ in $\gamma$, which are independent variables in the integral, and they are not functions of $t$:
$$
\begin{aligned}
&\quad \int_{\Gamma} \mathcal{D}(\mathbf{q}, \mathbf{p}; \gamma) \rho_\Gamma(\gamma, t) dv \\
& = \int_{\Gamma} \sum_{i = 1}^N \delta^3(\mathbf{q} - \mathbf{q}_i) \delta^3(\mathbf{p} - \mathbf{p}_i) \rho_\Gamma(\mathbf{q}_j, \mathbf{p}_j, t) dv \\
& = \sum_{i = 1}^N \int_{\Gamma} \delta^3(\mathbf{q} - \mathbf{q}_i) \delta^3(\mathbf{p} - \mathbf{p}_i) \rho_\Gamma(\mathbf{q}_1, \mathbf{p}_1, \ldots, t) dv
\end{aligned}
$$
Here, if we define $\tilde{f}_k$ as follows:
$$
\begin{aligned}
    \tilde{f}_k(\mathbf{q}, \mathbf{p}, t)
    :&= \int_{\Gamma} \delta^3(\mathbf{q} - \mathbf{q}_k) \delta^3(\mathbf{p} - \mathbf{p}_k) \rho_\Gamma(\mathbf{q}_1, \mathbf{p}_1, \ldots, t) dv \\
    &= \int_{\mu^{N-1}} \rho_\Gamma(\mathbf{q}_1, \mathbf{p}_1, \ldots, \mathbf{q}_{k-1}, \mathbf{p}_{k-1}, \mathbf{q}, \mathbf{p}, \ldots, t) d\mathbf{q}_2 d\mathbf{p}_2 \cdots d\mathbf{q}_N d\mathbf{p}_N
\end{aligned}
$$
the sum can be rewritten as
$$
\sum_{i = 1}^N \tilde{f}_i(\mathbf{q}, \mathbf{p}, t)
$$
Since the particles are identical and indistinguishable, we have $\tilde{f} := \tilde{f}_i = \tilde{f}_j$ for any $i, j$,
$$
\langle \mathcal{D}(\mathbf{q}, \mathbf{p}; \gamma) \rangle_t = N \tilde{f}(\mathbf{q}, \mathbf{p}, t)
$$
Often it is more useful to work with $N \tilde{f}$ instead of $\tilde{f}$, so we define the **one-particle distribution function** $f$ as
$$
f(\mathbf{q}, \mathbf{p}, t) = N \tilde{f}(\mathbf{q}, \mathbf{p}, t) = \langle \mathcal{D}(\mathbf{q}, \mathbf{p}; \gamma) \rangle_t.
$$

## Boltzmann Equation

### Reduced One-Particle Equation

Now, we also want to consider the time evolution of $f$,
$$
f(\mathbf{q}, \mathbf{p}, t)
= N \int_{\mu^{N-1}} \rho_\Gamma(\mathbf{q}, \mathbf{p}, \mathbf{q}_2, \mathbf{p}_2, \ldots, t) dv'
$$
where $dv' = d\mathbf{q}_2 d\mathbf{p}_2 \cdots d\mathbf{q}_N d\mathbf{p}_N$.

This $f$ is important because if we know $f$, we know the particle number density, the average velocity and energy density at each point in $\Omega$.
Notice that the time dependence of $f$ comes from $\rho_\Gamma$, so finding the time evolution of $f$ necessitates finding the time evolution of $\rho_\Gamma$.

From the previous discussion, we know that the probability density $\rho_\Gamma$ is locally conserved in $\Gamma$-space:
$$
\frac{\partial \rho_\Gamma(\mathbf{q}_1, \mathbf{p}_1, \ldots, \mathbf{q}_N, \mathbf{p}_N, t)}{\partial t} = - \nabla_\gamma \cdot (\rho_\Gamma u_\gamma)
$$
here, we integrate both sides over $\mu^{N-1} \subset \Gamma$, with $dv' = d\mathbf{q}_2 d\mathbf{p}_2 \cdots d\mathbf{q}_N d\mathbf{p}_N$:
$$
\begin{aligned}
\int_{\mu^{N-1}} \frac{\partial \rho_\Gamma(\mathbf{q}_1, \mathbf{p}_1, \ldots, \mathbf{q}_N, \mathbf{p}_N, t)}{\partial t} dv'
&= - \int_{\mu^{N-1}} \nabla_\gamma \cdot (\rho_\Gamma u_\gamma) dv' \\
\frac{\partial \tilde{f}_1(\mathbf{q}_1, \mathbf{p}_1, t)}{\partial t}
&= - \int_{\mu^{N-1}} \sum_{i=1}^N \left[
    \frac{\partial}{\partial \mathbf{q}_i} \cdot (\rho_\Gamma \dot{\mathbf{q}}_i) + \frac{\partial}{\partial \mathbf{p}_i} \cdot (\rho_\Gamma \dot{\mathbf{p}}_i)
\right] dv'
\end{aligned}
$$
here, we separate the term with $i = 1$ from the rest of the terms:
$$
\begin{aligned}
&= - \int_{\mu^{N-1}} \left[
    \frac{\partial}{\partial \mathbf{q}_1} \cdot (\rho_\Gamma \dot{\mathbf{q}}_1) + \frac{\partial}{\partial \mathbf{p}_1} \cdot (\rho_\Gamma \dot{\mathbf{p}}_1 )
\right] dv' - \int_{\mu^{N-1}} \sum_{i=2}^N \left[
    \frac{\partial}{\partial \mathbf{q}_i} \cdot (\rho_\Gamma \dot{\mathbf{q}}_i) + \frac{\partial}{\partial \mathbf{p}_i} \cdot (\rho_\Gamma \dot{\mathbf{p}}_i)
\right] dv'
\end{aligned}
$$
Let us calculate the second term first:
$$
\begin{aligned}
\int_{\mu^{N-1}} \sum_{i=2}^N \left[
    \frac{\partial}{\partial \mathbf{q}_i} \cdot (\rho_\Gamma \dot{\mathbf{q}}_i) + \frac{\partial}{\partial \mathbf{p}_i} \cdot (\rho_\Gamma \dot{\mathbf{p}}_i)
\right] dv'
&= \int_{\mu^{N-1}} \nabla_{\gamma'} \cdot (\rho_\Gamma u_{\gamma'}) dv' \\
&= \int_{\partial \mu^{N-1}} \rho_\Gamma u_{\gamma'} \cdot d\mathbf{s}'
\end{aligned}
$$
where $\gamma' = (\mathbf{q}_2, \mathbf{p}_2, \ldots, \mathbf{q}_N, \mathbf{p}_N)$ and $u_{\gamma'} = (\dot{\mathbf{q}}_2, \dot{\mathbf{p}}_2, \ldots, \dot{\mathbf{q}}_N, \dot{\mathbf{p}}_N)$.

The boundary $\partial \mu^{N-1}$ consists of points where at least one of the particles (except the first particle) is at the boundary of $\Omega$ or has infinite momentum.
The spatial boundary of $\Omega$ is essentially a wall which particles cannot move through, so the outflow of probability from $\partial \Omega$ is zero.
Also, the probability of particles having infinite momentum is zero, so the outflow of probability from the boundary of momentum space is also zero.
Therefore, we have
$$
\int_{\partial \mu^{N-1}} \rho_\Gamma u_{\gamma'} \cdot d\mathbf{s}' = 0
$$
which gives us
$$
\int_{\mu^{N-1}} \sum_{i=2}^N \left[
    \frac{\partial}{\partial \mathbf{q}_i} \cdot (\rho_\Gamma \dot{\mathbf{q}}_i) + \frac{\partial}{\partial \mathbf{p}_i} \cdot (\rho_\Gamma \dot{\mathbf{p}}_i)
\right] dv' = 0
$$
and hence
$$
\begin{aligned}
\frac{\partial \tilde{f}_1(\mathbf{q}_1, \mathbf{p}_1, t)}{\partial t}
&= - \int_{\mu^{N-1}} \left[
    \frac{\partial}{\partial \mathbf{q}_1} \cdot (\rho_\Gamma \dot{\mathbf{q}}_1) + \frac{\partial}{\partial \mathbf{p}_1} \cdot (\rho_\Gamma \dot{\mathbf{p}}_1 )
\right] dv'
\end{aligned}
$$
Since the integral is taken over $\mu^{N-1}$, we can take $\mathbf{q}_1$ and $\mathbf{p}_1$ as constants in the integral, which gives us
$$
\begin{aligned}
&= - \frac{\partial}{\partial \mathbf{q}_1} \int_{\mu^{N-1}} \rho_\Gamma \dot{\mathbf{q}}_1 dv' - \frac{\partial}{\partial \mathbf{p}_1} \int_{\mu^{N-1}} \rho_\Gamma \dot{\mathbf{p}}_1 dv'.
\end{aligned}
$$

In summary,
$$
\frac{\partial \tilde{f}_1(\mathbf{q}_1, \mathbf{p}_1, t)}{\partial t} + \frac{\partial}{\partial \mathbf{q}_1} \int_{\mu^{N-1}} \rho_\Gamma \dot{\mathbf{q}}_1 dv' + \frac{\partial}{\partial \mathbf{p}_1} \int_{\mu^{N-1}} \rho_\Gamma \dot{\mathbf{p}}_1 dv' = 0
$$
This is the reduced one-particle equation.

If we take $z = (\mathbf{q}_1, \mathbf{p}_1) \in \mu$,
$$
\frac{\partial \tilde{f}_1(z, t)}{\partial t} + \sum_{i=1}^N \frac{\partial}{\partial z_i} \int_{\mu^{N-1}} \rho_\Gamma u^i_{\mu} dv' = 0
$$
and the integral can be viewed as probability current density in $\mu$-space:
$$
J^i (z, t) : = \int_{\mu^{N-1}} \rho_\Gamma u^i_{\mu} dv'
$$
where $u^i_{\mu}$ is the $i$-th component of $u_\mu = (\dot{\mathbf{q}}_1, \dot{\mathbf{p}}_1)$.
This gives us
$$
\frac{\partial \tilde{f}_1(z, t)}{\partial t} + \partial_i \cdot J^i(z, t) = 0
$$
where $\partial_i := \frac{\partial}{\partial z_i}$.

Under coordinate transformation $z' = \phi(z)$,
$$
\begin{aligned}
\frac{\partial \tilde{f}_1(z, t)}{\partial t} + \frac{1}{\mathcal{J}} \partial_i \cdot (\mathcal{J} J^i(z, t)) = 0
\end{aligned}
$$
where $\mathcal{J} = \det D\phi(z)$.

### Boltzmann Equation

Now, the probability current density $J(z, t)$ can be decomposed into two parts: $u_\mu \tilde{f}_1(z, t)$, which is the current density without collision/ interactions (i.e. if we assume $\dot{\mathbf{q}}_1$ and $\dot{\mathbf{p}}_1$ are independent of the other particles, such as only considering external forces), and $K_c(z, t)$, which is the current density due to collision/ interactions (collisions change the momenta of the particles, which brings in/ takes out ):
$$
J^i(z, t) = u^i_\mu \tilde{f}_1(z, t) + K^i_c(z, t)
$$
if we substitute this into the reduced one-particle equation, we have
$$
\frac{\partial \tilde{f}_1(z, t)}{\partial t} + \frac{1}{\mathcal{J}} \partial_i \cdot (\mathcal{J} u_\mu^i \tilde{f}_1(z, t)) = - \frac{1}{\mathcal{J}} \partial_i \cdot (\mathcal{J} K^i_c(z, t)).
$$
If we multiply both sides by $N$, we have
$$
\frac{\partial f(z, t)}{\partial t} + \frac{1}{\mathcal{J}} \partial_i \cdot (\mathcal{J} u_\mu^i f(z, t)) = - \frac{N}{\mathcal{J}} \partial_i \cdot (\mathcal{J} K^i_c(z, t))
$$
and letting RHS be $C[f]$, we have the conservative **Boltzmann equation**:
$$
\frac{\partial f(\mathbf{q}, \mathbf{p}, t)}{\partial t} + \frac{1}{\mathcal{J}} \partial_i \cdot (\mathcal{J} u_\mu^i f(\mathbf{q}, \mathbf{p}, t)) = C[f]
$$
In a more familar form, we have
$$
\frac{\partial f(\mathbf{q}, \mathbf{p}, t)}{\partial t} + \nabla_\mathbf{q} \cdot (\dot{\mathbf{q}} f) + \nabla_\mathbf{p} \cdot (\dot{\mathbf{p}} f) = C[f]
$$
Equivalently, momentum is replaced by velocity:
$$
\frac{\partial f(\mathbf{x}, \mathbf{v}, t)}{\partial t} + \nabla_\mathbf{x} \cdot (\dot{\mathbf{x}} f) + \nabla_\mathbf{v} \cdot (\dot{\mathbf{v}} f) = C[f]
$$

## Boltzmann Equation in Spherical Coordinates

### Setup

We take the spatial coordinates to be spherical coordinates $(q_r, q_\theta, q_\phi)$, with basis vectors $\mathbf{e}_r$, $\mathbf{e}_\theta$, and $\mathbf{e}_\phi$. The velocity direction is parameterized by the angular variables $(\theta_\nu,\phi_\nu)$, where $\mathbf{e}_\theta$ is the $x$-axis, $\mathbf{e}_\phi$ is the $y$-axis, and $\mathbf{e}_r$ is the $z$-axis:
$$
\mathbf{v} = ||\mathbf{v}|| \cdot (
    \sin \theta_\nu \cos \phi_\nu \mathbf{e}_\theta + \sin \theta_\nu \sin \phi_\nu \mathbf{e}_\phi + \cos \theta_\nu \mathbf{e}_r
)
$$
For convinience, we also write the velocity direction in terms of $\mu_\nu = \cos \theta_\nu$.

Now, from the following expression of the Boltzmann equation,
$$
\frac{\partial f(\mathbf{q}, \mathbf{p}, t)}{\partial t} + \frac{1}{\mathcal{J}} \partial_i \cdot (\mathcal{J} u_\mu^i f(\mathbf{q}, \mathbf{p}, t)) = C[f]
$$

We know that $\mathcal{J} dq_x dq_y dq_z d\Omega_\nu = q_r^2 \sin q_\theta \, dq_r dq_\theta dq_\phi d\mu_\nu d\phi_\nu$, where $d\Omega_\nu = \sin \theta_\nu d\theta_\nu d\phi_\nu = d\mu_\nu d\phi_\nu$ is the solid angle element in the velocity space, and $\mu_\nu = \cos \theta_\nu$.

If we write out the summation explicitly, we have, for $f = f(q_r, q_\theta, q_\phi, \mu_\nu, \phi_\nu, t)$, 
$$
\begin{aligned}
    & \frac{\partial f}{\partial t}
    + \underbrace{
        \frac{1}{q_r^2 \sin q_\theta} \frac{\partial}{\partial r} \left(
            q_r^2 \sin q_\theta \, \dot{q}_r f
        \right)
    }_{r \text{ term}} \\
    & \qquad
    + \underbrace{
        \frac{1}{q_r^2 \sin q_\theta} \frac{\partial}{\partial \theta} \left(
                q_r^2 \sin q_\theta \, \dot{q}_\theta f
            \right)
    }_{\theta \text{ term}}
    + \underbrace{
        \frac{1}{q_r^2 \sin q_\theta} \frac{\partial}{\partial \phi} \left(
            q_r^2 \sin q_\theta \, \dot{q}_\phi f
        \right)
    }_{\phi \text{ term}} \\
    & \qquad \qquad
    + \underbrace{
        \frac{1}{q_r^2 \sin q_\theta} \frac{\partial}{\partial \mu_\nu} \left(
            q_r^2 \sin q_\theta \, \dot{\mu}_\nu f
        \right)
    }_{\mu_\nu \text{ term}}
    + \underbrace{
        \frac{1}{q_r^2 \sin q_\theta} \frac{\partial}{\partial \phi_\nu} \left(
            q_r^2 \sin q_\theta \, \dot{\phi}_\nu f
        \right)
    }_{\phi_\nu \text{ term}}
\end{aligned}
$$
Let us then calculate each term.

$r$ term: since $q_\theta$ is independent of $r$, we have
$$
\frac{1}{q_r^2 \sin q_\theta} \frac{\partial}{\partial r} \left(
    q_r^2 \sin q_\theta \, \dot{q}_r f
\right) = \frac{1}{q_r^2} \frac{\partial}{\partial r} \left(
    q_r^2 \, \dot{q}_r f
\right)
$$
$\theta$ term: here, $q_r$ is independent of $\theta$, so we have
$$
\frac{1}{q_r^2 \sin q_\theta} \frac{\partial}{\partial \theta} \left(
    q_r^2 \sin q_\theta \, \dot{q}_\theta f
\right) = \frac{1}{\sin q_\theta} \frac{\partial}{\partial \theta} \left(
    \sin q_\theta \, \dot{q}_\theta f
\right)
$$
$\phi$ term: here, $q_r$ and $q_\theta$ are independent of $\phi$, so we have
$$
\frac{1}{q_r^2 \sin q_\theta} \frac{\partial}{\partial \phi} \left(
    q_r^2 \sin q_\theta \, \dot{q}_\phi f
\right) = \frac{\partial}{\partial \phi} \left(
    \dot{q}_\phi f
\right)
$$
$\mu_\nu$ term: here, all the spatial coordinates are independent of $\mu_\nu$, so we have
$$
\frac{1}{q_r^2 \sin q_\theta} \frac{\partial}{\partial \mu_\nu} \left(
    q_r^2 \sin q_\theta \, \dot{\mu}_\nu f
\right) = \frac{\partial}{\partial \mu_\nu} \left(
    \dot{\mu}_\nu f
\right)
$$
$\phi_\nu$ term: here, all the spatial coordinates are independent of $\phi_\nu$, so we have
$$
\frac{1}{q_r^2 \sin q_\theta} \frac{\partial}{\partial \phi_\nu} \left(
    q_r^2 \sin q_\theta \, \dot{\phi}_\nu f
\right) = \frac{\partial}{\partial \phi_\nu} \left(
    \dot{\phi}_\nu f
\right)
$$
Which gives us a more simplified form of the Boltzmann equation in spherical coordinates:
$$
\begin{aligned}
    & \frac{\partial f}{\partial t}
    + \frac{1}{q_r^2} \frac{\partial}{\partial r} \left(
        q_r^2 \, \dot{q}_r f
    \right)
    + \frac{1}{\sin q_\theta} \frac{\partial}{\partial \theta} \left(
        \sin q_\theta \, \dot{q}_\theta f
    \right) \\
    & \qquad + \frac{\partial}{\partial \phi} \left(
        \dot{q}_\phi f
    \right) 
     + \frac{\partial}{\partial \mu_\nu} \left(
        \dot{\mu}_\nu f
    \right)
    + \frac{\partial}{\partial \phi_\nu} \left(
        \dot{\phi}_\nu f
    \right) = C[f]
\end{aligned}
$$

To further proceed, we need to calculate the time derivatives $\dot{q}_r$, $\dot{q}_\theta$, $\dot{q}_\phi$, $\dot{\mu}_\nu$, and $\dot{\phi}_\nu$.


### Calculating Time Derivatives

We consider that the particle moves at some constant speed $c$, then we have
$$
\mathbf{v} = c \mathbf{n}, \quad \text{where } \mathbf{n} = \sin \theta_\nu \cos \phi_\nu \mathbf{e}_\theta + \sin \theta_\nu \sin \phi_\nu \mathbf{e}_\phi + \cos \theta_\nu \mathbf{e}_r.
$$

Now, we can also write the velocity in the position space with basis $\mathbf{e}_r, \mathbf{e}_\theta, \mathbf{e}_\phi$:
$$
\mathbf{v} = \frac{dq_r}{dt} \mathbf{e}_r + q_r \frac{d q_\theta}{dt} \mathbf{e}_\theta + q_r \sin q_\theta \frac{d q_\phi}{dt} \mathbf{e}_\phi
$$
Comparing the components,
$$
\begin{dcases}
    \frac{d q_r}{dt} = c \cos \theta_\nu = c \mu_\nu \\
    \frac{d q_\theta}{dt} = \frac{c}{q_r} \sin \theta_\nu \cos \phi_\nu \\
    \frac{d q_\phi}{dt} = \frac{c}{q_r \sin q_\theta} \sin \theta_\nu \sin \phi_\nu
\end{dcases}
$$

To re-write the LHS of the Boltzmann equation, we can only consider collisionless situation, where the particles are moving in a straight line:
$$
\dot{\mathbf{n}} = 0
$$
the calculation here is a little convoluted, because we need to track change in both the component and basis of the velocity:
$$
\begin{aligned}
\dot{\mathbf{e}}_r &= \dot{q}_{\theta} \mathbf{e}_\theta + \dot{q}_{\phi} \sin q_\theta \mathbf{e}_\phi \\
\dot{\mathbf{e}}_\theta &= -\dot{q}_{\theta} \mathbf{e}_r + \dot{q}_{\phi} \cos q_\theta \mathbf{e}_\phi \\
\dot{\mathbf{e}}_\phi &= -\dot{q}_{\phi} \sin q_\theta \mathbf{e}_r - \dot{q}_{\phi} \cos q_\theta \mathbf{e}_\theta
\end{aligned}
$$
refer [here](/content/Tedious%20Calculations/sphere.md) for the detailed calculation of the above.

Then we have
$$
\begin{aligned}
    \dot{\mathbf{n}} &= \frac{d}{dt} \left(
        \cos \theta_\nu \mathbf{e}_r + \sin \theta_\nu \cos \phi_\nu \mathbf{e}_\theta + \sin \theta_\nu \sin \phi_\nu \mathbf{e}_\phi
    \right) \\
    &=
    \begin{aligned}[t]
        & - \dot{\theta}_\nu \sin \theta_\nu \mathbf{e}_r + \cos \theta_\nu \left(
            \dot{q}_{\theta} \mathbf{e}_\theta + \dot{q}_{\phi} \sin q_\theta \mathbf{e}_\phi
        \right) \\
        & \qquad + \frac{d}{dt} (\sin \theta_\nu \cos \phi_\nu) \mathbf{e}_\theta
        + \sin \theta_\nu \cos \phi_\nu \left(
            - \dot{q}_{\theta} \mathbf{e}_r + \dot{q}_{\phi} \cos q_\theta \mathbf{e}_\phi
        \right ) \\
        & \qquad + \frac{d}{dt} (\sin \theta_\nu \sin \phi_\nu) \mathbf{e}_\phi
        + \sin \theta_\nu \sin \phi_\nu \left(
            -\dot{q}_{\phi} \sin q_\theta \mathbf{e}_r - \dot{q}_{\phi} \cos q_\theta \mathbf{e}_\theta
        \right)
    \end{aligned} \\
\end{aligned}
$$
Now compute the time derivatives of the scalar coefficients:
$$
\begin{aligned}
\frac{d}{dt}(\sin \theta_\nu \cos \phi_\nu)
&=
\dot{\theta}_\nu \cos \theta_\nu \cos \phi_\nu
- \dot{\phi}_\nu \sin \theta_\nu \sin \phi_\nu, \\
\frac{d}{dt}(\sin \theta_\nu \sin \phi_\nu)
&=
\dot{\theta}_\nu \cos \theta_\nu \sin \phi_\nu
+ \dot{\phi}_\nu \sin \theta_\nu \cos \phi_\nu.
\end{aligned}
$$
Hence
$$
\begin{aligned}
\dot{\mathbf{n}}
&=
\begin{aligned}[t]
& \left(
    -\dot{\theta}_\nu \sin \theta_\nu
    - \dot{q}_\theta \sin \theta_\nu \cos \phi_\nu
    - \dot{q}_\phi \sin q_\theta \sin \theta_\nu \sin \phi_\nu
\right)\mathbf{e}_r \\
&\qquad +
\left(
    \dot{q}_\theta \cos \theta_\nu
    + \dot{\theta}_\nu \cos \theta_\nu \cos \phi_\nu
    - \dot{\phi}_\nu \sin \theta_\nu \sin \phi_\nu
    - \dot{q}_\phi \cos q_\theta \sin \theta_\nu \sin \phi_\nu
\right)\mathbf{e}_\theta \\
&\qquad +
\left(
    \dot{q}_\phi \sin q_\theta \cos \theta_\nu
    + \dot{q}_\phi \cos q_\theta \sin \theta_\nu \cos \phi_\nu
    + \dot{\theta}_\nu \cos \theta_\nu \sin \phi_\nu
    + \dot{\phi}_\nu \sin \theta_\nu \cos \phi_\nu
\right)\mathbf{e}_\phi.
\end{aligned}
\end{aligned}
$$

Since the motion is collisionless, the direction vector is constant along the trajectory, so
$$
\dot{\mathbf{n}} = 0.
$$
Because $\mathbf{e}_r$, $\mathbf{e}_\theta$, and $\mathbf{e}_\phi$ are linearly independent, each coefficient must vanish:
$$
\begin{dcases}
    -\dot{\theta}_\nu \sin \theta_\nu
    - \dot{q}_\theta \sin \theta_\nu \cos \phi_\nu
    - \dot{q}_\phi \sin q_\theta \sin \theta_\nu \sin \phi_\nu = 0, \\
    \dot{q}_\theta \cos \theta_\nu
    + \dot{\theta}_\nu \cos \theta_\nu \cos \phi_\nu
    - \dot{\phi}_\nu \sin \theta_\nu \sin \phi_\nu
    - \dot{q}_\phi \cos q_\theta \sin \theta_\nu \sin \phi_\nu = 0, \\
    \dot{q}_\phi \sin q_\theta \cos \theta_\nu
    + \dot{q}_\phi \cos q_\theta \sin \theta_\nu \cos \phi_\nu
    + \dot{\theta}_\nu \cos \theta_\nu \sin \phi_\nu
    + \dot{\phi}_\nu \sin \theta_\nu \cos \phi_\nu = 0.
\end{dcases}
$$

From the first equation, assuming $\sin \theta_\nu \neq 0$,
$$
\dot{\theta}_\nu
=
- \dot{q}_\theta \cos \phi_\nu
- \dot{q}_\phi \sin q_\theta \sin \phi_\nu.
$$
Substitute
$$
\dot{q}_\theta = \frac{c}{q_r} \sin \theta_\nu \cos \phi_\nu,
\qquad
\dot{q}_\phi = \frac{c}{q_r \sin q_\theta} \sin \theta_\nu \sin \phi_\nu,
$$
to obtain
$$
\begin{aligned}
\dot{\theta}_\nu
&=
- \frac{c}{q_r} \sin \theta_\nu \cos^2 \phi_\nu
- \frac{c}{q_r \sin q_\theta} \sin \theta_\nu \sin \phi_\nu \sin q_\theta \sin \phi_\nu \\
&=
- \frac{c}{q_r} \sin \theta_\nu (\cos^2 \phi_\nu + \sin^2 \phi_\nu) \\
&=
\boxed{- \frac{c}{q_r} \sin \theta_\nu }.
\end{aligned}
$$

Now use the second equation:
$$
\dot{q}_\theta \cos \theta_\nu
+ \dot{\theta}_\nu \cos \theta_\nu \cos \phi_\nu
- \dot{\phi}_\nu \sin \theta_\nu \sin \phi_\nu
- \dot{q}_\phi \cos q_\theta \sin \theta_\nu \sin \phi_\nu = 0.
$$
Substituting $\dot{\theta}_\nu = - \dfrac{c}{q_r} \sin \theta_\nu$ and $\dot{q}_\theta = \dfrac{c}{q_r} \sin \theta_\nu \cos \phi_\nu$, the first two terms cancel:
$$
\frac{c}{q_r} \sin \theta_\nu \cos \phi_\nu \cos \theta_\nu
- \frac{c}{q_r} \sin \theta_\nu \cos \phi_\nu \cos \theta_\nu
= 0.
$$
Thus
$$
- \dot{\phi}_\nu \sin \theta_\nu \sin \phi_\nu
- \dot{q}_\phi \cos q_\theta \sin \theta_\nu \sin \phi_\nu = 0,
$$
which gives
$$
\dot{\phi}_\nu = - \dot{q}_\phi \cos q_\theta.
$$
Substituting $\dot{q}_\phi = \dfrac{c}{q_r \sin q_\theta} \sin \theta_\nu \sin \phi_\nu$, we obtain
$$
\boxed{
\dot{\phi}_\nu
=
- \frac{c}{q_r} \cot q_\theta \sin \theta_\nu \sin \phi_\nu
}.
$$

Finally, the third equation serves as a consistency check:
$$
\begin{aligned}
&\quad
\dot{q}_\phi \sin q_\theta \cos \theta_\nu
+ \dot{q}_\phi \cos q_\theta \sin \theta_\nu \cos \phi_\nu
+ \dot{\theta}_\nu \cos \theta_\nu \sin \phi_\nu
+ \dot{\phi}_\nu \sin \theta_\nu \cos \phi_\nu \\
&=
\frac{c}{q_r} \sin \theta_\nu \sin \phi_\nu \cos \theta_\nu
+ \frac{c}{q_r} \cot q_\theta \sin^2 \theta_\nu \sin \phi_\nu \cos \phi_\nu \\
&\qquad
- \frac{c}{q_r} \sin \theta_\nu \cos \theta_\nu \sin \phi_\nu
- \frac{c}{q_r} \cot q_\theta \sin^2 \theta_\nu \sin \phi_\nu \cos \phi_\nu \\
&= 0.
\end{aligned}
$$
So the result is consistent.

Therefore, in the collisionless case,
$$
\boxed{
\begin{dcases}
    \dot{\theta}_\nu = - \dfrac{c}{q_r} \sin \theta_\nu, \\
    \dot{\phi}_\nu = - \dfrac{c}{q_r} \cot q_\theta \sin \theta_\nu \sin \phi_\nu.
\end{dcases}
}
$$
But the variable we use is $\mu_\nu = \cos \theta_\nu$:
$$
\dot{\mu}_\nu = - \sin \theta_\nu \dot{\theta}_\nu = \frac{c}{q_r} \sin^2 \theta_\nu = \frac{c}{q_r} (1 - \mu_\nu^2).
$$

Together with
$$
\begin{dcases}
    \dot{q}_r = c \cos \theta_\nu = c \mu_\nu, \\
    \dot{q}_\theta = \dfrac{c}{q_r} \sin \theta_\nu \cos \phi_\nu, \\
    \dot{q}_\phi = \dfrac{c}{q_r \sin q_\theta} \sin \theta_\nu \sin \phi_\nu,
\end{dcases}
$$
these are the characteristic equations for free streaming in spherical coordinates.

Remember the Boltzmann equation in spherical coordinates:
$$
\begin{aligned}
    & \frac{\partial f}{\partial t}
    + \frac{1}{q_r^2} \frac{\partial}{\partial r} \left(
        q_r^2 \, \dot{q}_r f
    \right)
    + \frac{1}{\sin q_\theta} \frac{\partial}{\partial \theta} \left(
        \sin q_\theta \, \dot{q}_\theta f
    \right) \\
    & \qquad + \frac{\partial}{\partial \phi} \left(
        \dot{q}_\phi f
    \right)
     + \frac{\partial}{\partial \mu_\nu} \left(
        \dot{\mu}_\nu f
    \right)
    + \frac{\partial}{\partial \phi_\nu} \left(
        \dot{\phi}_\nu f
    \right) = C[f]
\end{aligned}
$$
Substituting the above time derivatives, we have
$$
\begin{aligned}
    & \frac{\partial f}{\partial t}
    + \frac{1}{q_r^2} \frac{\partial}{\partial r} \left(
        q_r^2 \, c \mu_\nu f
    \right)
    + \frac{1}{\sin q_\theta} \frac{\partial}{\partial \theta} \left(
        \sin q_\theta \, \frac{c}{q_r} \sin \theta_\nu \cos \phi_\nu f
    \right) \\
    & \qquad + \frac{\partial}{\partial \phi} \left(
        \frac{c}{q_r \sin q_\theta} \sin \theta_\nu \sin \phi_\nu f
    \right)
     + \frac{\partial}{\partial \mu_\nu} \left(
        \frac{c}{q_r} (1 - \mu_\nu^2) f
    \right) \\
    &\qquad \quad + \frac{\partial}{\partial \phi_\nu} \left(
        -\frac{c}{q_r} \cot q_\theta \sin \theta_\nu \sin \phi_\nu  f
    \right) = C[f]
\end{aligned}
$$
We can take some factors out of the derivatives:
$$
\implies \quad
\begin{aligned}[t]
    & \frac{\partial f}{\partial t}
    + c \frac{\mu_\nu}{q_r^2} \frac{\partial}{\partial r} \left(
        q_r^2 \,  f
    \right)
    + c \frac{q_r \sin \theta_\nu \cos \phi_\nu}{\sin q_\theta} \frac{\partial}{\partial \theta} \left(
        \sin q_\theta \,  f
    \right) \\
    & \qquad + c \frac{\sqrt{1 - \mu_\nu^2} \sin \phi_\nu}{q_r \sin q_\theta} \frac{\partial}{\partial \phi} \left(
          f
    \right)
     + c \frac{1}{q_r}\frac{\partial}{\partial \mu_\nu} \left(
        (1 - \mu_\nu^2) f
    \right) \\
    &\qquad \quad - c\frac{(1 - \mu_\nu^2)^{1/2} \cot q_\theta}{q_r}\frac{\partial}{\partial \phi_\nu} \left(
            \sin \phi_\nu f
    \right) = C[f]
\end{aligned} \\
$$
Dividing both sides by $c$, and replacing $q_\cdot \to r, \theta, \phi$ for better readability, we have
$$
\begin{aligned}
    & \frac{1}{c} \frac{\partial f}{\partial t}
    + \frac{\mu_\nu}{r^2} \frac{\partial}{\partial r} \left(
        r^2 \,  f
    \right)
    + \frac{r \sin \theta_\nu \cos \phi_\nu}{\sin \theta} \frac{\partial}{\partial \theta} \left(
        \sin \theta \,  f
    \right) \\
    & \qquad + \frac{\sqrt{1 - \mu_\nu^2} \sin \phi_\nu}{r \sin \theta} \frac{\partial}{\partial \phi} \left(
          f  \right)
     + \frac{1}{r}\frac{\partial}{\partial \mu_\nu} \left[
        (1 - \mu_\nu^2) \, f
    \right] \\
    &\qquad \quad - \frac{(1 - \mu_\nu^2)^{1/2}}{r} \cot \theta \, \frac{\partial}{\partial \phi_\nu} \left(
            \sin \phi_\nu f
    \right) = C\left[ \frac{f}{c} \right]
\end{aligned}
$$
which is the conservative form of the Boltzmann equation in spherical coordinates.