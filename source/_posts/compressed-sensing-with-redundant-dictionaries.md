---
title: "Compressed Sensing with Redundant Dictionaries - L1 Algorithm"
date: 2020-01-28 23:30:16
tags: 
  - Compressed Sensing
categories: Computational Mathematics
mathjax: true
---

[参考文献] Candes, E. J., Eldar, Y. C., Needell, D., & Randall, P. (2011). Compressed sensing with coherent and redundant dictionaries. Applied and Computational Harmonic Analysis, 31(1), 59-73.

<!--more-->

## Problem

$x \in \mathbb{R}^d, \quad f = Dx \in \mathbb{R}^n, \quad y = Af + z \in \mathbb{R}^m, \quad \lVert z \rVert \leq \varepsilon$

![](fig1.jpg)

**(P)**
$$
\hat{f}=\underset{\tilde{f} \in \mathbb{R}^{n}}{\arg \min }\left\|D^{*} \tilde{f}\right\|_{1} \quad \text { s.t. } \quad\|A \tilde{f}-y\|_{2} \leqslant \varepsilon.
$$

## Definitions

**$D$-RIP**

Let $\Sigma_s$ be the union of all subspaces spanned by all subsets of $s$ columns of $D$,
$$
\Sigma_s = \bigcup_{1 \leq i_1 < \cdots < i_s \leq d} \operatorname{span}(D_{i_1}, \cdots, D_{i_s}).
$$
The measurement matrix $A$ is said to be obey **the restricted isometry property adapted to $D$ (D-RIP)** with constant $\delta_s$ if
$$
(1 - \delta_s) \| v \|_2^2 \leq \| Av \|_2^2 \leq (1 + \delta_s) \| v \|_2^2, \quad \forall v \in \Sigma_s.
$$

## Theorem

Let $(D_i)_{i=1}^d \subset \mathbb{R}^n$ be an arbitrary tight frame with the associated synthesis operator $D = (D_1, \cdots, D_d ) \subset  \mathbb{R}^{n \times d}$, and let $A$ be a $m \times n$ measurement matrix satisfying **$D$-RIP** with $\delta_{2s} < 0.08$. Then the solution of **(P1)** satisfies
$$
\|\hat{f}-f\|_{2} \leqslant C_{0} \varepsilon+C_{1} \frac{\left\|D^{*} f-\left(D^{*} f\right)_{s}\right\|_{1}}{\sqrt{s}}
$$
where the constants $C_0$ and $C_1$ may only depend on $\delta_{2s}$.

## Proof

**Notations**

+ $h = f - \hat{f}.$

+ Let $T$ be a index set and denote $D_T$ as the matrix $D$ restricted to the columns indexed by $T$. In other words,
  $$
  (D_T)_{(i,j)} = 
  \begin{cases}
  D_{(i,j)}, & j \in T \\
  0, & j \notin T
  \end{cases}.
  $$
  We also write $D_T^\*$ to mean $(D_T)^\*$.

+ Let $T_0$ denote the index of the largest $s$ coefficients of $D^∗ f$ in magnitude:
  $$
  T_0 = \{ i: {[(D^* f)_s]} _{(i)} \not= 0 \},
  $$
  where $(D^\*f)_s$ is the the best $s$-sparse approximation of $D^\*f$.

### 引理 1 (Cone constraint)

The vector $D^∗h$ obeys the following cone constraint,
$$
\| D_{T_0^c}^* h \|_1 \leq 2 \| D _{T_0^c}^* f \|_1 + \| D _{T_0}^* h \|_1.
$$

> 由于 $f$ 和 $\hat{f}$ 都是可行解，而且 $\hat{f}$ 为最优值，所以目标函数值必满足 $\lVert D^\*f \|_1 \geq \rVert D^\* \hat{f} \|_1$。另外注意到对任意 $g \in \mathbb{R}^n$，有
> $$
> \| D^* g \|_1 = \| D_{T_0}^* g \|_1 + \| D_{T_0^c}^* g \|_1.
> $$
> 因此，
> $$
> \begin{split}
> \| D_{T_0}^* f \|_1 + \| D_{T_0^c}^* f \|_1 &= \| D^* f \|_1 \geq \| D^* \hat{f} \|_1 \\
> &= \| D^* (f - h) \|_1 \\
> &= \| D_{T_0}^* (f-h) \|_1 + \| D_{T_0^c}^* (f-h) \|_1 \\
> & \geq \| D_{T_0}^* f \|_1 - \| D_{T_0}^* h \|_1 + \| D_{T_0^c}^* h \|_1 -\| D_{T_0^c}^* f \|_1.
> \end{split}
> $$
>
> 于是引理 1 得证。

**Notations**

+ Divide the index set $T_0^c$ into sets of size $M$ (to be chosen later) in order of decreasing magnitude of $D^∗_{T_0^c} h$.

### 引理 2 (Bounding the tail)

Setting 
$$
\rho = \frac{s}{M}, \quad \eta = \frac{2 \| D^∗_{T_0^c} f\|_1}{\sqrt{s}},
$$
we have the following bound,
$$
\sum_{j \geqslant 2}\left\|D_{T_{j}}^{*} h\right\|_{2} \leq \sqrt{\rho}\left(\left\|D_{T_{0}}^{*} h\right\|_{2}+\eta\right)
$$

> 根据指标集 $T_j$ 的构造，$D^\*_ {T_{j+1}}h$ 中任意一个非零元素的绝对值至多为 $D^\*_ {T_{j}}h$ 中非零元素绝对值的平均值，即
> $$
> \left|D_{T_{j+1}}^{*} h\right|_{(k)} \leq \left\|D_{T_{j}}^{*} h\right\|_{1} / M, \quad \forall k \in T_{j+1}.
> $$
> 于是
> $$
> \left\|D_{T_{j+1}}^{*} h\right\|_2^2 \leq \left\|D_{T_{j}}^{*} h\right\|_{1}^2 / M,
> $$
> 再注意到 $T_i$ 之间两两不交，从而有
> $$
> \begin{split}
> \sum_{j \geq 2}\left\|D_{T_{j}}^{*} h\right\|_{2} & \leq \frac{1}{\sqrt{M}}{\sum_{j \geq 1}\left\|D_{T_{j}}^{*} h\right\|_{1} } \\
> & = \frac{1}{\sqrt{M}} \left\| \left(\sum_{j \geq 1} D_{T_j}^{*} \right) h\right\|_{1} =\frac{1}{\sqrt{M}}\left\|D_{T_{0}^{c}}^{*} h\right\|_{1}.
> \end{split}
> $$
> 根据引理 1，可以进一步得到
> $$
> \begin{split}
> \sum_{j \geq 2}\left\|D_{T_{j}}^{*} h\right\|_{2} 
> & \leq \frac{1}{\sqrt{M}} \left(2 \| D_{T_0^c}^* f \|_1 + \| D_{T_0}^* h \|_1 \right) \\
> & = \sqrt{\rho} \left( \eta + \frac{\left\|D_{T_{0}}^{*} h\right\|_{1}}{\sqrt{s}} \right) \\
> & \leq \sqrt{\rho} \left( \eta + {\left\|D_{T_{0}}^{*} h\right\|_{2}} \right).
> \end{split}
> $$
> 其中最后一步使用了 Cauchy–Schwarz 不等式。

**Notations**

+ $T_{01} = T_0 \cup T_1$.

### 引理 3 (Consequence of $D$-RIP)

The following inequality holds,
$$
\sqrt{1-\delta_{s+M}}\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}-\sqrt{\rho\left(1+\delta_{M}\right)}\left(\|h\|_{2}+\eta\right) \leq 2 \varepsilon
$$

> 由于 $f$ 和 $\hat{f}$ 都是可行解，
> $$
> \|A h\|_{2}=\|A f-A \hat{f}\|_{2} \leq \|A f-y\|_{2}+\|A \hat{f}-y\|_{2} \leq \varepsilon+\varepsilon=2 \varepsilon.
> $$
> 根据定理条件，$D$ 为 tight frame，于是 $DD^\* = \operatorname{Id}$，另外注意到当指标集 $T$ 与 $T'$ 不交时，$D_TD_{T'}^\* = 0$，于是
> $$
> \begin{split}
> 2 \varepsilon & \geq \|A h\|_{2}=\left\|A D D^{*} h\right\|_{2} \\
> &= \left\|A \left(D_{T_{01}} + \sum_{j \geq 2} D_{T_{j}} \right) \left( D_{T_{01}}^{*} + \sum_{j \geq 2} D_{T_{j}}^{*} \right) h \right\|_{2} \\
> &= \left\|A \left(D_{T_{01}} D_{T_{01}}^{*} + \sum_{j \geq 2} D_{T_{j}} D_{T_{j}}^{*} \right) h \right\|_{2} \\
> & \geq \left\|A D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}-\sum_{j \geq 2}\left\|A D_{T_{j}} D_{T_{j}}^{*} h\right\|_{2}
> \end{split}
> $$
> 由于 $D_{T_{01}}$ 中至多有 $(s + M)$ 列来自 $D$，其余为非零列，于是 $\forall g \in \mathbb{R}^d$，有 $D_{T_{01}}g \in \Sigma_{M+s}$，特别地，$D_{T_{01}}(D_{T_{01}}^\*h) \in \Sigma_{M+s}$。类似可知，$\forall j \geq 2$，有 $D_{T_{j}} (D_{T_{j}}^{*}h) \in \Sigma_M$。因此，由于 $A$ 满足 $D$-RIP 条件，
> $$
> 2 \varepsilon  \geq \sqrt{1-\delta_{s+M}}\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}-\sqrt{1+\delta_{M}} \sum_{j \geq 2}\left\|D_{T_{j}} D_{T_{j}}^{*} h\right\|_{2}
> $$
> 由于 $D$ 为 tight frame，$D^*$ 为等距映射，从而 
> $$
> \| h \|_2 = \| D^* h \|_2 = \left \| \left( \sum_{j \geq 0} D_{T_j}^* \right) h \right \|_2 \geq  \left \| D_{T_k}^* h \right \|_2, \quad \forall k \geq 0
> $$
> 于是在算子范数意义下有 $\forall k \geq 0, \ \lVert D_{T_k} \rVert = \lVert D_{T_k}^* \rVert \leq 1$，因此，根据引理 2，
> $$
> \begin{split}
> 2 \varepsilon 
> & \geq \sqrt{1-\delta_{s+M}}\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}-\sqrt{1+\delta_{M}} \sum_{j \geq 2}\left\| D_{T_{j}}^{*} h\right\|_{2} \\
> & \geq \sqrt{1-\delta_{s+M}}\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}-\sqrt{\rho\left(1+\delta_{M}\right)}\left(\left\|D_{T_{0}}^{*} h\right\|_{2}+\eta\right) \\ 
> &\geq \sqrt{1-\delta_{s+M}}\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}-\sqrt{\rho\left(1+\delta_{M}\right)}\left(\left\|h\right\|_{2}+\eta\right)
> \end{split}
> $$

### 引理 4 (Bounding the error)

The error vector $h$ has norm that satisfies
$$
\| h \|_2^2 \leq \| h \|_2 \| D_{T_{01}} D_{T_{01}}^* h \|_2 + \rho  ( \| D_{T_0}^* h \|_2 + \eta)^2.
$$

> 由于$D^*$ 为等距映射，
> $$
> \begin{split}
> \|h\|_{2}^{2} 
> & = \left\|D^{*} h\right\|_{2}^{2}=\left\|D_{T_{01}}^{*} h\right\|_{2}^{2}+ \left\|D_{T_{01}^{c}}^{*} h\right\|_{2}^{2} \\
> & = \left\langle D_{T_{01}} D_{T_{01}}^{*} h, h\right\rangle+ \sum_{j \geq 2} \left\|D_{T_{j}^{c}}^{*} h\right\|_{2}^{2}\\
> & \leq \|h\|_{2}\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}+ \left(\sum_{j \geq 2} \left\|D_{T_{j}^{c}}^{*} h\right\|_{2} \right)^{2} \\
> & \leq \|h\|_{2}\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}+\rho\left(\left\|D_{T_{0}}^{*} h\right\|_{2}+\eta\right)^{2}.
> \end{split}
> $$
> 其中最后一个不等号利用了引理 2 的结论。

### 定理证明

> 注意到对任意的 $u, v \in \mathbb{R}$ 以及 $c > 0$，下面的不等式成立，
> $$
> uv \leq \frac{c u^2}{2} + \frac{v^2}{2c}.
> $$
> 假设 $c_1, c_2 > 0$ 为待定常数，在引理 3 的证明中，已经推导了 $\lVert D_{T_{0}}^*h \rVert_2 \leq \lVert h \rVert_2$，因此根据引理 4 的结论，
> $$
> \begin{split}
> \|h\|_{2}^{2} 
> & \leq \|h\|_{2}\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}+\rho\left(\left\|D_{T_{0}}^{*} h\right\|_{2}+\eta\right)^{2} \\
> & \leq\|h\|_{2}\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}+\rho\left(\left\|h\right\|_{2}+\eta\right)^{2} \\
> & \leq \frac{c_{1}\|h\|_{2}^{2}}{2}+\frac{\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}^{2}}{2 c_{1}} + \rho\left(\left\|h\right\|_{2}+\eta\right)^{2}  \\
> &=\frac{c_{1}\|h\|_{2}^{2}}{2}+\frac{\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}^{2}}{2 c_{1}}+\rho\|h\|_{2}^{2}+2 \rho \eta\|h\|_{2}+\rho \eta^{2}\\
> &\leq \frac{c_{1}\|h\|_{2}^{2}}{2}+\frac{\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}^{2}}{2 c_{1}}+\rho\|h\|_{2}^{2}+2 \rho\left(\frac{c_{2}\|h\|_{2}^{2}}{2}+\frac{\eta^{2}}{2 c_{2}}\right)+\rho \eta^{2}.
> \end{split}
> $$
> 整理之后并利用 $\forall u,v > 0$，有 $u^2 + v^2 \leq (u+v)^2$，
> $$
> \begin{split}
> \left(1-\frac{c_{1}}{2}-\rho-\rho c_{2}\right)\|h\|_{2}^{2} 
> &\leq \frac{1}{2 c_{1}}\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}^{2}+\left(\frac{\rho}{c_{2}}+\rho\right) \eta^{2} \\
> & \leq \left( \frac{1}{\sqrt{2 c_{1}}}\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}+\eta \sqrt {\frac{\rho}{c_{2}}+\rho} \right) ^{2}.
> \end{split}
> $$
> 因此当 $c_1, c_2$ 的选取满足 $1-{c_{1}}/{2}-\rho-\rho c_{2} \geq 0$ 时，有
> $$
> \left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2} \geq\|h\|_{2} \sqrt{2 c_{1}\left[1-\left(\frac{c_{1}}{2}+\rho+\rho c_{2}\right)\right]}-\eta \sqrt{2 c_{1}\left(\frac{\rho}{c_{2}}+\rho\right)}.
> $$
> 而根据引理 3 的结论，
> $$
> \sqrt{1-\delta_{s+M}}\left\|D_{T_{01}} D_{T_{01}}^{*} h\right\|_{2}-\sqrt{\rho\left(1+\delta_{M}\right)}\left(\|h\|_{2}+\eta\right) \leq 2 \varepsilon.
> $$
> 结合上述两条式子可以得到 $2\varepsilon \geq K_1 \lVert h \rVert_2 - K_2 \eta$，其中
> $$
> \begin{split}&K_{1}:=\sqrt{2 c_{1}\left(1-\delta_{s+M}\right)\left[1-\left(\frac{c_{1}}{2}+\rho+\rho c_{2}\right)\right]}-\sqrt{\rho\left(1+\delta_{M}\right)}\\&K_{2}:=\sqrt{2 c_{1}\left(1-\delta_{s+M}\right)\left(\rho / c_{2}+\rho\right)}-\sqrt{\rho\left(1+\delta_{M}\right)}.\end{split}
> $$

