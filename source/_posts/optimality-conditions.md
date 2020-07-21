---
title: Optimality Conditions
date: 2019-11-15 00:57:40
tags:
categories: Optimization
mathjax: true
---

$\mathbb{R}^n$ 中常用优化问题最优性条件，内容来自 <u>Nonlinear Optimization</u> [Andrzej Ruszczynski]。

<!--more-->

## Unconstrained Minimum of Differentiable Functions

Assume that $f : \mathbb{R}^n \rightarrow {\mathbb{R}}$ is differentiable at a point $\hat{x}$.

+ If $f(·)$ attains its unconstrained local minimum at $\hat{x}$, then
  $$
  \nabla f(\hat{x})=0
  $$

+ If $f(·)$ is convex and $\nabla f(\hat{x})=0$, then $\hat{x}$ is an unconstrained global minimum of $f(·)$.

## Unconstrained Minimum of Convex Functions

Let $f : \mathbb{R}^n \rightarrow \overline{\mathbb{R}}$ be a proper convex function. A point $\hat{x}$ is a global minimum of $f(·)$ if and only if
$$
0 \in \partial f(\hat{x})
$$
**Tangent**

A direction $d$ is called **tangent** to the set $X \subset \mathbb{R}^n$ at the point $x \in X$ if there exist sequences of points $x_k \in X$ and scalars $\tau_k > 0$, $k = 1, 2, \cdots$, such that $\tau_k \downarrow 0$ and
$$
d=\lim _{k \rightarrow \infty} \frac{x^{k}-x}{\tau_{k}}
$$
Let $X \subset \mathbb{R}^n$ and let $x \in X$. The set $T_X(x)$ of all tangent directions for $X$ at $x$ is a closed cone.

Let $X \subset \mathbb{R}^n$ be a convex set and let $x \in X$. Then
$$
T_X(x) = \overline{K_X(x)}
$$

##  Optimal Conditions for Smooth Problems

Consider the constrained optimization problem
$$
\begin{alignat*}{2}
\min \quad & f(x)  \\ 
\mbox{s.t.} \quad 
& x \in X
\end{alignat*}
$$
with a differentiable function $f : \mathbb{R}^n \rightarrow \mathbb{R}$ and a set $X \subset \mathbb{R}^n$.

Assume that $\hat{x}$ is a local minimum of the problem and that $f(·)$ is differentiable at $\hat{x}$. Let $T_X(\hat{x})$ be the tangent cone to the set $X$ at $\hat{x}$. Then
$$
-\nabla f(\hat{x}) \in \left[T_X(\hat{x}) \right]^\circ
$$
Conversely, if the function $f(·)$ is convex, the set $X$ is convex, and a point $\hat{x} \in X$ satisfies relation $-\nabla f(\hat{x}) \in \left[T_X(\hat{x}) \right]^\circ$, then $\hat{x}$ is a global minimum of problem.

## Optimal Conditions for Convex Problems

Consider the constrained optimization problem
$$
\begin{alignat*}{2}\min \quad & f(x)  \\ \mbox{s.t.} \quad & x \in X\end{alignat*}
$$
with a convex function $f : \mathbb{R}^n \rightarrow \overline{\mathbb{R}}$ and a convex set $X \subset \mathbb{R}^n$.

Assume that $\hat{x}$ is a local minimum of the problem and that there exists a point $x_0 \in X$ such that $f$ is continuous at $x_0$. Then there exists $s \in \partial f(\hat{x})$ such that
$$
-s \in N_X(\hat{x})
$$
Conversely, if a point $\hat{x} \in X$ satisfies the relation $-s \in N_X(\hat{x})$ for some $s \in \partial f(\hat{x})$, then $\hat{x}$ is a global minimum of problem.
