---
title: Low Rank Matrix Recovery - Preliminary
date: 2019-11-09 12:57:38
tags:  
  - Nuclear Norm
  - Low Rank Matrix Recovery
categories: Optimization
mathjax: true
---

矩阵秩最小化问题在某些情况下可以通过核范数最小化来解决，参阅文章 <u>Guaranteed Minimum-Rank Solutions of Linear Matrix Equations via Nuclear Norm Minimization</u> [B Recht, M Fazel, PA Parrilo]，此篇介绍文章涉及的一些有关核范数的基本知识，内容主要来自文章的第二部分。

<!--more-->

需要求解的优化问题为**秩最小化问题** (rank minimization problem)：
$$
\begin{alignat*}{2}
\min \quad & rank(X)  \\ 
\mbox{s.t.} \quad 
& X \in \mathcal{C}
\end{alignat*}
$$
其中 $X \in \mathbb{R}^{m \times n}$ 为决策变量，$\mathcal{C} \subset \mathbb{R}^{m \times n}$ 为给定凸集。

文章重点关注的是上述问题的特殊情形**仿射秩最小化问题** (affine rank minimization problem)：
$$
\begin{alignat*}{2}
\min \quad & rank(X)  \\ 
\mbox{s.t.} \quad 
& \mathcal{A}(X) = b
\end{alignat*}
$$
其中 $\mathcal{A}: \mathbb{R}^{m \times n} \rightarrow \mathbb{R}^{p}$ 为给定线性映射，$b \in \mathbb{R}^{p}$ 已知。

## Matrix Norms

Given $X \in \mathbb{R}^{m \times n}$, let $\sigma_i(X)$ denotes the $i$-th largest singular value of $X$, $i = 1, 2, \cdots, r.$

+ **Frobenius norm** (or Hilbert–Schmidt norm): the $l_2$-norm of the vector of singular values
  $$
  \|X\|_{F}:=\sqrt{\langle X, X\rangle}=\sqrt{\operatorname{Tr}\left(X^{\prime} X\right)}=\left(\sum_{i=1}^{m} \sum_{j=1}^{n} X_{i j}^{2}\right)^{\frac{1}{2}}=\left(\sum_{i=1}^{r} \sigma_{i}^{2}\right)^{\frac{1}{2}}
  $$

+ **Operator norm** (or induced 2-norm): the $l_\infty$-norm of the vector of singular values
  $$
  \|X\|:=\sigma_1(X)
  $$

+ **Nuclear norm** (or the Schatten $1$-norm, the Ky Fan $r$-norm, the trace class norm): the $l_1$-norm of the vector of singular values
  $$
  \|X\|_*:=\sum_{i=1}^r \sigma_i(X)
  $$

Relation of these norms:
$$
\|X\| \leq\|X\|_{F} \leq\|X\|_{*} \leq \sqrt{r}\|X\|_{F} \leq r\|X\|
$$

## Dual Norms

For any given norm $\left\lVert \cdot \right\rVert$ of the inner product space $\mathbb{R}^{m \times n}$, there exists a **dual norm** $\left\lVert \cdot \right\rVert_d$ defined as
$$
\|X\|_{d}:=\sup \left\{\langle X, Y\rangle : Y \in \mathbb{R}^{m \times n},\|Y\| \leq 1\right\}
$$
The norm dual to the norm $\left\lVert \cdot \right\rVert_d$ is again the original norm $\left\lVert \cdot \right\rVert$ (**待验证**)
$$
\|X\|=\sup \left\{\langle X, Y\rangle : Y \in \mathbb{R}^{m \times n},\|Y\|_d \leq 1\right\}
$$

### Theorem: dual norm of the Frobenius norm

The dual norm of the Frobenius norm is the Frobenius norm.

> **证明**：容易通过 Cauchy–Schwarz 不等式验证。

### Theorem: dual norm of the nuclear norm

The dual norm of the operator norm $\left\lVert \cdot \right\rVert$ in $\mathbb{R}^{m \times n}$ is the nuclear norm $\left\lVert \cdot \right\rVert_*$.

> **证明**：对于任意 $Z \in \mathbb{R}^{m \times n}$，
> $$
> \|Z\| \leq t \quad \Longleftrightarrow \quad t^{2} I_{m}-Z Z^{\prime} \succeq 0 \quad \Longleftrightarrow \quad\left[\begin{array}{cc}{t I_{m}} & {Z} \\ {Z^{\prime}} & {t I_{n}}\end{array}\right] \succeq 0
> $$
>
> + 第一个等价关系是由于 $\sigma_i(Z)$ 就是 $ZZ'$ 第 $i$ 大的特征值
> + 第二个等价关系就是  Schur complement 的性质，也可以通过对二次型求梯度，从而说明二次型的非负性来验证
>
> 假设 $X \in \mathbb{R}^{m \times n}$ 的 SVD 分解为 $X = U\Sigma V'$，其中 $U \in \mathbb{R}^{m \times r}, V \in \mathbb{R}^{n \times r}$ 且各自的列向量都是标准正交的，$\Sigma$ 为 $r$ 阶对角矩阵，这里 $r = rank(X)$。
>
> 首先取 $Y = UV'$，于是 $\left\lVert Y \right\rVert = 1$ 并且 $\langle X, Y\rangle = \operatorname{Tr}(\Sigma) = \sum_{i=1}^r{\sigma_i(X)} = \left\lVert X \right\rVert_{*}$，从而
> $$
> \|X\|_{*} \leq \sup \left\{\langle X, Y\rangle : Y \in \mathbb{R}^{m \times n},\|Y\| \leq 1\right\}
> $$
> 另一方面，$\left\lVert \cdot \right\rVert$ 的对偶范数的求解可以看作优化问题：
> $$
> \begin{alignat*}{2}
> \min \quad & \operatorname{Tr}(X'Y)  \\ 
> \mbox{s.t.} \quad 
> & \|Y\| \leq 1 \quad  \Longleftrightarrow \quad\left[\begin{array}{cc}{I_{m}} & {Y} \\ {Y'} & {I_{n}}\end{array}\right] \succeq 0
> \end{alignat*}
> $$
> 这是一个 [SDP 问题](https://tsechinlin.github.io/2019/11/08/conic-linear-programming)，令
> $$
> Z = \left[\begin{array}{cc}{I_{m}} & {Y} \\ {Y'} & {I_{n}}\end{array}\right], \quad 
> C = \left[\begin{array}{cc}{0} & {X/2} \\ {X'/2} & {0}\end{array}\right] \quad 
> A^{(ij)} = [a^{(ij)}_{kl}] \in \mathbb{R}^{(m+n) \times (m+n)}
> $$
> 其中
> $$
> a^{(ij)}_{kl} = 
> \begin{cases}
> 1, &\text{if} \quad k = i, l = j \quad \text{or} \quad k = j, l = i \\
> 0, &\text{otherwise}
> \end{cases}
> $$
> 原问题因此可以写成 SDP 的标准形式：
> $$
> \begin{alignat*}{2}
> \min \quad & \langle \mathbf{C},\mathbf{Z} \rangle  \\ 
> \mbox{s.t.} \quad 
> & \langle \mathbf{A}^{(ii)},\mathbf{Z} \rangle=1, \quad 1 \leq i \leq m+n, \\
> & \langle \mathbf{A}^{(ij)},\mathbf{Z} \rangle=0, \quad 1 \leq i < j \leq m \quad \text{or} \quad m+1 \leq i < j \leq m+n, \\
> & \mathbf{Z} \succeq \mathbf{0}
> \end{alignat*}
> $$
> 其对偶问题为 ($W_1 \in \mathbb{R}^{m \times m}, W_2 \in \mathbb{R}^{n \times n}$ 为自变量)
> $$
> \begin{alignat*}{2}
> \min \quad & \frac{1}{2} \left(\operatorname{Tr}\left(W_{1}\right)+\operatorname{Tr}\left(W_{2}\right)\right) \\ 
> \mbox{s.t.} \quad 
> & \left[\begin{array}{cc}{W_{1}} & {X} \\ {X^{\prime}} & {W_{2}}\end{array}\right] \succeq 0
> \end{alignat*}
> $$
> 原问题与对偶问题可行性满足时，弱对偶性总是成立的：
> $$
> \frac{1}{2} \left(\operatorname{Tr}\left(W_{1}\right)+\operatorname{Tr}\left(W_{2}\right)\right) \geq \operatorname{Tr}(X'Y)
> $$
> 特别的，取 $W_1 = U\Sigma U', W_2 = V\Sigma V'$，那么其显然为可行解，并且 
> $$
> \frac{1}{2} \left(\operatorname{Tr}\left(W_{1}\right)+\operatorname{Tr}\left(W_{2}\right)\right) = \operatorname{Tr}\left(\Sigma\right) =\left\lVert X \right\rVert_{*}
> $$
> 于是根据弱对偶性，
> $$
> \|X\|_{*} \geq \sup \left\{\langle X, Y\rangle : Y \in \mathbb{R}^{m \times n},\|Y\| \leq 1\right\}
> $$

## Convex Envelopes of Rank and Cardinality Functions

Let $\mathcal{C}$ be a given convex set. The **convex envelope** of a (possibly nonconvex) function $f : \mathcal{C}→ \mathbb{R}$ is defined as the largest convex function $g$ such that $g(x) \leq f(x)$ for all $x \in \mathcal{C}$.

### Theorem: convex envelope of the rank function

The convex envelope of $rank(X)$ on the set $\{X \in \mathbb{R}^{m \times n} : \left\lVert X \right\rVert \leq 1 \}$ is the nuclear norm $\left\lVert X \right\rVert_*$.

> **证明**：待验证，参见 <u>Matrix Rank Minimization with Applications</u> [M. Fazel].

Let $X_0 =  \mathop{\arg\min}\limits_{\mathcal{A}(X)=b} rank(X)$ and $M = \left\lVert X_0 \right\rVert$, then 

$$
X_* =  \mathop{\arg\min}\limits_{\mathcal{A}(X)=b} \|X\|_*
$$

can be used to provided an upper and lower bound on the optimal rank.

$$
rank(X_*) \geq rank(X_0) = rank(\frac{X_0}{M}) \geq \frac{\|X_0\|_*}{M} \geq \frac{\|X_*\|_*}{M}
$$

## Additivity of Rank and Nuclear Norm

## Nuclear Norm Minimization

## Optimality Conditions 

