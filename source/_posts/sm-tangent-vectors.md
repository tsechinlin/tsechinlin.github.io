---
title: 微分流形笔记 - Tangent Vectors 切向量
date: 2019-12-28 01:12:04
tags: 
  - Smooth Manifolds
categories: Manifolds
mathjax: true
---

[GTM-218] John M. Lee - Introduction to Smooth Manifolds 第三章笔记。

<!--more-->

## 切空间与切向量

### 欧式空间中的切空间与切向量

The **geometric tangent space** to $\mathbb{R}^n$ at $a$
$$
\mathbb{R}^n_a :=\{a\} \times \mathbb{R}^{n}=\left\{(a, v): v \in \mathbb{R}^{n}\right\}
$$
A **geometric tangent vector** in $\mathbb{R}^n$ is an element of $\mathbb{R}^n_a$ for some $a \in \mathbb{R}^n$. As a matter of notation, we abbreviate $(a, v)$ as $v_a$ or $v|_a$.

The set $\mathbb{R}^n_a$ is a real vector space under the natural operations
$$
v_a+w_a=(v+w)_a, \quad c(v_a) = (cv)_a
$$
The vectors $e_i|_a, i = 1, \cdots, n$, are a basis for $\mathbb{R}^n_a$.

### 由切向量自然引出方向导数

Any geometric tangent vector $v_a \in \mathbb{R}^n_a$ yields a map $\left.D_{v}\right|_{a}: C^{\infty}\left(\mathbb{R}^{n}\right) \rightarrow \mathbb{R}$,
$$
\left.D_{v}\right|_{a} f=D_{v} f(a)=\left.\frac{d}{d t}\right|_{t=0} f(a+t v)
$$

+ $\left.D_{v}\right|_{a}$ is linear over $\mathbb{R}$.
  $$
  \left.D_{v}\right|_{a}(f+g) = \left.D_{v}\right|_{a}f + \left.D_{v}\right|_{a}g, \quad \forall f, g \in C^{\infty}\left(\mathbb{R}^{n}\right)
  $$

+ $\left.D_{v}\right|_{a}$ satisfies the product rule.
  $$
  \left.D_{v}\right|_{a}(f g)=\left.f(a) D_{v}\right|_{a} g+\left.g(a) D_{v}\right|_{a} f
  $$

If $v_{a}=\left.v^{i} e_{i}\right|_{a}$, then
$$
\left.D_{v}\right|_{a} f= v^{i} \left.D_{e_i}\right|_{a} f =  v^{i} \frac{\partial f}{\partial x^{i}}(a)
$$

### 欧式空间中的 Derivation

If $a \in \mathbb{R}^n$, a map $w: C^{\infty}\left(\mathbb{R}^{n}\right) \rightarrow \mathbb{R}$ is called a **derivation** at $a$ if 

+ $w$ is linear over $R$.

+ $w$ satisfies the following product rule.
  $$
  w(f g)=f(a) w g+g(a) w f \quad \text { for all } f, g \in C^{\infty}(\mathbb{R}^n)
  $$

Let $T_a \mathbb{R}^n$ denote the set of all derivations of at $a$. 

$T_a \mathbb{R}^n$ is a vector space under the operations
$$
\left(w_{1}+w_{2}\right) f=w_{1} f+w_{2} f, \quad(c w) f=c(w f)
$$
__Properties__

Suppose $a \in \mathbb{R}^{n}, w \in T_{a} \mathbb{R}^{n}$, and $f, g \in C^{\infty}\left(\mathbb{R}^{n}\right)$.

+ If $f$ is a constant function, then $wf = 0$.
+ If $f(a) = g(a) = 0$, then $w(fg) = 0$.

### $T_a \mathbb{R}^n$ 与 $\mathbb{R}^n_a$ 同构

$T_{a} \mathbb{R}^{n}$ is naturally isomorphic to the geometric tangent space $\mathbb{R}^n_a$.

+ For each geometric tangent vector $v_a \in \mathbb{R}^n_a$, the map $\left.D_{v}\right|_{a}: C^{\infty}\left(\mathbb{R}^{n}\right) \rightarrow \mathbb{R}$ is a derivation at $a$.
+ The map $\left.v_{a} \mapsto D_{v}\right|_{a}$ is an isomorphism from $\mathbb{R}^n_a$ onto $T_{a} \mathbb{R}^{n}$.

For any $a \in \mathbb{R}^n$, the $n$ derivations
$$
\left.\frac{\partial}{\partial x^{1}}\right|_{a}, \cdots,\left.\frac{\partial}{\partial x^{n}}\right|_{a} \quad \text { defined by } \quad\left.\frac{\partial}{\partial x^{i}}\right|_{a} f=\frac{\partial f}{\partial x^{i}}(a)
$$
form a basis for $T_{a} \mathbb{R}^{n}$, which therefore has dimension $n$.

### 一般流形中的 Derivation

Let $M$ be a smooth manifold, and $p \in M$. A map $v: C^{\infty}\left(M\right) \rightarrow \mathbb{R}$ is called a **derivation** at $p$ if

+ $v$ is linear over $\mathbb{R}$.

+ $v$ satisfies the following product rule.
  $$
  v(f g)=f(p) v g+g(p) v f \quad \text { for all } f, g \in C^{\infty}(M)
  $$

**Properties**

Suppose $M$ is a smooth manifold, $p \in M, v \in T_{a} M$, and $f, g \in C^{\infty}\left(M\right)$.

+ If $f$ is a constant function, then $vf = 0$.
+ If $f(p) = g(p) = 0$, then $v(fg) = 0$.

## 光滑函数的微分

### 函数微分的定义与基本性质

If $M$ and $N$ are smooth manifolds and $F: M \rightarrow N$ is a smooth map, for each $p \in M$ we define a map
$$
d F_{p}: T_{p} M \rightarrow T_{F(p)} N
$$
called the the **differential** of $F$ at $p$. Given $v \in T_pM$, we let $dF_p(v)$ be the derivation at $F(p)$ that acts on $f \in C^{\infty}(N)$ by the rule
$$
d F_{p}(v)(f)=v(f \circ F)
$$
**Properties**

Let $M, N$, and P be smooth manifolds, let $F: M \rightarrow N$ and $G: N \rightarrow P$ be smooth maps, and let $p \in M$.

+ **线性** $d F_{p}: T_{p} M \rightarrow T_{F(p)} N$ is linear.

+ **复合** $d(G \circ F)_{p}=d G_{F(p)} \circ d F_{p}: T_{p} M \rightarrow T_{G \circ F(p)} P$

+ **恒等映射的切映射** $d\left(\mathrm{Id}_{M}\right)_{p}=\mathrm{Id}_{T_{p} M}: T_{p} M \rightarrow T_{p} M$

+ **微分同胚的切映射** If $F$ is a diffeomorphism, then $d F_{p}: T_{p} M \rightarrow T_{F(p)} N$ is an isomorphism, and
  $$
  \left(d F_{p}\right)^{-1}=d\left(F^{-1}\right)_{F(p)}
  $$

### 函数微分的作用是局部的

**Tangent Vectors Act Locally**

Let $M$ be a smooth manifold, $p \in M$, and $v \in T_pM$. If $f,g \in C^\infty(M)$ agree on some neighborhood of $p$, then $vf = vg$.

**The Tangent Space to an Open Submanifold**

Let $M$ be a smooth manifold, let $U \subset M$ be an open subset, and let $\iota: U \hookrightarrow M$ be the inclusion map. For every $p \in U$, the differential $d\iota_p: T_pU \rightarrow T_pM$ is an isomorphism.

### 切空间的维数

If $M$ is an $n$-dimensional smooth manifold, then for each $p \in M$, the tangent space $T_pM$ is an $n$-dimensional vector space.

### 向量空间，积空间的切空间

**The Tangent Space to a Vector Space**

Suppose $V$ is a finite-dimensional vector space with its standard smooth manifold structure and $a \in V$. For any vector $v \in V$, we define a map $\left.D_{v}\right|_{a}: C^{\infty}(V) \rightarrow \mathbb{R}$ by
$$
\left.D_{v}\right|_{a} f=\left.\frac{d}{d t}\right|_{t=0} f(a+t v)
$$
This map $v \rightarrow D_v|_a$ is a canonical isomorphism from $V$ to $T_aV$.

If $W$ is another finite-dimensional vector space, then for any linear map $L:V \rightarrow W$ and $v \in V$,
$$
dL_a(D_v|_a) = D_{Lv}|_{La}
$$
**The Tangent Space to a Product Manifold**

Let $M_1, \cdots, M_k$ be smooth manifolds, and for each $j$, let $\pi_j: M_1 \times \cdots \times M_k \rightarrow M_j$ be the projection onto the $M_j$ factor. For any point $p=\left(p_{1}, \ldots, p_{k}\right) \in M_{1} \times \cdots \times M_{k}$, the map
$$
\alpha: T_{p}\left(M_{1} \times \cdots \times M_{k}\right) \rightarrow T_{p_{1}} M_{1} \oplus \cdots \oplus T_{p_{k}} M_{k}
$$
defined by
$$
\alpha(v)=\left(d\left(\pi_{1}\right)_{p}(v), \ldots, d\left(\pi_{k}\right)_{p}(v)\right)
$$
is an isomorphism.

## 切向量，微分在局部坐标下的表示

### 切向量的坐标表示

Suppose $M$ is a smooth manifold, and let $(U, \varphi)$ be a smooth coordinate chart on $M$. Then $\varphi$ is a diffeomorphism from $U$ to an open subset $\hat{U}\subset \mathbb{R}^n$ and thus $d \varphi_{p}: T_{p} M \rightarrow T_{\varphi(p)} \mathbb{R}^{n}$ is an isomorphism.

The derivations $\partial /\left.\partial x^{1}\right|_{\varphi(p)}, \ldots, \partial /\left.\partial x^{n}\right|_{\varphi(p)}$ forms a basis for $T_{\varphi(p)}{\mathbb{R}^n}$. Therefore, the preimages of these vectors under the isomorphism $d \varphi_{p}$ form a basis for $T_pM$.
$$
\left.\frac{\partial}{\partial x^{i}}\right|_{p} = 
(d \varphi_{p})^{-1} \left( \left.\frac{\partial}{\partial x^{i}}\right|_{\varphi(p)} \right) =
d (\varphi^{-1})_{\varphi(p)} \left( \left.\frac{\partial}{\partial x^{i}}\right|_{\varphi(p)} \right)
$$
For any $f \in C^{\infty}(U)$,
$$
\left.\frac{\partial}{\partial x^{i}}\right|_{p}=\left.\frac{\partial}{\partial x^{i}}\right|_{\varphi(p)}\left(f \circ \varphi^{-1}\right)=\frac{\partial \hat{f}}{\partial x^{i}}(\hat{p})
$$
where $\hat{f} = f \circ \varphi^{-1}$ is the coordinate representation of $f$, and $\hat{p} = \varphi(p)$ is the coordinate representation of $p$.

+ The vectors $\partial/\partial x^i |_p$ are called the **coordinate vectors** at $p$ associated with the given coordinate system.

+ A tangent vector $v \in T_pM$ can be written uniquely as a linear combination
  $$
  v=\left.v^{i} \frac{\partial}{\partial x^{i}}\right|_{p}
  $$

+ The orderd basis $(\partial/\partial x^i |_p)$ is called a **coordinate basis** for $T_pM$, and $(v^1, \cdots, v^n)$ are called the components of $v$ with respect to the coordinate basis.

+ Computation of components: $v^j = v(x^j)$.
  $$
  v\left(x^{j}\right)=
  \left( \left.v^{i} \frac{\partial}{\partial x^{i}}\right|_{p} \right)\left(x^{j}\right)=v^{i} \frac{\partial x^{j}}{\partial x^{i}}(p)=v^{j}
  $$

### 微分/切映射的坐标表示

**Euclidean Spaces**

Suppose $F: U \rightarrow V$ is a smooth map between open subsets $U \subset \mathbb{R}^n$ and $V \subset \mathbb{R}^m$. For any $p \in U$, using $(x^1, \cdots, x^n)$ to donate the coordinates in the domain and $(y^1, \cdots, y^m)$ to donate those in the codomain, we obtain
$$
\begin{aligned}
d F_{p}\left( \left. \frac{\partial}{\partial x^{i}}\right|_{p} \right) f 
&=\left.\frac{\partial}{\partial x^{i}}\right|_{p}(f \circ F) \\
&=\frac{\partial f}{\partial y^{j}}(F(p)) \frac{\partial F^{j}}{\partial x^{i}}(p) \\
&=\left( \frac{\partial F^j}{\partial x^{i}}(p) \left. \frac{\partial}{\partial y^{i}}\right|_{F(p)} \right) f
\end{aligned}
$$
In other words, the matrix of $dF_p$ in terms of the coordinate bases is the Jacobian matrix of $F$ at $p$.
$$
\left(\begin{array}{ccc}
{\frac{\partial F^{1}}{\partial x^{1}}(p)} & {\cdots} & {\frac{\partial F^{1}}{\partial x^{n}}(p)} \\
{\vdots} & {\ddots} & {\vdots} \\
{\frac{\partial F^{m}}{\partial x^{1}}(p)} & {\cdots} & {\frac{\partial F^{m}}{\partial x^{n}}(p)}
\end{array}\right)
$$
**General Manifolds**

Suppose $F: M \rightarrow N$ is a smooth map between smooth manifolds. For any $p \in M$, choosing smooth coordinate charts $(U, \varphi; x^i)$ for $M$ containing $p$ and $(V, \psi; y^i)$ for $N$ containing $F(p)$, we obtain the coordinate representation
$$
\widehat{F}=\psi \circ F \circ \varphi^{-1}: \varphi\left(U \cap F^{-1}(V)\right) \rightarrow \psi(V)
$$
Using the fact that $F \circ \varphi^{-1} = \psi^{-1} \circ \hat{F}$, we obtain
$$
\begin{aligned}
d F_{p}\left( \left. \frac{\partial}{\partial x^{i}}\right|_{p} \right)
&= d F_{p}\left( d (\varphi^{-1})_{\hat{p}} \left( \left.\frac{\partial}{\partial x^{i}}\right|_{\hat{p}} \right) \right) \\
&= d (\psi^{-1})_{\hat{F}(\hat{p}) }\left( d \hat{F}_{\hat{p}} \left( \left.\frac{\partial}{\partial x^{i}}\right|_{\hat{p}} \right) \right) \\
&= d (\psi^{-1})_{\hat{F}(\hat{p}) } \left( \frac{\partial \hat{F}^j}{\partial x^{i}}(\hat{p}) \left. \frac{\partial}{\partial y^{i}}\right|_{\hat{F}(\hat{p})} \right) \\
&= \frac{\partial \hat{F}^j}{\partial x^{i}}(\hat{p}) \left. \frac{\partial}{\partial y^{i}}\right|_{F(p)} \\
\end{aligned}
$$
Therefore, the matrix of $dF_p$ in terms of the coordinate bases is the Jacobian matrix of $\hat{F}$ at $p$.

### 切向量与坐标变换

Suppose $(U, \varphi; x^i)$ and $(V, \psi; \tilde{x}^i)$ are two smooth charts on $M$, and $p \in U \cap V$. Assume that the transition map $\psi \circ \varphi^{-1}: \varphi(U \cap V) \rightarrow \psi(U \cap V)$ has the following shorthand notation:
$$
\psi \circ \varphi^{-1}(x)=\left(\widetilde{x}^{1}(x), \ldots, \widetilde{x}^{n}(x)\right)
$$
Then
$$
\left. \frac{\partial}{\partial x^{i}}\right|_{p} = d\left(\mathrm{Id}_{U\cap V}\right)_{p}\left(\left. \frac{\partial}{\partial x^{i}}\right|_{p} \right) = \frac{\partial \tilde{x}^j}{\partial x^{i}}(\varphi(p)) \left. \frac{\partial}{\partial \tilde{x}^j}\right|_{p}
$$

Applying this to the components of a vector $v=v^{i} \partial /\left.\partial x^{i}\right|_{p}=\widetilde{v}^{j} \partial /\left.\partial \widetilde{x}^{j}\right|_{p}$, we find that
$$
\widetilde{v}^{j}=\frac{\partial \widetilde{x}^{j}}{\partial x^{i}}(\varphi{(p)}) v^{i}
$$

## 切丛

