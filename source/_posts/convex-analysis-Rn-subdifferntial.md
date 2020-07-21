---
title: Convex Analysis in $\mathbb{R}^n$ - Subdifferential
date: 2019-11-15 00:56:59
tags:
  - Convex
  - Kone
categories: Optimization
mathjax: true
---

$\mathbb{R}^n$ 中常用的凸分析定义与结论整理，内容来自 <u>Nonlinear Optimization</u> [Andrzej Ruszczynski]。

<!--more-->

## Subgradient & Subdifferential

**Definition**

Let $f : \mathbb{R}^n \rightarrow \overline{\mathbb{R}}$ be a proper convex function and $x \in \operatorname{dom} f$. A vector $g \in \mathbb{R}^n$ is called a **subgradient** of $f$ at $x$ if
$$
f(y) \geq f(x) + \langle g, y-x \rangle, \quad \forall y \in \mathbb{R}^n
$$
The set of all subgradients of $f$ at $x$ is called the **subdifferential** of $f$ at $x$ and is denoted by $\partial f(x)$.

**Geometrical Interpretation**

Let $f : \mathbb{R}^n \rightarrow \overline{\mathbb{R}}$ be a proper convex function and $x \in \operatorname{dom} f$. If $g \in \partial f(x)$, then $(g, -1)$ is an element of the normal cone $N_{\operatorname{epi} f}(x, f(x))$,
$$
\langle g, y-x \rangle + (-1) (v - f(x)) \leq 0, \quad \forall (y, v) \in \operatorname{epi} f
$$
Conversely, if a vector $(u, \gamma) \in N_{\operatorname{epi} f}(x, f(x))$ and $\gamma < 0$, then $g = −u/\gamma$ is a subgradient of $f$ at $x$.

## Subdifferential Calculus

**Scalar Multiplication**

Assume that $f : \mathbb{R}^n \rightarrow \overline{\mathbb{R}}$ is a convex function, $\alpha > 0$, and $h(x) = \alpha f(x)$. Then $h$ is convex, and 
$$
\partial h(x) = \alpha \partial f(x), \quad \forall x \in \operatorname{dom} f
$$
**Addition (Moreau–Rockafellar Theorem)**

Assume that $f = f_1 + f_2$, where $f_1 : \mathbb{R}^n \rightarrow \overline{\mathbb{R}}$ and $f_1 : \mathbb{R}^n \rightarrow \overline{\mathbb{R}}$ are proper convex functions. If there exists a point $x_0 \in \operatorname{dom} f$ such that $f_1$ is continuous at $x_0$, then
$$
\partial f(x) = \partial f_1(x) + \partial f_2(x), \quad \forall x \in \operatorname{dom} f
$$
**Linear Transformation**

Assume that $f : \mathbb{R}^m \rightarrow \overline{\mathbb{R}}$ is a convex function, and $A: \mathbb{R}^{m} \rightarrow \mathbb{R}^n$ is a linear operator. Let $h(x) = f(Ax)$, then 
$$
\partial h(x) = A^* \partial f(Ax), \quad \forall x \in \operatorname{dom} h
$$

