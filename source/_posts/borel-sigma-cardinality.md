---
title: $\mathbb{R}^k$ 中 Borel $\sigma$-代数的基数
date: 2019-11-06 23:42:19
tags: 
  - Borel Set
  - Cardinality
categories: Real Analysis
mathjax: true
---

有限维欧式空间 $\mathbb{R}^k$ 中有多少 Borel 集？第一次碰到这个问题是在 Rudin 的实分析与复分析一书中。该书在第二章中讨论 $\mathbb{R}^k$ 中 Lebesgue 可测集与 Borel 集关系时，提到 $\mathbb{R}^k$ 中的 Borel $\sigma$-代数具有连续统势。书上并没有给出这个结论的证明，只是一笔带过，事实上这个结论并不是特别好证。找了一些相关的证明，发现有一种思路比较巧妙，也比较容易接受，所以在这里记录下来。
参考：[How Many Borel Sets are There?](https://math.dartmouth.edu/archive/m103f08/public_html/borel-sets-soln.pdf)

<!--more-->

## 问题描述

> 赋 $\mathbb{R}^k$ 以标准拓扑，其中 $k \in \mathbb{Z}_+$。假设 $\mathcal{B}_k$ 表示该空间中的 Borel $\sigma$-代数。求证：
> $$
> \operatorname{Card}\left(\mathcal{B}_k\right) = \mathfrak{c} := \operatorname{Card}(\mathbb{R})
> $$

即有限维欧式空间中的 Borel $\sigma$ 代数具有连续统势。$\mathcal{B}_k$ 至少有连续统势是显然的，所以只需证明另一方向。事实上，我们可以证明一个更一般的结论。

> 假设 $X$ 为一集合，$\mathcal{D}$ 为 $X$ 的某个非空子集族，即 $\mathcal{D} \subset \mathcal{P}(X)$，用 $\sigma(\mathcal{D})$ 表示 $\mathcal{D}$ 生成的 $\sigma$-代数。那么，当 $\operatorname{Card}\left(\mathcal{D}\right) \leq \mathfrak{c}$ 时，有 $\operatorname{Card}\left(\sigma(\mathcal{D})\right) \leq \mathfrak{c}$。

在有了这个结论之后，再说明 $\mathcal{B}_k$ 可以由有连续统势的子集族生成即可证明原命题。

## 结论证明

### 构造

为了完成结论的证明，首先需要引入下述操作符。对任意的子集族 $\mathcal{B} \subset \mathcal{P}(X)$，定义
$$
\mathcal{B}^c := \left\{ E^c : E \in \mathcal{B} \right\} \\
\mathcal{B}^{\sigma} := \left\{ \bigcup_{i=1}^{\infty}{E_i} : \ E_i \in \mathcal{B}, i \in \mathbb{Z}_+ \right\}
$$
另外证明过程中需要借助极小不可数良序集 $\Omega$ (minimal uncountable well-order set，可参考 Munkres 的拓扑学第 10 节)。借助 $\Omega$ 以及广义归纳定义原理 (general principle of recursive definition，可参考 Munkres 的拓扑学第 1 章附加习题)，定义：

+ $\mathcal{F}_1 := \mathcal{D} \cup \mathcal{D}^c$
+ $\forall x \in \Omega, x > 1,$
  + 如果 $x$ 有紧接前元 $y$，$\mathcal{F}_x := \mathcal{F}_{y}^{\sigma} \cup (\mathcal{F}_{y}^{\sigma})^c$
  + 如果 $x$ 没有紧接前元，$\mathcal{F}_x := \bigcup_{y < x} \mathcal{F}_{y}$
+ 最后令 $\mathcal{F} := \bigcup_{x \in \Omega} \mathcal{F}_{x}$

### 构造所得的集合与 $\sigma$-域相等

> $\mathcal{F} \subset \sigma(\mathcal{D})$

只需证明：$\forall x \in \Omega$，$\mathcal{F}_x \subset \sigma(\mathcal{D})$。可以使用超限归纳原理 (principle of transfinite induction) 证明。

+ 首先根据 $\mathcal{D} \subset \sigma(\mathcal{D})$，容易证得 $\mathcal{D}^c \subset \sigma(\mathcal{D})$，于是 $\mathcal{F}_1 = \mathcal{D} \cup \mathcal{D}^c \subset \sigma(\mathcal{D})$。
+ 假设 $x \in \Omega$ 且 $x > 1$，而且 $\forall y < x$，有 $\mathcal{F}_y  \subset \sigma(\mathcal{D})$。
  + 如果 $x$ 有紧接前元 $y$，由于 $\mathcal{F}_{y}^{\sigma}$ 中的集合仅由 $\mathcal{F}_{y}$ 中的集合的可数并组成，于是  $\mathcal{F}_y^{\sigma}  \subset \sigma(\mathcal{D})$，从而 $\mathcal{F}_x = \mathcal{F}_{y}^{\sigma} \cup (\mathcal{F}_{y}^{\sigma})^c \subset \sigma(\mathcal{D})$。
  + 如果 $x$ 没有紧接前元，$\mathcal{F}_x = \bigcup_{y < x} \mathcal{F}_{y} \subset \sigma(\mathcal{D})$ 显然成立。

于是根据超限归纳原理，$\forall x \in \Omega$，$\mathcal{F}_x \subset \sigma(\mathcal{D})$，于是 $\mathcal{F} = \bigcup_{x \in \Omega} \mathcal{F}_{x} \subset \sigma(\mathcal{D})$。

> $\sigma(\mathcal{D}) \subset \mathcal{F}$

只需证明 $\mathcal{F}$ 为 $\sigma$-代数。

+ 任取 $E \in \mathcal{D}$，则 $X = E^c \cup E \cup E \cup \cdots \cup E \cup \cdots$，于是
  $$
  X \in \mathcal{F}_1^{\sigma} \subset \mathcal{F}_2 \subset \mathcal{F}
  $$
  此时还可以得到 $\varnothing  \in \mathcal{F}_3$，所以 $x\in \Omega, x \geq 3$ 时，有 $\mathcal{F}_x \subset \mathcal{F}_x^{\sigma} \subset \mathcal{F}_{x+1}$。

+ $\forall E \in \mathcal{F}, \exists x\in \Omega$ 使得 $E \in \mathcal{F}_x$，于是
  $$
  E^c \in \mathcal{F}_x^c \subset \mathcal{F}_{x+1} \subset \mathcal{F}
  $$

+ 设 $\{E_i\}_{i=1}^\infty \subset \mathcal{F}$，则 $\forall i \in \mathbb{Z}_+, \exists x_i \in \Omega$，使得 $E_i \in \mathcal{F}_{x_i}$。由于 $\{ x_i \}_{i=1}^{\infty} \subset \Omega$ 为可数集，$\{x_i\}$ 在 $\Omega$ 中必有上界 $x$ (同样参考 Munkres 的拓扑学第 10 节)。这个上界可以选取的足够大，使其至少不小于一个没有紧接前元的元素 (为了使 $\mathcal{F}_1, \mathcal{F}_2 \subset \mathcal{F}_x$)，于是根据第一条的推论，$\forall i \in \mathbb{Z}_+, E_i \in \mathcal{F}_x$。从而
  $$
  \bigcup_{i}{E_i} \in \mathcal{F}_x^{\sigma} \subset \mathcal{F}_{x+1} \subset \mathcal{F}
  $$

### $\mathcal{F}$ 至多为连续统势

> $\forall x \in \Omega, \operatorname{Card}\left(\mathcal{F}_x\right) \leq \mathfrak{c}$

同样使用超限归纳原理证明。

+ 由于 $\operatorname{Card}\left(\mathcal{D}\right) \leq \mathfrak{c}$，所以 $\operatorname{Card}\left(\mathcal{D}^c\right)=\operatorname{Card}\left(\mathcal{D}\right) \leq \mathfrak{c}$，从而
  $$
  \operatorname{Card}\left(\mathcal{F}_1\right) = \operatorname{Card}\left(\mathcal{D} \cup \mathcal{D}^c\right) \leq \mathfrak{c}
  $$

+ 假设 $x > 1, x \in \Omega$，并且 $\forall y < x, \operatorname{Card}\left(\mathcal{F}_y\right) \leq \mathfrak{c},$

  + 若 $x$ 有紧接前元 $z$，由于 $\operatorname{Card}\left(\mathcal{F}_z\right) \leq \mathfrak{c}$，存在满射 $f: \mathbb{R} \rightarrow \mathcal{F}_z$，令 $g:\mathbb{R}^{\infty} \rightarrow \mathcal{F}_z^{\sigma}$，使得
    $$
    g(x_1, x_2, \cdots) = \bigcup_i{f(x_i)}, \quad x_i \in \mathbb{R}, i = 1, 2, \cdots
    $$
    于是 $g$ 为满射，故 $\operatorname{Card}\left( \mathcal{F}_z^{\sigma} \right) \leq \operatorname{Card}\left( \mathbb{R}^{\infty} \right) \leq \mathfrak{c}$，从而
    $$
    \operatorname{Card}\left(\mathcal{F}_x\right) = \operatorname{Card}\left(\mathcal{F}_z^{\sigma} \cup (\mathcal{F}_z^{\sigma})^c\right) \leq \mathfrak{c}
    $$

  + 如果 $x$ 没有紧接前元，由于 $S_x := \{y\in \Omega:y<x\}$ 为可数集，所以
    $$
    \operatorname{Card}\left(\mathcal{F}_x\right) = \operatorname{Card}\left( \bigcup_{y < x} \mathcal{F}_{y} \right) \leq \operatorname{Card}\left(S_x \times \mathbb{R}\right) = \mathfrak{c}
    $$

> $\operatorname{Card}\left(\mathcal{F}\right) \leq \mathfrak{c}$ 

这个结论的证明需要使用 $\operatorname{Card}\left(\Omega\right) \leq \mathfrak{c}$，事实上，可以很简单地利用广义归纳定义原理定义出一个单射 $f: \Omega \rightarrow \mathbb{R}$。首先在 $\mathbb{R}$ 上定义良序，然后定义：
$$
\forall x \in \Omega, f(x) = min\left\{ \mathbb{R} - f(S_x) \right\}, \quad S_x = \{y\in \Omega:y < x \}
$$
由于 $\forall x \in \Omega$，$S_x$ 可数，所以 $\mathbb{R} - f(S_x)$ 非空，所以 $f$ 是 well-defined 的，并且容易证明其为单射。

利用上述结论，可以得到：
$$
\operatorname{Card}\left(\mathcal{F}\right) = \operatorname{Card}\left( \bigcup_{x \in \Omega} \mathcal{F}_{x} \right) \leq \operatorname{Card}\left(\Omega \times \mathbb{R}\right) \leq \mathfrak{c}^2 = \mathfrak{c}
$$
事实上到这里证明就基本完成了：
$$
\operatorname{Card}\left(\sigma(\mathcal{D})\right) = \operatorname{Card}\left(\mathcal{F}\right) \leq \mathfrak{c}
$$

### $\mathcal{B}_k$ 可以由至多为连续统势的集族导出

令 $\mathcal{D}_k = \left\{ B(x, r) : x \in \mathbb{Q}^k, r \in \mathbb{Q}_+ \right\}$，这是一个可数集，并且对 $\mathbb{R}^k$ 中任意开集 $V$，容易证得：
$$
V = \bigcup_{B \in \mathcal{D}_k, B \subset V} B
$$
上面的并是可数并，所以 $\sigma(\mathcal{D}_k)$ 包含所有的开集，因此容易得到：$\sigma(\mathcal{D}_k) = \mathcal{B}_k$，证毕。
