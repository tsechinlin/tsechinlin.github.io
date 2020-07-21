---
title: 微分流形笔记 - 微分形式 Differential Forms
date: 2020-01-11 00:31:18
tags: 
  - Smooth Manifolds
categories: Manifolds
mathjax: true
---

[GTM-218] John M. Lee - Introduction to Smooth Manifolds 第十四章笔记。

<!--more-->

## 外代数 The Algebra of Alternating Tensors

### 反称张量的定义与基本性质 Covariant Tensors

**反称张量的定义**

Assume $V$ is a finite-dimensional real vector space. A covariant $k$-tensor $\alpha$ on $V$ is said to be **alternating (or antisymmetric or skew-symmetric)** if it changes sign whenever two of its arguments are interchanged:

For all vectors $v_1, \cdots, v_k \in V$ and every pair of distinct indices $1 \leq i < j \leq k$ it satisfies
$$
\alpha\left(v_{1}, \dots, v_{i}, \dots, v_{j}, \dots, v_{k}\right)=-\alpha\left(v_{1}, \dots, v_{j}, \dots, v_{i}, \dots, v_{k}\right)
$$
**Alternating covariant $k$-tensors** are also variously called **exterior forms, multi-covectors, or $k$-covectors**.

**$0$ 阶张量，$1$ 阶张量为反称张量**

Every $0$-tensor (which is just a real number), $1$-tensor (covector) is alternating.

**$k$ 阶反称张量全体构成子空间**

The subspace of all alternating covariant $k$-tensors on $V$ is denoted by $\Lambda^k(V^\*) \subset T^k(V^\*)$.

**反称张量与指标变换**

The following are equivalent for a covariant $k$-tensor $\alpha$ on a finite-dimensional vector space $V$:

+ $\alpha$ is alternating.

+ For any vectors $v_1, \cdots, v_k \in V$ and any permutation $\sigma \in S_k$,
  $$
  \alpha\left(v_{\sigma(1)}, \ldots, v_{\sigma(k)}\right)=(\operatorname{sgn} \sigma) \alpha\left(v_{1}, \ldots, v_{k}\right)
  $$

+ With respect to any basis, the components $\alpha_{i_1 \cdots i_k}$ of $\alpha$ change sign whenever two indices are interchanged.

**反称张量与线性相关**

The following are equivalent for a covariant $k$-tensor $\alpha$ on a finite-dimensional vector space $V$:

+ $\alpha$ is alternating.

+ $\alpha\left(v_{1}, \ldots, v_{k}\right) = 0$ whenever the $k$-tuple $\left(v_{1}, \ldots, v_{k}\right)$ is linearly dependent.

+ $\alpha$ gives the value zero whenever two of its arguments are equal:
  $$
  \alpha\left(v_{1}, \ldots, w, \ldots, w, \ldots, v_{k}\right)=0
  $$

### 反称化算子 Alternation

**反称化算子的定义**

Assume $V$ is a finite-dimensional real vector space, define a projection $\operatorname { Alt } :T^{k}\left(V^{\*}\right) \rightarrow \Lambda^{k}\left(V^{\*}\right)$, called **alternation**, as follows:
$$
\operatorname { Alt } \alpha=\frac{1}{k !} \sum_{\sigma \in S_{k}}(\operatorname{sgn} \sigma)\left(^{\sigma} \alpha\right)
$$
This means for any vectors $v_1, \cdots, v_k \in V$,
$$
(\operatorname { Alt } \alpha)\left(v_{1}, \ldots, v_{k}\right)=\frac{1}{k !} \sum_{\sigma \in S_{k}}(\operatorname{sgn} \sigma) \alpha\left(v_{\sigma(1)}, \ldots, v_{\sigma(k)}\right)
$$
**反称化算子的性质**

Let $\alpha$ be a covariant tensor on a finite-dimensional vector space.

+ $\operatorname { Alt } \alpha$ is alternating.
+ $\operatorname { Alt } \alpha = \alpha$ if and only if $\alpha$ is alternating.

### 基本反称张量 Elementary Alternating Tensors

**多重指标**

Given a positive integer $k$, an ordered $k$-tuple $I = (i_1, \cdots, i_k)$ of positive integers is called a **multi-index** of length $k$.

If $I$ is a multi-index of length $k$ and $\sigma \in S_k$, define
$$
I_\sigma = (i_{\sigma(1)}, \cdots, i_{\sigma(k)})
$$
Note that $I_{\sigma \tau}=\left(I_{\sigma}\right)_{\tau}$ for $\sigma, \tau \in S_{k}$.

A multi-index $I = (i_1, \cdots, i_k)$ is said to be **increasing** if $i_1 < \cdots < i_k$. It is useful to use a primed summation sign to denote a sum over only increasing multi-indices,
$$
\sum_{I}' \alpha_{I} \varepsilon^{I}=\sum_{\left\{I: i_{1}<\cdots<i_{k}\right\}} \alpha_{I} \varepsilon^{I}
$$
**多重指标与 $\delta$ 行列式**

If $I$ and $J$ are multi-indices of length $k$, define
$$
\begin{equation*}\delta_{J}^{I}=\operatorname{det}\left(\begin{array}{ccc}{\delta_{j_{1}}^{i_{1}}} & {\cdots} & {\delta_{j_{k}}^{i_{1}}} \\{\vdots} & {\ddots} & {\vdots} \\{\delta_{j_{1}}^{i_{k}}} & {\cdots} & {\delta_{j_{k}}^{i_{k}}}\end{array}\right)\end{equation*}
$$
Notice that
$$
\begin{equation}\delta_{J}^{I}=\left\{\begin{array}{ll}{\operatorname{sgn} \sigma} & {\text { if neither } I \text { nor } J \text { has a repeated index and } J=I_{\sigma} \text { for some } \sigma \in S_{k}} \\{0} & {\text { if } I \text { or } J \text { has a repeated index or } J \text { is not a permutation of } I}\end{array}\right.\end{equation}
$$
**基本反称张量的定义**

Let $V$ be an $n$-dimensional vector space, and suppose $\left(\varepsilon^1, \cdots, \varepsilon^n \right)$ is any basis for $V^*$. For each multi-index $I = (i_1, \cdots, i_k)$ such that $1 \leq i_1, \cdots, i_k \leq n$, define a covariant $k$-tensor $\varepsilon^I = \varepsilon^{i_1 \cdots i_k}$ by 
$$
\varepsilon^{I}\left(v_{1}, \ldots, v_{k}\right)= \operatorname{det}\left(\begin{array}{ccc}{\varepsilon^{i_{1}}\left(v_{1}\right)} & \cdots & \varepsilon^{i_{1}}\left(v_{k}\right) \\{\vdots} & {\ddots} & {\vdots} \\{\varepsilon^{i_{k}}\left(v_{1}\right)} & \cdots & \varepsilon^{i_{k}}\left(v_{k}\right)\end{array}\right)=\operatorname{det}\left(\begin{array}{ccc}{v_{1}^{i_{1}}} & {\cdots} & {v_{k}^{i_{1}}} \\{\vdots} & {\ddots} & {\vdots} \\{v_{1}^{i_{k}}} & {\cdots} & {v_{k}^{i_{k}}}\end{array}\right)
$$
Because the determinant changes sign whenever two columns are interchanged, $\varepsilon^I$ is indeed an alternating $k$-tensor, called an **elementary alternating tensor** or elementary $k$-covector.

**基本反称张量的性质**

Let $(E_i)$ be a basis for $V$, let $(\varepsilon^i)$ be the dual basis for $V$, and let $\varepsilon^I$ be the elementary alternating tensor defined above.

+ If $I$ has a repeated index, then $\varepsilon^I = 0$.

+ If $J  = I_\sigma$ for some $\sigma \in S_k$, then $\varepsilon^I = (\operatorname{sgn} \sigma)\varepsilon^J$.

+ The result of evaluating $\varepsilon^I$ on a sequence of basis vectors is
  $$
  \varepsilon^{I}\left(E_{j_{1}}, \ldots, E_{j_{k}}\right)=\delta_{J}^{I}
  $$

**非零的 $k$ 阶基本反称张量构成 $k$ 阶反称张量全体的一组基**

Let $V$ be an $n$-dimensional vector space. If $(\varepsilon^i)$ is any basis for $V^*$, then for each positive integer $k \leq n$, the collection of $k$-covectors
$$
\mathcal{E}=\left\{\varepsilon^{I}: I = (i_1, \cdots, i_k) \text{ such that } 1 \leq i_1 < \cdots < i_k \leq n \right\}
$$
is a basis for $\Lambda^k(V^*)$. Therefore,
$$
\operatorname{dim} \Lambda^{k}\left(V^{*}\right)=\left(\begin{array}{l}{n} \\{k}\end{array}\right)=\frac{n !}{k !(n-k) !}
$$
If $k> n$, then $\operatorname{dim} \Lambda^{k}\left(V^{*}\right) = 0$.

**$n$ 阶反称张量与线性变换**

If $T: V \rightarrow V$ is a linear map, the **determinant** of $T$ is defined to be the determinant of the matrix representation of $T$ with respect to any basis.

Suppose $V$ is an $n$-dimensional vector space and $\omega \in \Lambda^{n}\left(V^{*}\right)$. If $T: V \rightarrow V$ is any linear map and $v_1, \cdots, v_n$ are arbitrary vectors in $V$, then
$$
\omega\left(T v_{1}, \ldots, T v_{n}\right)=(\operatorname{det} T) \omega\left(v_{1}, \ldots, v_{n}\right)
$$

### 外积运算 The Wedge Product

**外积运算的定义**

Assume $V$ is a finite-dimensional real vector space. Given $\omega \in \Lambda^{k}\left(V^{\*}\right) $and $\eta \in \Lambda^{l}\left(V^{\*}\right)$, define their **wedge product** or exterior product to be the following $(k + l)$-covector:
$$
\omega \wedge \eta=\frac{(k+l) !}{k ! l !} \operatorname{Alt}(\omega \otimes \eta)
$$
**基本反称张量的外积**

Let $V$ be an $n$-dimensional vector space and let$\left(\varepsilon^1, \cdots, \varepsilon^n \right)$ be a basis for $V^*$. For any multi-indices $I = (i_1, \cdots, i_k)$ and $J = (j_1, \cdots, j_l)$,
$$
\varepsilon^I \wedge\varepsilon^J = \varepsilon^{IJ}
$$
where $IJ = (i_1, \cdots, i_k, j_1, \cdots, j_k)$ is obtained by concatenating $I$ and $J$.

**外积运算的性质**

Suppose $\omega, \omega', \eta, \eta'$ and $\xi$ are multi-covectors on a finite-dimensional vector space $V$.

+ **线性 Bilinearity**: For $a, a' \in \mathbb{R}$,
  $$
  \begin{aligned}
  &\left(a \omega+a^{\prime} \omega^{\prime}\right) \wedge \eta=a(\omega \wedge \eta)+a^{\prime}\left(\omega^{\prime} \wedge \eta\right)\\
  &\eta \wedge\left(a \omega+a^{\prime} \omega^{\prime}\right)=a(\eta \wedge \omega)+a^{\prime}\left(\eta \wedge \omega^{\prime}\right)
  \end{aligned}
  $$

+ **结合律 Associativity**:
  $$
  \omega \wedge (\eta \wedge \xi) = (\omega \wedge \eta) \wedge \xi
  $$

+ **反交换律 Anti-commutativity**: For $\omega \in \Lambda^{k}\left(V^{\*}\right) $and $\eta \in \Lambda^{l}\left(V^{\*}\right)$,
  $$
  \omega \wedge \eta = (-1)^{kl} \ \eta \wedge \omega
  $$

+ Suppose $\left(\varepsilon^1, \cdots, \varepsilon^n \right)$ is any basis for $V^*$, and $I = (i_1, \cdots, i_k)$ is any multi-index, then
  $$
  \varepsilon^{i_{1}} \wedge \cdots \wedge \varepsilon^{i_{k}}=\varepsilon^{I}
  $$

+ For any covectors $\omega^1, \cdots, \omega^k$ and vectors $(v_1, \cdots, v_k)$,
  $$
  \omega^{1} \wedge \cdots \wedge \omega^{k}\left(v_{1}, \ldots, v_{k}\right)=\operatorname{det}\left(\omega^{j}\left(v_{i}\right)\right)
  $$

### 内乘运算 Interior Multiplication

**内乘运算的定义**

Let $V$ be a finite-dimensional vector space. For each $v \in V$ and positive integer $k$, define a linear map $i_v: \Lambda^{k}\left(V^{\*}\right) \rightarrow \Lambda^{k-1}\left(V^{\*}\right)$, called **interior multiplication** by $v$, as follows:
$$
i_{v} \omega\left(w_{1}, \ldots, w_{k-1}\right)=\omega\left(v, w_{1}, \ldots, w_{k-1}\right)
$$
By convention, $i_v\omega$ is interpreted to be zero when $\omega$ is a $0$-covector.

**内乘运算的性质**

Let $V$ be a finite-dimensional vector space and $v \in V$,

+ $i_v \circ i_v = 0$.

+ For $\omega \in \Lambda^{k}\left(V^{\*}\right) $and $\eta \in \Lambda^{l}\left(V^{\*}\right)$,
  $$
  i_{v}(\omega \wedge \eta)=\left(i_{v} \omega\right) \wedge \eta+(-1)^{k} \omega \wedge\left(i_{v} \eta\right)
  $$

## 流形上的微分形式 Differential Forms on Manifolds

### 微分形式

**微分形式的定义**

The subset of $T^k T^* M$ consisting of alternating tensors is denoted by $\Lambda^k T^* M$:
$$
\Lambda^{k} T^{\*} M=\coprod_{p \in M} \Lambda^{k}\left(T_{p}^{\*} M\right)
$$
A section of $\Lambda^k T^* M$ is called a **differential $k$-form**, or just a **$k$-form**, which means a continuous tensor field whose value at each point is an alternating tensor.

The integer $k$ is called the **degree** of the form.

A $0$-form is just a continuous real-valued function, and a $1$-form is a covector field.

**光滑微分形式**

The vector space of smooth $k$-forms is donated by
$$
\Omega^{k}(M)=\Gamma\left(\Lambda^{k} T^{*} M\right)
$$
**微分形式外积的局部表示与光滑性条件**

In any smooth chart $(U, \varphi; x^i)$, a $k$-form $\omega$ can be written locally as
$$
\omega=\sum_{I}' \omega_{I} d x^{i_{1}} \wedge \cdots \wedge d x^{i_{k}}=\sum_{I}' \omega_{I} d x^{I}
$$
where the coefficients $\omega^I$ are continuous functions defined on the coordinate domain.
$$
\omega_{I}=\omega\left(\frac{\partial}{\partial x^{i_{1}}}, \ldots, \frac{\partial}{\partial x^{i_{k}}}\right)
$$
$\omega$ is smooth on $U$ if and only if the component functions $\omega_I$ are smooth.

**微分形式的外积**

The wedge product of two differential forms is defined pointwise: $(\omega \wedge \eta)_p = \omega_p \wedge \eta_p$.

The wedge product of a $k$-form with an $l$-form is a $(k+l)$-form.

If $f$ is a $0$-form and $\eta$ is a $k$-form, the wedge product $f\wedge \eta$ is interpreted to mean the ordinary product $f\eta$.

**微分形式的内乘运算**

If $X \in \mathfrak{X}(M)$ and $\omega \in \Omega^k(M)$, define a $(k-1)$-form $i_X\omega$ by
$$
(i_X\omega)_p = i_{X_p}(\omega_p)
$$
If $X \in \mathfrak{X}(M)$ and $\omega \in \Omega^k(M)$,

+ $i_X \omega \in \Omega^{k-1}(M)$.
+ $i_X: \Omega^{k}\left(M\right) \rightarrow \Omega^{k-1}\left(M\right)$ is linear over $C^\infty(M)$.

### 微分形式的拉回映射

**微分形式拉回映射的定义**

If $F: M \rightarrow N$ is a smooth map between smooth manifolds and $\omega$ is a differential form on $N$, the pullback $F^*\omega$ is a differential form on $M$, defined as
$$
\left(F^{*} \omega\right)_{p}\left(v_{1}, \ldots, v_{k}\right)=\omega_{F(p)}\left(d F_{p}\left(v_{1}\right), \ldots, d F_{p}\left(v_{k}\right)\right)
$$
**微分形式拉回映射的性质**

Suppose $F: M \rightarrow N$ is smooth.

+ $F^* : \Omega^k(N) \rightarrow \Omega^k(M)$ is linear over $\mathbb{R}$.

+ $F^{*}(\omega \wedge \eta)=\left(F^{*} \omega\right) \wedge\left(F^{*} \eta\right)$.

+ In any smooth chart,
  $$
  F^{*}\left(\sum_{I}' \omega_{I} d y^{i_{1}} \wedge \cdots \wedge d y_{k}^{i_{k}}\right)=\sum_{I}'\left(\omega_{I} \circ F\right) d\left(y^{i_{1}} \circ F\right) \wedge \cdots \wedge d\left(y^{i_{k}} \circ F\right)
  $$

**最高阶微分形式的拉回**

Let $F: M \rightarrow N$ be a smooth map between $n$-manifolds. If $(x^i)$ and $(y^i)$ are smooth coordinates on open subsets $U \subset M$ and $V \subset N$, respectively, and $u$ is a continuous real-valued function on $V$, then the following holds on $U \cap F^{-1}(V)$,
$$
F^{*}\left(u \ d y^{1} \wedge \cdots \wedge d y^{n}\right)=(u \circ F)(\operatorname{det} D F) d x^{1} \wedge \cdots \wedge d x^{n}
$$
where $DF$ represents the Jacobian matrix of $F$ in these coordinates.

**微分形式与坐标变换**

If $(U, \varphi; x^i)$ and $(\tilde{U}, \tilde{\varphi}; \tilde{x}^j)$ are overlapping smooth coordinate charts on $M$, then the following identity holds on $U \cap \tilde{U}$,
$$
d \widetilde{x}^{1} \wedge \cdots \wedge d \widetilde{x}^{n}=\operatorname{det}\left(\frac{\partial \widetilde{x}^{j}}{\partial x^{i}}\right) d x^{1} \wedge \cdots \wedge d x^{n}
$$

## 外微分 Exterior Derivatives

### 欧式空间中的外微分算子 The Exterior Derivative on $\mathbb{R}^n$

**欧式空间中的外微分算子的定义**

If $\sum_{J}^{'} \omega_{J} d x^{J}$ is a smooth $k$-form on an open subset $U \subset \mathbb{R}^n$, its exterior derivative $d\omega$ is defined to be to be the following $(k+1)$-form:
$$
d\left(\sum_{J}' \omega_{J} d x^{J}\right)=\sum_{J}' d \omega_{J} \wedge d x^{J}
$$
where $d\omega^J$ is the differential of the function $\omega^J$.
$$
d\left(\sum_{J}' \omega_{J} d x^{j_{1}} \wedge \cdots \wedge d x^{j_{k}}\right)=\sum_{J}' \sum_{i} \frac{\partial \omega_{J}}{\partial x^{i}} d x^{i} \wedge d x^{j_{1}} \wedge \cdots \wedge d x^{j_{k}}
$$

+ For a smooth $0$-form $f$ (a real-valued function),
  $$
  d f=\frac{\partial f}{\partial x^{i}} d x^{i}
  $$

+ When $\omega$ is a $1$-form,
  $$
  \begin{aligned}d\left(\omega_{j} d x^{j}\right) &=\sum_{i, j} \frac{\partial \omega_{j}}{\partial x^{i}} d x^{i} \wedge d x^{j} \\&=\sum_{i<j}\left(\frac{\partial \omega_{j}}{\partial x^{i}}-\frac{\partial \omega_{i}}{\partial x^{j}}\right) d x^{i} \wedge d x^{j}\end{aligned}
  $$

**欧式空间中的外微分算子的性质**

+ $d$ is linear over $\mathbb{R}$.

+ If $\omega$ is a smooth $k$-form and $\eta$ is a smooth $l$-form on an open subset $U \subset \mathbb{R}^n$, then
  $$
  d(\omega \wedge \eta)=d \omega \wedge \eta+(-1)^{k} \omega \wedge d \eta
  $$

+ $d \circ d \equiv 0$.

+ $d$ commutes with pullbacks: if $U$ is an open subset of $\mathbb{R}^n$, $V$ is an open subset of $\mathbb{R}^m$, $F: M \rightarrow N$ is a smooth map, and $\omega \in \Omega^k(V)$, then
  $$
  F^*(d \omega) = d(F^* \omega)
  $$

### 一般流形上的外微分算子 Exterior Differentiation on Smooth Manifolds

**外微分算子的存在唯一性 Existence and Uniqueness of Exterior Differentiation**

Suppose $M$ is a smooth manifold. There are unique operators $d: \Omega^k(M) \rightarrow \Omega^{k+1}(M)$ for all $k$, called exterior differentiation, satisfying the following four properties:

+ $d$ is linear over $\mathbb{R}$.

+ If $\omega \in \Omega^k(M)$ and $\eta \in \Omega^l(M)$, then
  $$
  d(\omega \wedge \eta)=d \omega \wedge \eta+(-1)^{k} \omega \wedge d \eta
  $$

+ $d \circ d \equiv 0$.

+ For $f \in \Omega^0(M) = C^\infty(M)$, $df$ is the differential of $f$, given by $df(X) = Xf$.

**外微分算子的构造**

Suppose $\omega \in \Omega^k(M)$. For each smooth chart $(U, \varphi)$ for $M$, set
$$
d \omega=\varphi^{*} d\left(\varphi^{-1 *} \omega\right)
$$
**外微分算子与拉回映射 Naturality of the Exterior Derivative**

If $F: M \rightarrow N$ is a smooth map, then for each $k$ the pullback map $F^*: \Omega^k(N) \rightarrow \Omega^k(M)$ commutes with $d$.
$$
F^*(d \omega) = d(F^* \omega), \quad \forall \omega \in \Omega^k(N)
$$

### Exterior Derivatives and Vector Calculus in $\mathbb{R}^3$

### An Invariant Formula for the Exterior Derivative

### Lie Derivatives ofDifferential Forms

