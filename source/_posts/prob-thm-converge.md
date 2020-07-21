---
title: 随机变量的收敛性
date: 2020-05-25 22:58:32
tags: 
  - Random Variables
  - Convergence
categories: Probability
mathjax: true
---

随机变量收敛性有关定理及其证明。

<!--more-->

## Portmanteau 定理：依分布收敛的等价描述

对任意随机向量序列 $\left \{ \boldsymbol{X}_n \right \}$ 与随机向量 $\boldsymbol{X}$，下列命题等价：

+ **(i)** 对 $F_{\boldsymbol{X}}$ 的任意连续点 $\boldsymbol{x}$，有 $F_{\boldsymbol{X}_n}(\boldsymbol{x}) \to F_{\boldsymbol{X}}(\boldsymbol{x})$；
+ **(ii)** 对任意具有紧支撑的连续函数 $f: \mathbb{R}^k \to \mathbb{R}$，有 $\mathbb{E} f(\boldsymbol{X}_n) \to \mathbb{E} f(\boldsymbol{X})$；
+ **(iii)** 对任意有界连续函数 $f: \mathbb{R}^k \to \mathbb{R}$，有 $\mathbb{E} f(\boldsymbol{X}_n) \to \mathbb{E} f(\boldsymbol{X})$；
+ **(iv)** 对任意有界 Lipschitz 函数 $f: \mathbb{R}^k \to \mathbb{R}$，有 $\mathbb{E} f(\boldsymbol{X}_n) \to \mathbb{E} f(\boldsymbol{X})$；
+ **(v)** 对任意非负连续函数 $f: \mathbb{R}^k \to \mathbb{R}$，有 $\underset{n}{\lim \inf}_ \ \mathbb{E} f(\boldsymbol{X}_n) \geq \mathbb{E} f(\boldsymbol{X})$；
+ **(vi)** 对任意开集 $G \in \mathbb{R}^k$，有 $\underset{n}{\lim \inf} \ \mathbb{P} \left( \boldsymbol{X}_n \in G \right) \geq \mathbb{P} \left( \boldsymbol{X} \in G \right)$；
+ **(vii)** 对任意闭集 $F \in \mathbb{R}^k$，有 $\underset{n}{\lim \sup} \ \mathbb{P} \left( \boldsymbol{X}_n \in F \right) \leq \mathbb{P} \left( \boldsymbol{X} \in F \right)$；
+ **(viii)** 对任意满足 $\mathbb{P} \left( \boldsymbol{X} \in \partial B \right) = 0$ 的 Borel 集 $B \subset \mathbb{R}^k$，有 $\mathbb{P} \left( \boldsymbol{X}_n \in B \right) \to \mathbb{P} \left( \boldsymbol{X} \in B \right)$；

> **证明**：
>
> 对于 $\boldsymbol{X}$ 的第 $j$ 个分量 $X^{(j)}$，其边际分布 $F_{\boldsymbol{X}^{(j)}}$ 的连续点集合记为 $Q^{(j)}$，并令 $Q = Q^{(1)} \times \cdots \times Q^{(k)}$。由分布函数性质，$\mathbb{R} \backslash Q^{(j)}$ 中至多有可数个点。在下面的证明过程中，用类似下式的符号对 $\mathbb{R}^k$ 中长方体进行简记：
> $$
> (\boldsymbol{a}, \boldsymbol{b}] := ( a^{(1)}, b^{(1)} ] \times \cdots \times ( a^{(k)}, b^{(k)} ].
> $$
> 特别地，本证明关注那些端点满足 $\boldsymbol{a}, \boldsymbol{b} \in Q$ 的长方体，这是因为 $Q$ 中的点均为分布函数 $F_{\boldsymbol{X}}$ 的连续点：假设 $\boldsymbol{x} \in Q$，那么对于任意的 $\epsilon > 0$，由于 $x^{(j)}$ 为 $F_{\boldsymbol{X}^{(j)}}$ 的连续点，因此存在 $\delta^{(j)} > 0$ 使得对任意满足 $\left| y^{(j)} - x^{(j)} \right| < \delta^{(j)}$ 的 $y^{(j)}$，有
> $$
> \left | F_{\boldsymbol{X}^{(j)}} ( y^{(j)} ) - F_{\boldsymbol{X}^{(j)}} ( x^{(j)} ) \right | < \epsilon / k.
> $$
> 此时对任意的 $\boldsymbol{y} \in (\boldsymbol{x} - \boldsymbol{\delta}, \boldsymbol{x} + \boldsymbol{\delta})$，有
> $$
> \left | F_{\boldsymbol{X}} (\boldsymbol{y}) - F_{\boldsymbol{X}} (\boldsymbol{x}) \right | \leq \sum_{j=1}^k \left | F_{\boldsymbol{X}^{(j)}} ( y^{(j)} ) - F_{\boldsymbol{X}^{(j)}} ( x^{(j)} ) \right | < \epsilon,
> $$
> 于是 $F_{\boldsymbol{X}}$ 在 $\boldsymbol{x}$ 处连续。

### (i) $\Rightarrow$ (ii)

> 假设连续函数 $f$ 具有紧支撑 $C$，不失一般性，可以假设 $C$ 包含于长方体 $(\boldsymbol{a}, \boldsymbol{b}]$ 之中，并且 $\boldsymbol{a}, \boldsymbol{b} \in Q$。由于 $f$ 在紧集 $C$ 上连续，因此 $f$ 在 $C$ 上一致连续，进而也在 $(\boldsymbol{a}, \boldsymbol{b}]$ 上一致连续，即对任意 $\epsilon > 0$，存在 $\delta > 0$ 使得对任意的 $\boldsymbol{x}_1, \boldsymbol{x}_2 \in (\boldsymbol{a}, \boldsymbol{b}]$，只要 $\left \lVert \boldsymbol{x}_1 - \boldsymbol{x}_2 \right \rVert_2 < \delta$，就有 $| f(\boldsymbol{x}_1) - f(\boldsymbol{x}_2) | < \epsilon$。由 $Q$ 的稠密性，存在有限点列 $\boldsymbol{a}_i, \boldsymbol{b}_i \in Q$，$1 \leq i \leq L$，使得 $\left \lVert \boldsymbol{b}_i - \boldsymbol{a}_i \right \rVert_2 < \delta$，以及
> $$
> \bigcup_{i = 1}^{L} \ (\boldsymbol{a}_i, \boldsymbol{b}_i] = (\boldsymbol{a}, \boldsymbol{b}].
> $$
> 如果令
> $$
> f_{\epsilon}(\boldsymbol{x}) = \sum_{i = 1}^{L} f(\boldsymbol{b}_i) \boldsymbol{1}_{(\boldsymbol{a}_i, \boldsymbol{b}_i]} (\boldsymbol{x}),
> $$
> 那么对任意的 $\boldsymbol{x} \in \mathbb{R}^k$，有 $| f(\boldsymbol{x}) - f_{\epsilon}(\boldsymbol{x}) | < \epsilon$，因此
> $$
> \left | \mathbb{E} f(\boldsymbol{X}_n) - \mathbb{E} f_{\epsilon}(\boldsymbol{X}_n) \right | \leq \mathbb{E} | f(\boldsymbol{X}_n) - f_{\epsilon}(\boldsymbol{X}_n) | \leq \epsilon,
> $$
> 同理有
> $$
> \left | \mathbb{E} f(\boldsymbol{X}) - \mathbb{E} f_{\epsilon}(\boldsymbol{X}) \right | \leq \mathbb{E} | f(\boldsymbol{X}) - f_{\epsilon}(\boldsymbol{X}) | \leq \epsilon.
> $$
> 另外由于 $f_{\epsilon}$ 可以写成如下形式：
> $$
> f_{\epsilon}(\boldsymbol{x}) = \sum_{i = 1}^{L^\prime} \alpha_i \boldsymbol{1}_{(-\infty, \boldsymbol{c}_i]} (\boldsymbol{x}),
> $$
> 这里 $\boldsymbol{c}_i \in Q$，因此
> $$
> \begin{align*}
> \left | \mathbb{E} f_{\epsilon}(\boldsymbol{X}) - \mathbb{E} f_{\epsilon}(\boldsymbol{X}_n) \right | 
> & = \left | \sum_{i = 1}^{L^\prime} \alpha_i \mathbb{P} ( \boldsymbol{X} \leq \boldsymbol{c}_i) - \sum_{i = 1}^{L^\prime} \alpha_i \mathbb{P} ( \boldsymbol{X}_n \leq \boldsymbol{c}_i) \right | \\
> & \leq \sum_{i = 1}^{L^\prime} \left | \alpha_i \right | \cdot \left | \mathbb{P} ( \boldsymbol{X} \leq \boldsymbol{c}_i) - \mathbb{P} ( \boldsymbol{X}_n \leq \boldsymbol{c}_i) \right |.
> \end{align*}
> $$
> 注意 $\boldsymbol{c}_i$ 为分布函数 $F_{\boldsymbol{X}}$ 的连续点，于是 $\left | \mathbb{E} f_{\epsilon}(\boldsymbol{X}) - \mathbb{E} f_{\epsilon}(\boldsymbol{X}_n) \right | \to 0$。综上，可以推出
> $$
> \begin{align*}
> \left | \mathbb{E} f(\boldsymbol{X}) - \mathbb{E} f(\boldsymbol{X}_n) \right |
> & \leq \left | \mathbb{E} f(\boldsymbol{X}) - \mathbb{E} f_{\epsilon}(\boldsymbol{X}) \right | + \left | \mathbb{E} f_{\epsilon}(\boldsymbol{X}) - \mathbb{E} f_{\epsilon}(\boldsymbol{X}_n) \right | +\left | \mathbb{E} f_{\epsilon}(\boldsymbol{X}_n) - \mathbb{E} f(\boldsymbol{X}_n) \right | \\
> & \leq 2 \epsilon + \left | \mathbb{E} f_{\epsilon}(\boldsymbol{X}) - \mathbb{E} f_{\epsilon}(\boldsymbol{X}_n) \right |,
> \end{align*}
> $$
> 进一步地，有 $\underset{n}{\lim \sup} \left | \mathbb{E} f(\boldsymbol{X}) - \mathbb{E} f(\boldsymbol{X}_n) \right | \leq 2 \epsilon$，此时再由 $\epsilon > 0$ 的任意性，知 $\mathbb{E} f(\boldsymbol{X}_n) \to \mathbb{E} f(\boldsymbol{X})$ 成立。

### (ii) $\Rightarrow$ (iii)

> 假设连续函数 $f$ 满足 $\lVert f \rVert_{\infty} \leq M$。首先，对任意给定的 $\epsilon > 0$，存在 $R > 0$ 使得
> $$
> \mathbb{P} \left( \| \boldsymbol{X} \|_2 > R \right) < \epsilon / M.
> $$
> 由 Urysohn 引理，存在值域为 $[0, 1]$ 的连续函数 $h: \mathbb{R}^k \to \mathbb{R}$ 使得 $\| \boldsymbol{x} \|_2 \geq R + 1$ 时 $h(\boldsymbol{x}) = 0$ 以及 $\| \boldsymbol{x} \|_2 \leq R$ 时 $h(\boldsymbol{x}) = 1$。由于 $h$ 是具有紧支撑的连续函数，于是根据 **(ii)** 可知 $\mathbb{E} h(\boldsymbol{X}_n) \to \mathbb{E} h(\boldsymbol{X})$。注意到
> $$
> \mathbb{E} h(\boldsymbol{X}) \geq \mathbb{P} \left( \| \boldsymbol{X} \|_2 \leq R \right) > 1 - \epsilon / M,
> $$
> 以及
> $$
> \begin{align*}
> \left | \mathbb{E} f(\boldsymbol{X}_n) - \mathbb{E} (f h)(\boldsymbol{X}_n) \right | 
> & \leq \mathbb{E} \left ( \left | f(\boldsymbol{X}_n) \right | \cdot \left | 1- h(\boldsymbol{X}_n) \right | \right ) \leq M \mathbb{E} \left | 1- h(\boldsymbol{X}_n) \right | \\
> & = M \mathbb{E} \left ( 1- h(\boldsymbol{X}_n) \right ),
> \end{align*}
> $$
> 因此 $\underset{n}{\lim \sup} \left | \mathbb{E} f(\boldsymbol{X}_n) - \mathbb{E} (f\cdot h)(\boldsymbol{X}_n) \right | \leq \epsilon$。类似地，
> $$
> \begin{align*}
> \left | \mathbb{E} f(\boldsymbol{X}) - \mathbb{E} (f h)(\boldsymbol{X}) \right | 
> & \leq \mathbb{E} \left ( \left | f(\boldsymbol{X}) \right | \cdot \left | 1- h(\boldsymbol{X}) \right | \right ) \leq M \mathbb{E} \left | 1- h(\boldsymbol{X}) \right | \\
> & = M \mathbb{E} \left ( 1- h(\boldsymbol{X}) \right ) < \epsilon.
> \end{align*}
> $$
> 此外，$f h$ 也是具有紧支撑的连续函数，于是同样由 **(ii)** 可以推出 $\mathbb{E} (f h)(\boldsymbol{X}_n) \to \mathbb{E} (f h)(\boldsymbol{X})$。综上所述，由
> $$
> \begin{align*}
> \left | \mathbb{E} f(\boldsymbol{X}) - \mathbb{E} f(\boldsymbol{X}_n) \right |
> & \leq \left | \mathbb{E} f(\boldsymbol{X}) - \mathbb{E} (f h)(\boldsymbol{X}) \right | + \left | \mathbb{E} (f h)(\boldsymbol{X}) - \mathbb{E} (f h)(\boldsymbol{X}_n) \right | +\left | \mathbb{E} (f h)(\boldsymbol{X}_n) - \mathbb{E} f(\boldsymbol{X}_n) \right | \\
> & < \epsilon + \left | \mathbb{E} (f h)(\boldsymbol{X}) - \mathbb{E} (f h)(\boldsymbol{X}_n) \right | +\left | \mathbb{E} (f h)(\boldsymbol{X}_n) - \mathbb{E} f(\boldsymbol{X}_n) \right |,
> \end{align*}
> $$
> 可以推出 $\underset{n}{\lim \sup} \left | \mathbb{E} f(\boldsymbol{X}) - \mathbb{E} f(\boldsymbol{X}_n) \right | \leq 2 \epsilon$，此时再由 $\epsilon > 0$ 的任意性，知 $\mathbb{E} f(\boldsymbol{X}_n) \to \mathbb{E} f(\boldsymbol{X})$ 成立。

### (iii) $\Rightarrow$ (iv)

> 显然 (因为 Lipschitz 函数都是连续函数)。

### (iv) $\Rightarrow$ (vi)

> 记 $\boldsymbol{x} \in \mathbb{R}^k$ 到闭集 $F \subset \mathbb{R}^k$ 的距离为
> $$
> d_2(\boldsymbol{x}, F) := \min_{\boldsymbol{y} \in F} \| \boldsymbol{x} - \boldsymbol{y} \|_2.
> $$
> 对任意开集 $G \subset \mathbb{R}^k$，令
> $$
> f_m(\boldsymbol{x}) = \left( md_2(\boldsymbol{x}, G^c) \right) \wedge 1.
> $$
> 如果 $\boldsymbol{x} \in G$，那么当 $m$ 足够大之后，$f_m(\boldsymbol{x}) = 1$；反之，如果 $\boldsymbol{x} \notin G$，那么对任意的 $m \in \mathbb{Z}_+$，有 $f_m(\boldsymbol{x}) = 0$。因此，非负函数列 $\{f_m\}$ 满足 $f_m \uparrow \boldsymbol{1}_{G}$。另外注意到，对于固定的 $m$，
> $$
> | f_m(\boldsymbol{x}) - f_m(\boldsymbol{y}) | \leq m \| \boldsymbol{x} - \boldsymbol{y} \|_2
> $$
> 对任意的 $\boldsymbol{x}, \boldsymbol{y} \in \mathbb{R}^k$ 均成立，即 $f_m$ 为 Lipschitz 函数。因此结合 **(iv)** 可以推出，对任意 $m$，
> $$
> \underset{n}{\lim \inf} \ \mathbb{P} \left( \boldsymbol{X}_n \in G \right) = \underset{n}{\lim \inf} \ \mathbb{E}  \boldsymbol{1}_{G}(\boldsymbol{X}_n) \geq \underset{n}{\lim \inf} \ \mathbb{E} f_m(\boldsymbol{X}_n) = \mathbb{E} f_m(\boldsymbol{X}).
> $$
>
> 另外由单调收敛定理，
> $$
> \mathbb{E} f_m(\boldsymbol{X}) \to \mathbb{E} \boldsymbol{1}_{G}(\boldsymbol{X}) = \mathbb{P} \left( \boldsymbol{X} \in G \right).
> $$
> 因此下式成立：
> $$
> \underset{n}{\lim \inf} \ \mathbb{P} \left( \boldsymbol{X}_n \in G \right) \geq \mathbb{P} \left( \boldsymbol{X} \in G \right).
> $$

### (vi) $\Leftrightarrow$ (vii)

> 显然 (因为一个集合为开集当且仅当其补集为闭集)。

### (vi) $+$ (vii) $\Rightarrow$ (viii)

> 假设Borel 集 $B \subset \mathbb{R}^k$ 满足 $\mathbb{P} \left( \boldsymbol{X} \in \partial B \right) = 0$，由 **(vi)** 以及 **(vii)** 可知，
> $$
> \mathbb{P} \left( \boldsymbol{X} \in B^\circ \right) \leq \underset{n}{\lim \inf} \ \mathbb{P} \left( \boldsymbol{X}_n \in B^\circ \right) \leq \underset{n}{\lim \sup} \ \mathbb{P} \left( \boldsymbol{X}_n \in \bar{B} \right) \leq \mathbb{P} \left( \boldsymbol{X} \in \bar{B} \right).
> $$
> 由条件，$\mathbb{P} \left( \boldsymbol{X} \in \bar{B} \right) = \mathbb{P} \left( \boldsymbol{X} \in B^\circ \right)$，因此上式的不等号均可以换为等号，于是由
> $$
> \underset{n}{\lim \inf} \ \mathbb{P} \left( \boldsymbol{X}_n \in B^\circ \right) \leq\underset{n}{\lim \inf} \ \mathbb{P} \left( \boldsymbol{X}_n \in B \right) \leq\underset{n}{\lim \sup} \ \mathbb{P} \left( \boldsymbol{X}_n \in B \right) \leq\underset{n}{\lim \sup} \ \mathbb{P} \left( \boldsymbol{X}_n \in \bar{B} \right)
> $$
> 可知 $\lim_n \mathbb{P} \left( \boldsymbol{X}_n \in B \right)$ 存在并且
> $$
> \lim_n \mathbb{P} \left( \boldsymbol{X}_n \in B \right) = \mathbb{P} \left( \boldsymbol{X} \in B \right).
> $$

### (viii) $\Rightarrow$ (i)

> 假设 $\boldsymbol{x}$ 为分布函数 $F_{\boldsymbol{X}}$ 的任意连续点，那么 Borel 集 $B = (-\boldsymbol{\infty}, \boldsymbol{x}]$ 满足 $\mathbb{P} \left( \boldsymbol{X} \in \partial B \right) = 0$。这是因为对任意 $\epsilon > 0$，存在 $\boldsymbol{\delta} = (\delta^{(1)}, \ldots, \delta^{(k)}) > \boldsymbol{0}$ 使得对任意的 $\boldsymbol{y} \in (\boldsymbol{x} - \boldsymbol{\delta}, \boldsymbol{x} + \boldsymbol{\delta})$，有
> $$
> \left | F_{\boldsymbol{X}} (\boldsymbol{y}) - F_{\boldsymbol{X}} (\boldsymbol{x}) \right | < \epsilon.
> $$
> 从而
> $$
> \begin{align*}
> \mathbb{P} \left( \boldsymbol{X} \in \partial B \right) \leq F_{\boldsymbol{X}} (\boldsymbol{x}) - F_{\boldsymbol{X}} (\boldsymbol{x} - \boldsymbol{\delta} / 2) < \epsilon.
> \end{align*}
> $$
> 由 $\epsilon > 0$ 的任意性，可知 $\mathbb{P} \left( \boldsymbol{X} \in \partial B \right) = 0$ 成立。因此由 **(viii)** 可以推出：
> $$
> F_{\boldsymbol{X}_n}(\boldsymbol{x}) = \mathbb{P} \left( \boldsymbol{X}_n \in B \right) \to \mathbb{P} \left( \boldsymbol{X} \in B \right) = F_{\boldsymbol{X}}(\boldsymbol{x}).
> $$
