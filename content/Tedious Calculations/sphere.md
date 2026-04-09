---
title: "Spherical Coordinates"
date: "2026-04-10"
tags: ["calculus", "coordinate transformation"]
---

## Coordinate Map

We use the spherical coordinates $(r,\theta,\phi)$ defined by
$$
\begin{dcases}
x = r \sin \theta \cos \phi, \\
y = r \sin \theta \sin \phi, \\
z = r \cos \theta,
\end{dcases}
$$
where
$$
r \ge 0,
\qquad
0 \le \theta \le \pi,
\qquad
0 \le \phi < 2\pi.
$$

Equivalently, the position vector is
$$
\mathbf{x}(r,\theta,\phi)
=
\bigl(
r \sin \theta \cos \phi,\;
r \sin \theta \sin \phi,\;
r \cos \theta
\bigr).
$$

## Differential Geometry of the Coordinates

Differentiate $\mathbf{x}(r,\theta,\phi)$ with respect to each coordinate:
$$
\begin{aligned}
\frac{\partial \mathbf{x}}{\partial r}
&=
\bigl(
\sin \theta \cos \phi,\;
\sin \theta \sin \phi,\;
\cos \theta
\bigr), \\
\frac{\partial \mathbf{x}}{\partial \theta}
&=
\bigl(
r \cos \theta \cos \phi,\;
r \cos \theta \sin \phi,\;
-r \sin \theta
\bigr), \\
\frac{\partial \mathbf{x}}{\partial \phi}
&=
\bigl(
-r \sin \theta \sin \phi,\;
r \sin \theta \cos \phi,\;
0
\bigr).
\end{aligned}
$$

These are the tangent vectors to the coordinate curves. Their lengths are
$$
\begin{aligned}
\left\lVert \frac{\partial \mathbf{x}}{\partial r} \right\rVert
&=
\sqrt{
\sin^2 \theta \cos^2 \phi
+ \sin^2 \theta \sin^2 \phi
+ \cos^2 \theta
}
= 1, \\
\left\lVert \frac{\partial \mathbf{x}}{\partial \theta} \right\rVert
&=
\sqrt{
r^2 \cos^2 \theta \cos^2 \phi
+ r^2 \cos^2 \theta \sin^2 \phi
+ r^2 \sin^2 \theta
}
= r, \\
\left\lVert \frac{\partial \mathbf{x}}{\partial \phi} \right\rVert
&=
\sqrt{
r^2 \sin^2 \theta \sin^2 \phi
+ r^2 \sin^2 \theta \cos^2 \phi
}
= r \sin \theta.
\end{aligned}
$$

Therefore the spherical scale factors are
$$
h_r = 1,
\qquad
h_\theta = r,
\qquad
h_\phi = r \sin \theta.
$$

Dividing each tangent vector by its length gives the orthonormal basis vectors:
$$
\begin{aligned}
\mathbf{e}_r
&=
\bigl(
\sin \theta \cos \phi,\;
\sin \theta \sin \phi,\;
\cos \theta
\bigr), \\
\mathbf{e}_\theta
&=
\bigl(
\cos \theta \cos \phi,\;
\cos \theta \sin \phi,\;
-\sin \theta
\bigr), \\
\mathbf{e}_\phi
&=
\bigl(
-\sin \phi,\;
\cos \phi,\;
0
\bigr).
\end{aligned}
$$

Since
$$
d\mathbf{x}
=
\frac{\partial \mathbf{x}}{\partial r} \, dr
+ \frac{\partial \mathbf{x}}{\partial \theta} \, d\theta
+ \frac{\partial \mathbf{x}}{\partial \phi} \, d\phi,
$$
we get
$$
d\mathbf{x}
=
\mathbf{e}_r \, dr
+ r \mathbf{e}_\theta \, d\theta
+ r \sin \theta \, \mathbf{e}_\phi \, d\phi.
$$

Taking the squared norm,
$$
ds^2
=
d\mathbf{x} \cdot d\mathbf{x}
=
dr^2 + r^2 d\theta^2 + r^2 \sin^2 \theta \, d\phi^2.
$$

## Time Derivative of Basis Vectors

Suppose the spherical coordinates depend on time:
$$
r = r(t),
\qquad
\theta = \theta(t),
\qquad
\phi = \phi(t).
$$

Then the spherical basis vectors also depend on time through $\theta(t)$ and $\phi(t)$:
$$
\begin{aligned}
\mathbf{e}_r
&=
\bigl(
\sin \theta \cos \phi,\;
\sin \theta \sin \phi,\;
\cos \theta
\bigr), \\
\mathbf{e}_\theta
&=
\bigl(
\cos \theta \cos \phi,\;
\cos \theta \sin \phi,\;
-\sin \theta
\bigr), \\
\mathbf{e}_\phi
&=
\bigl(
-\sin \phi,\;
\cos \phi,\;
0
\bigr).
\end{aligned}
$$

Notice that none of these basis vectors depends on $r$. Therefore
$$
\frac{\partial \mathbf{e}_r}{\partial r}
=
\frac{\partial \mathbf{e}_\theta}{\partial r}
=
\frac{\partial \mathbf{e}_\phi}{\partial r}
=
\mathbf{0}.
$$

So only derivatives with respect to $\theta$ and $\phi$ contribute to the time derivatives.

### Partial Derivatives of the Basis Vectors

First compute the derivatives of $\mathbf{e}_r$.

With respect to $\theta$,
$$
\begin{aligned}
\frac{\partial \mathbf{e}_r}{\partial \theta}
&=
\frac{\partial}{\partial \theta}
\bigl(
\sin \theta \cos \phi,\;
\sin \theta \sin \phi,\;
\cos \theta
\bigr) \\
&=
\bigl(
\cos \theta \cos \phi,\;
\cos \theta \sin \phi,\;
-\sin \theta
\bigr) \\
&= \mathbf{e}_\theta.
\end{aligned}
$$

With respect to $\phi$,
$$
\begin{aligned}
\frac{\partial \mathbf{e}_r}{\partial \phi}
&=
\frac{\partial}{\partial \phi}
\bigl(
\sin \theta \cos \phi,\;
\sin \theta \sin \phi,\;
\cos \theta
\bigr) \\
&=
\bigl(
-\sin \theta \sin \phi,\;
\sin \theta \cos \phi,\;
0
\bigr) \\
&=
\sin \theta
\bigl(
-\sin \phi,\;
\cos \phi,\;
0
\bigr) \\
&= \sin \theta \, \mathbf{e}_\phi.
\end{aligned}
$$

Now compute the derivatives of $\mathbf{e}_\theta$.

With respect to $\theta$,
$$
\begin{aligned}
\frac{\partial \mathbf{e}_\theta}{\partial \theta}
&=
\frac{\partial}{\partial \theta}
\bigl(
\cos \theta \cos \phi,\;
\cos \theta \sin \phi,\;
-\sin \theta
\bigr) \\
&=
\bigl(
-\sin \theta \cos \phi,\;
-\sin \theta \sin \phi,\;
-\cos \theta
\bigr) \\
&=
-\bigl(
\sin \theta \cos \phi,\;
\sin \theta \sin \phi,\;
\cos \theta
\bigr) \\
&= -\mathbf{e}_r.
\end{aligned}
$$

With respect to $\phi$,
$$
\begin{aligned}
\frac{\partial \mathbf{e}_\theta}{\partial \phi}
&=
\frac{\partial}{\partial \phi}
\bigl(
\cos \theta \cos \phi,\;
\cos \theta \sin \phi,\;
-\sin \theta
\bigr) \\
&=
\bigl(
-\cos \theta \sin \phi,\;
\cos \theta \cos \phi,\;
0
\bigr) \\
&=
\cos \theta
\bigl(
-\sin \phi,\;
\cos \phi,\;
0
\bigr) \\
&= \cos \theta \, \mathbf{e}_\phi.
\end{aligned}
$$

Finally compute the derivatives of $\mathbf{e}_\phi$.

With respect to $\theta$,
$$
\begin{aligned}
\frac{\partial \mathbf{e}_\phi}{\partial \theta}
&=
\frac{\partial}{\partial \theta}
\bigl(
-\sin \phi,\;
\cos \phi,\;
0
\bigr) \\
&=
\mathbf{0},
\end{aligned}
$$
since $\mathbf{e}_\phi$ does not depend on $\theta$.

With respect to $\phi$,
$$
\begin{aligned}
\frac{\partial \mathbf{e}_\phi}{\partial \phi}
&=
\frac{\partial}{\partial \phi}
\bigl(
-\sin \phi,\;
\cos \phi,\;
0
\bigr) \\
&=
\bigl(
-\cos \phi,\;
-\sin \phi,\;
0
\bigr).
\end{aligned}
$$

To rewrite this in the spherical basis, express it as a linear combination of $\mathbf{e}_r$ and $\mathbf{e}_\theta$:
$$
\begin{aligned}
-\sin \theta \, \mathbf{e}_r - \cos \theta \, \mathbf{e}_\theta
&=
-\sin \theta
\bigl(
\sin \theta \cos \phi,\;
\sin \theta \sin \phi,\;
\cos \theta
\bigr) \\
&\qquad
- \cos \theta
\bigl(
\cos \theta \cos \phi,\;
\cos \theta \sin \phi,\;
-\sin \theta
\bigr) \\
&=
\bigl(
-(\sin^2 \theta + \cos^2 \theta)\cos \phi,\;
-(\sin^2 \theta + \cos^2 \theta)\sin \phi,\;
0
\bigr) \\
&=
\bigl(
-\cos \phi,\;
-\sin \phi,\;
0
\bigr).
\end{aligned}
$$

Hence
$$
\frac{\partial \mathbf{e}_\phi}{\partial \phi}
=
-\sin \theta \, \mathbf{e}_r
- \cos \theta \, \mathbf{e}_\theta.
$$

Collecting all partial derivatives:
$$
\boxed{
\begin{aligned}
\frac{\partial \mathbf{e}_r}{\partial \theta} &= \mathbf{e}_\theta,
&\qquad
\frac{\partial \mathbf{e}_r}{\partial \phi} &= \sin \theta \, \mathbf{e}_\phi, \\
\frac{\partial \mathbf{e}_\theta}{\partial \theta} &= -\mathbf{e}_r,
&\qquad
\frac{\partial \mathbf{e}_\theta}{\partial \phi} &= \cos \theta \, \mathbf{e}_\phi, \\
\frac{\partial \mathbf{e}_\phi}{\partial \theta} &= \mathbf{0},
&\qquad
\frac{\partial \mathbf{e}_\phi}{\partial \phi} &= -\sin \theta \, \mathbf{e}_r - \cos \theta \, \mathbf{e}_\theta.
\end{aligned}
}
$$

### Time Derivatives

Now apply the chain rule. Since the basis vectors depend only on $\theta$ and $\phi$,
$$
\frac{d\mathbf{e}}{dt}
=
\frac{\partial \mathbf{e}}{\partial \theta}\dot{\theta}
+ \frac{\partial \mathbf{e}}{\partial \phi}\dot{\phi}
$$
for each spherical basis vector $\mathbf{e}$.

For $\mathbf{e}_r$:
$$
\begin{aligned}
\dot{\mathbf{e}}_r
&=
\frac{\partial \mathbf{e}_r}{\partial \theta}\dot{\theta}
+ \frac{\partial \mathbf{e}_r}{\partial \phi}\dot{\phi} \\
&=
\mathbf{e}_\theta \dot{\theta}
+ \sin \theta \, \mathbf{e}_\phi \dot{\phi}.
\end{aligned}
$$

For $\mathbf{e}_\theta$:
$$
\begin{aligned}
\dot{\mathbf{e}}_\theta
&=
\frac{\partial \mathbf{e}_\theta}{\partial \theta}\dot{\theta}
+ \frac{\partial \mathbf{e}_\theta}{\partial \phi}\dot{\phi} \\
&=
-\mathbf{e}_r \dot{\theta}
+ \cos \theta \, \mathbf{e}_\phi \dot{\phi}.
\end{aligned}
$$

For $\mathbf{e}_\phi$:
$$
\begin{aligned}
\dot{\mathbf{e}}_\phi
&=
\frac{\partial \mathbf{e}_\phi}{\partial \theta}\dot{\theta}
+ \frac{\partial \mathbf{e}_\phi}{\partial \phi}\dot{\phi} \\
&=
\mathbf{0} \cdot \dot{\theta}
+ \bigl(
-\sin \theta \, \mathbf{e}_r
- \cos \theta \, \mathbf{e}_\theta
\bigr)\dot{\phi} \\
&=
-\sin \theta \, \dot{\phi} \, \mathbf{e}_r
- \cos \theta \, \dot{\phi} \, \mathbf{e}_\theta.
\end{aligned}
$$

Therefore the time derivatives of the spherical basis vectors are
$$
\boxed{
\begin{aligned}
\dot{\mathbf{e}}_r
&=
\dot{\theta} \, \mathbf{e}_\theta
+ \dot{\phi}\sin \theta \, \mathbf{e}_\phi, \\
\dot{\mathbf{e}}_\theta
&=
-\dot{\theta} \, \mathbf{e}_r
+ \dot{\phi}\cos \theta \, \mathbf{e}_\phi, \\
\dot{\mathbf{e}}_\phi
&=
-\dot{\phi}\sin \theta \, \mathbf{e}_r
- \dot{\phi}\cos \theta \, \mathbf{e}_\theta.
\end{aligned}
}
$$

## Jacobian and Volume Element

From
$$
d\mathbf{x}
=
\frac{\partial \mathbf{x}}{\partial r} \, dr
+ \frac{\partial \mathbf{x}}{\partial \theta} \, d\theta
+ \frac{\partial \mathbf{x}}{\partial \phi} \, d\phi,
$$
the differential relation in Cartesian coordinates is
$$
\begin{pmatrix}
dx \\
dy \\
dz
\end{pmatrix}
=
\begin{pmatrix}
\dfrac{\partial x}{\partial r} & \dfrac{\partial x}{\partial \theta} & \dfrac{\partial x}{\partial \phi} \\
\dfrac{\partial y}{\partial r} & \dfrac{\partial y}{\partial \theta} & \dfrac{\partial y}{\partial \phi} \\
\dfrac{\partial z}{\partial r} & \dfrac{\partial z}{\partial \theta} & \dfrac{\partial z}{\partial \phi}
\end{pmatrix}
\begin{pmatrix}
dr \\
d\theta \\
d\phi
\end{pmatrix}.
$$

So the Jacobian matrix is
$$
J
=
\frac{\partial(x,y,z)}{\partial(r,\theta,\phi)}
=
\begin{pmatrix}
\sin \theta \cos \phi & r \cos \theta \cos \phi & -r \sin \theta \sin \phi \\
\sin \theta \sin \phi & r \cos \theta \sin \phi & r \sin \theta \cos \phi \\
\cos \theta & -r \sin \theta & 0
\end{pmatrix}.
$$

Its determinant is
$$
\begin{aligned}
\det J
&=
r^2
\begin{vmatrix}
\sin \theta \cos \phi & \cos \theta \cos \phi & -\sin \theta \sin \phi \\
\sin \theta \sin \phi & \cos \theta \sin \phi & \sin \theta \cos \phi \\
\cos \theta & -\sin \theta & 0
\end{vmatrix}.
\end{aligned}
$$

Now expand along the third column:
$$
\begin{aligned}
\det J
&=
r^2
\left[
(-\sin \theta \sin \phi)
\begin{vmatrix}
\sin \theta \sin \phi & \cos \theta \sin \phi \\
\cos \theta & -\sin \theta
\end{vmatrix}
+
(\sin \theta \cos \phi)
\left(
-\begin{vmatrix}
\sin \theta \cos \phi & \cos \theta \cos \phi \\
\cos \theta & -\sin \theta
\end{vmatrix}
\right)
\right].
\end{aligned}
$$

Compute the two cofactors:
$$
\begin{aligned}
\begin{vmatrix}
\sin \theta \sin \phi & \cos \theta \sin \phi \\
\cos \theta & -\sin \theta
\end{vmatrix}
&=
-\sin^2 \theta \sin \phi - \cos^2 \theta \sin \phi
= -\sin \phi, \\
-\begin{vmatrix}
\sin \theta \cos \phi & \cos \theta \cos \phi \\
\cos \theta & -\sin \theta
\end{vmatrix}
&=
-\bigl(-\sin^2 \theta \cos \phi - \cos^2 \theta \cos \phi \bigr)
= \cos \phi.
\end{aligned}
$$

Substitute these back:
$$
\begin{aligned}
\det J
&=
r^2
\left[
(-\sin \theta \sin \phi)(-\sin \phi)
+ (\sin \theta \cos \phi)(\cos \phi)
\right] \\
&=
r^2 \sin \theta (\sin^2 \phi + \cos^2 \phi) \\
&= r^2 \sin \theta.
\end{aligned}
$$

Hence the Jacobian is
$$
\boxed{
\frac{\partial(x,y,z)}{\partial(r,\theta,\phi)} = r^2 \sin \theta
}.
$$

Therefore the volume element is
$$
\boxed{
dV = r^2 \sin \theta \, dr \, d\theta \, d\phi
}.
$$

The same result also follows immediately from the scale factors:
$$
dV = h_r h_\theta h_\phi \, dr \, d\theta \, d\phi
= (1)(r)(r \sin \theta) \, dr \, d\theta \, d\phi.
$$

## Inverse Differential Relations

Starting from
$$
d\mathbf{x}
=
\mathbf{e}_r \, dr
+ r \mathbf{e}_\theta \, d\theta
+ r \sin \theta \, \mathbf{e}_\phi \, d\phi,
$$
take dot products with the orthonormal basis vectors.

Because
$$
\mathbf{e}_i \cdot \mathbf{e}_j = \delta_{ij},
$$
we obtain
$$
\begin{aligned}
dr &= \mathbf{e}_r \cdot d\mathbf{x}, \\
r \, d\theta &= \mathbf{e}_\theta \cdot d\mathbf{x}, \\
r \sin \theta \, d\phi &= \mathbf{e}_\phi \cdot d\mathbf{x}.
\end{aligned}
$$

Now substitute
$$
d\mathbf{x} = (dx,dy,dz).
$$

For $dr$:
$$
\begin{aligned}
dr
&=
\mathbf{e}_r \cdot d\mathbf{x} \\
&=
\bigl(
\sin \theta \cos \phi,\;
\sin \theta \sin \phi,\;
\cos \theta
\bigr)
\cdot
(dx,dy,dz) \\
&=
\sin \theta \cos \phi \, dx
+ \sin \theta \sin \phi \, dy
+ \cos \theta \, dz.
\end{aligned}
$$

For $d\theta$:
$$
\begin{aligned}
r \, d\theta
&=
\mathbf{e}_\theta \cdot d\mathbf{x} \\
&=
\bigl(
\cos \theta \cos \phi,\;
\cos \theta \sin \phi,\;
-\sin \theta
\bigr)
\cdot
(dx,dy,dz) \\
&=
\cos \theta \cos \phi \, dx
+ \cos \theta \sin \phi \, dy
- \sin \theta \, dz,
\end{aligned}
$$
so
$$
\boxed{
d\theta
=
\frac{\cos \theta \cos \phi}{r} \, dx
+ \frac{\cos \theta \sin \phi}{r} \, dy
- \frac{\sin \theta}{r} \, dz
}.
$$

For $d\phi$:
$$
\begin{aligned}
r \sin \theta \, d\phi
&=
\mathbf{e}_\phi \cdot d\mathbf{x} \\
&=
\bigl(
-\sin \phi,\;
\cos \phi,\;
0
\bigr)
\cdot
(dx,dy,dz) \\
&=
-\sin \phi \, dx + \cos \phi \, dy,
\end{aligned}
$$
so
$$
\boxed{
d\phi
=
-\frac{\sin \phi}{r \sin \theta} \, dx
+ \frac{\cos \phi}{r \sin \theta} \, dy
}.
$$

Collecting the three formulas,
$$
\boxed{
\begin{aligned}
dr
&=
\sin \theta \cos \phi \, dx
+ \sin \theta \sin \phi \, dy
+ \cos \theta \, dz, \\
d\theta
&=
\frac{\cos \theta \cos \phi}{r} \, dx
+ \frac{\cos \theta \sin \phi}{r} \, dy
- \frac{\sin \theta}{r} \, dz, \\
d\phi
&=
-\frac{\sin \phi}{r \sin \theta} \, dx
+ \frac{\cos \phi}{r \sin \theta} \, dy.
\end{aligned}
}
$$

## Gradient, Divergence, and Curl

For any orthogonal coordinate system $(q_1,q_2,q_3)$ with scale factors $(h_1,h_2,h_3)$,
$$
\nabla f
=
\sum_{i=1}^3 \mathbf{e}_i \frac{1}{h_i} \frac{\partial f}{\partial q_i},
$$
$$
\nabla \cdot \mathbf{A}
=
\frac{1}{h_1 h_2 h_3}
\sum_{i=1}^3
\frac{\partial}{\partial q_i}
\left(
\frac{h_1 h_2 h_3}{h_i} A_i
\right),
$$
and
$$
\nabla \times \mathbf{A}
=
\frac{1}{h_1 h_2 h_3}
\begin{vmatrix}
h_1 \mathbf{e}_1 & h_2 \mathbf{e}_2 & h_3 \mathbf{e}_3 \\
\dfrac{\partial}{\partial q_1} & \dfrac{\partial}{\partial q_2} & \dfrac{\partial}{\partial q_3} \\
h_1 A_1 & h_2 A_2 & h_3 A_3
\end{vmatrix}.
$$

In spherical coordinates,
$$
(q_1,q_2,q_3) = (r,\theta,\phi),
\qquad
(h_1,h_2,h_3) = (1,r,r \sin \theta).
$$

Write the vector field as
$$
\mathbf{A} = A_r \mathbf{e}_r + A_\theta \mathbf{e}_\theta + A_\phi \mathbf{e}_\phi.
$$

### Gradient

Substitute the scale factors into the general formula:
$$
\begin{aligned}
\nabla f
&=
\mathbf{e}_r \frac{1}{h_r} \frac{\partial f}{\partial r}
+ \mathbf{e}_\theta \frac{1}{h_\theta} \frac{\partial f}{\partial \theta}
+ \mathbf{e}_\phi \frac{1}{h_\phi} \frac{\partial f}{\partial \phi} \\
&=
\mathbf{e}_r \frac{\partial f}{\partial r}
+ \mathbf{e}_\theta \frac{1}{r} \frac{\partial f}{\partial \theta}
+ \mathbf{e}_\phi \frac{1}{r \sin \theta} \frac{\partial f}{\partial \phi}.
\end{aligned}
$$

Therefore
$$
\boxed{
\nabla f
=
\mathbf{e}_r \frac{\partial f}{\partial r}
+ \mathbf{e}_\theta \frac{1}{r} \frac{\partial f}{\partial \theta}
+ \mathbf{e}_\phi \frac{1}{r \sin \theta} \frac{\partial f}{\partial \phi}
}.
$$

### Divergence

Start from the orthogonal-coordinate formula:
$$
\nabla \cdot \mathbf{A}
=
\frac{1}{h_r h_\theta h_\phi}
\left[
\frac{\partial}{\partial r}
\left(
\frac{h_r h_\theta h_\phi}{h_r} A_r
\right)
+
\frac{\partial}{\partial \theta}
\left(
\frac{h_r h_\theta h_\phi}{h_\theta} A_\theta
\right)
+
\frac{\partial}{\partial \phi}
\left(
\frac{h_r h_\theta h_\phi}{h_\phi} A_\phi
\right)
\right].
$$

Now use
$$
h_r h_\theta h_\phi = (1)(r)(r \sin \theta) = r^2 \sin \theta.
$$

Then
$$
\begin{aligned}
\nabla \cdot \mathbf{A}
&=
\frac{1}{r^2 \sin \theta}
\left[
\frac{\partial}{\partial r}(r^2 \sin \theta \, A_r)
+ \frac{\partial}{\partial \theta}(r \sin \theta \, A_\theta)
+ \frac{\partial}{\partial \phi}(r A_\phi)
\right].
\end{aligned}
$$

Because $\sin \theta$ does not depend on $r$, and $r$ does not depend on $\theta$ or $\phi$, this simplifies to
$$
\boxed{
\nabla \cdot \mathbf{A}
=
\frac{1}{r^2} \frac{\partial}{\partial r}(r^2 A_r)
+ \frac{1}{r \sin \theta} \frac{\partial}{\partial \theta}(\sin \theta \, A_\theta)
+ \frac{1}{r \sin \theta} \frac{\partial A_\phi}{\partial \phi}
}.
$$

### Curl

Substitute $(h_r,h_\theta,h_\phi) = (1,r,r \sin \theta)$ into the determinant formula:
$$
\nabla \times \mathbf{A}
=
\frac{1}{r^2 \sin \theta}
\begin{vmatrix}
\mathbf{e}_r & r \mathbf{e}_\theta & r \sin \theta \, \mathbf{e}_\phi \\
\dfrac{\partial}{\partial r} & \dfrac{\partial}{\partial \theta} & \dfrac{\partial}{\partial \phi} \\
A_r & r A_\theta & r \sin \theta \, A_\phi
\end{vmatrix}.
$$

Expanding the determinant along the first row gives the $\mathbf{e}_r$ component:
$$
\begin{aligned}
(\nabla \times \mathbf{A})_r
&=
\frac{1}{r^2 \sin \theta}
\begin{vmatrix}
\dfrac{\partial}{\partial \theta} & \dfrac{\partial}{\partial \phi} \\
r A_\theta & r \sin \theta \, A_\phi
\end{vmatrix} \\
&=
\frac{1}{r^2 \sin \theta}
\left[
\frac{\partial}{\partial \theta}(r \sin \theta \, A_\phi)
- \frac{\partial}{\partial \phi}(r A_\theta)
\right] \\
&=
\frac{1}{r \sin \theta}
\left[
\frac{\partial}{\partial \theta}(\sin \theta \, A_\phi)
- \frac{\partial A_\theta}{\partial \phi}
\right].
\end{aligned}
$$

For the $\mathbf{e}_\theta$ component:
$$
\begin{aligned}
(\nabla \times \mathbf{A})_\theta
&=
-\frac{1}{r^2 \sin \theta}
\begin{vmatrix}
\dfrac{\partial}{\partial r} & \dfrac{\partial}{\partial \phi} \\
A_r & r \sin \theta \, A_\phi
\end{vmatrix} \\
&=
-\frac{1}{r^2 \sin \theta}
\left[
\frac{\partial}{\partial r}(r \sin \theta \, A_\phi)
- \frac{\partial A_r}{\partial \phi}
\right] \\
&=
\frac{1}{r}
\left[
\frac{1}{\sin \theta} \frac{\partial A_r}{\partial \phi}
- \frac{\partial}{\partial r}(r A_\phi)
\right].
\end{aligned}
$$

For the $\mathbf{e}_\phi$ component:
$$
\begin{aligned}
(\nabla \times \mathbf{A})_\phi
&= 
\frac{1}{r^2 \sin \theta}
\cdot (r \sin \theta)
\begin{vmatrix}
\dfrac{\partial}{\partial r} & \dfrac{\partial}{\partial \theta} \\
A_r & r A_\theta
\end{vmatrix} \\
&= 
\frac{1}{r^2 \sin \theta}
\cdot (r \sin \theta)
\left[
\frac{\partial}{\partial r}(r A_\theta)
- \frac{\partial A_r}{\partial \theta}
\right] \\
&=
\frac{1}{r}
\left[
\frac{\partial}{\partial r}(r A_\theta)
- \frac{\partial A_r}{\partial \theta}
\right].
\end{aligned}
$$

Therefore
$$
\boxed{
\begin{aligned}
\nabla \times \mathbf{A}
= {} &
\mathbf{e}_r
\frac{1}{r \sin \theta}
\left[
\frac{\partial}{\partial \theta}(\sin \theta \, A_\phi)
- \frac{\partial A_\theta}{\partial \phi}
\right] \\
&+
\mathbf{e}_\theta
\frac{1}{r}
\left[
\frac{1}{\sin \theta} \frac{\partial A_r}{\partial \phi}
- \frac{\partial}{\partial r}(r A_\phi)
\right] \\
&+
\mathbf{e}_\phi
\frac{1}{r}
\left[
\frac{\partial}{\partial r}(r A_\theta)
- \frac{\partial A_r}{\partial \theta}
\right].
\end{aligned}
}
$$

Equivalently, the components are
$$
\boxed{
\begin{aligned}
(\nabla \times \mathbf{A})_r
&=
\frac{1}{r \sin \theta}
\left[
\frac{\partial}{\partial \theta}(\sin \theta \, A_\phi)
- \frac{\partial A_\theta}{\partial \phi}
\right], \\
(\nabla \times \mathbf{A})_\theta
&=
\frac{1}{r}
\left[
\frac{1}{\sin \theta} \frac{\partial A_r}{\partial \phi}
- \frac{\partial}{\partial r}(r A_\phi)
\right], \\
(\nabla \times \mathbf{A})_\phi
&=
\frac{1}{r}
\left[
\frac{\partial}{\partial r}(r A_\theta)
- \frac{\partial A_r}{\partial \theta}
\right].
\end{aligned}
}
$$

These formulas are valid away from the coordinate singularities $r = 0$ and $\sin \theta = 0$.
