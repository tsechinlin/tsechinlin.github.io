---
title: Marčenko-Pastur Law for Sample Covariance Matrices - Proof by Stieltjes Transform
date: 2020-12-30 17:57:21
tags: 
  - M-P Law
  - Stieltjes Transform
categories: Random Matrix
mathjax: true
---

[Notes] <u>Spectral analysis of large dimensional random matrices</u> by Zhidong Bai & Jack W. Silverstein.

<!--more-->

**[Theorem]** Suppose that, for each $n \in \mathbb{Z}_+$, the entries of the $p \times n$ matrix $\mathbf{X}_n = \big ( x_{ij}^{(n)} \big )$ are independent complex variables with a common mean $\mu$ and variance $\sigma^2$. Assume that $p/n \to y \in (0, \infty)$ and that, for any $\eta > 0$,
$$
\lim _{n \rightarrow \infty} \frac{1}{n p} \sum_{j, k = 1}^n \mathbb{E} \left [ \left|x_{j k}^{(n)}\right|^{2} \cdot \mathbb{I}\left(\left|x_{j k}^{(n)}\right| \geq \eta \sqrt{n}\right) \right ]=0.
$$
Then, with probability one, the spectral distribution of $\mathbf{S}_n = \mathbf{X}_n \mathbf{X}_n^* / n$ weakly converges to the Marčenko-Pastur law with ratio index $y$ and scale index $\sigma$.

## Overview

仅需考虑 $\sigma = 1$ 的情形，利用矩阵简化之后得到如下假设：

+ $\left|x_{j k}^{(n)}\right| < \eta_n \sqrt{n}$，
+ $\mathbb{E} x_{j k}^{(n)} = 0$ 以及 $\operatorname{Var} \left [ x_{j k}^{(n)} \right ] = 1$。

考虑矩阵 $\mathbf{S}_n$ 谱分布的 Stieltjes 变换：

$$
s_n(z) = \frac{1}{p} \operatorname{tr} (\mathbf{S}_n - z \mathbf{I}_p)^{-1},
\quad z \in \mathbb{C}_+.
$$

为了得到所需结论，需要证明：对于任意固定的 $z \in \mathbb{C}_+$，当 $n \to \infty$ 时几乎处处有 $s_n(z) \to s(z)$，这里 $s(\cdot)$ 表示 $\sigma = 1$ 时 M-P 律的 Stieltjes 变换：
$$
s(z) = \frac{1 - z - y +  \sqrt{(1 - z - y)^{2} - 4 y z}}{2 yz}.
$$
以下证明中出现的量基本都与 $n$ 有关，但简便起见省去了上标 $^{(n)}$。

## Step 1 - Almost Sure Convergence of the Random Part

对于任意固定的 $z \in \mathbb{C}_+$，当 $n \to \infty$ 时几乎处处有 $s_n(z) - \mathbb{E} s_n(z) \to 0$。

> 固定 $n$，令 $\mathbf{x}_{k}$ 表示矩阵 $\mathbf{X}_n$ 的第 $k$ 列，用 $\widehat{\mathbb{E}}_k$ 表示给定 $\{ \mathbf{x}_{k+1}, \cdots, \mathbf{x}_{n} \}$ 的条件期望，那么
> $$
> \begin{align*}
> s_n(z) - \mathbb{E} s_n(z) 
> & = \widehat{\mathbb{E}}_0 s_n(z) - \widehat{\mathbb{E}}_n s_n(z) \\
> &= \frac{1}{p} \sum_{k = 1}^n \left [ \widehat{\mathbb{E}}_{k-1} \operatorname{tr} (\mathbf{S}_n - z \mathbf{I}_p)^{-1} - \widehat{\mathbb{E}}_{k} \operatorname{tr} (\mathbf{S}_n - z \mathbf{I}_p)^{-1}  \right ] 
> \triangleq \frac{1}{p} \sum_{k = 1}^n \gamma_k (z).
> \end{align*}
> $$
> 注意此处 $\gamma_n(z), \cdots, \gamma_1(z)$ 构成一组鞅差序列。
>
> 记 $\widehat{\mathbf{S}}_{k} := \mathbf{S}_n - \mathbf{x}_k \mathbf{x}_k^* / n$，注意到
> $$
> \widehat{\mathbb{E}}_{k-1} \operatorname{tr} \big ( \widehat{\mathbf{S}}_{k} - z \mathbf{I}_p \big )^{-1}
> = \widehat{\mathbb{E}}_{k} \operatorname{tr} \big ( \widehat{\mathbf{S}}_{k} - z \mathbf{I}_p \big )^{-1},
> $$
> 将其代入到 $\gamma_k (z)$ 的表达式，可以得到
> $$
> \begin{align*}
> \gamma_k (z) & = \widehat{\mathbb{E}}_{k-1} \operatorname{tr} (\mathbf{S}_n - z \mathbf{I}_p)^{-1} - \widehat{\mathbb{E}}_{k} \operatorname{tr} (\mathbf{S}_n - z \mathbf{I}_p)^{-1} \\
> & = \big ( \widehat{\mathbb{E}}_{k-1} - \widehat{\mathbb{E}}_{k} \big ) \left [ \operatorname{tr} (\mathbf{S}_n - z \mathbf{I}_p)^{-1} - \operatorname{tr} \big ( \widehat{\mathbf{S}}_{k} - z \mathbf{I}_p \big )^{-1} \right ].
> \end{align*}
> $$
> 而由于 $\widehat{\mathbf{S}}_{k}$ 为 Hermite 矩阵，因此根据引理 [MA-5]，有 $| \gamma_k(z) | \leq 2/v$。
>
> 此时利用鞅差序列的 Burkholder 不等式，可以推出
> $$
> \mathbb{E} \left | s_n(z) - \mathbb{E} s_n(z) \right |^4 
> = \frac{1}{p^4} \mathbb{E} \left | \sum_{k=1}^n \gamma_k(z) \right |^4
> \leq \frac{K_4}{p^4} \mathbb{E} \left [ \sum_{k=1}^n | \gamma_k(z) |^2 \right ]^2 
> \leq \frac{16 K_4 n^2}{p^4 v^2} 
> = O(n^{-2}).
> $$
> 因此根据引理，$s_n(z) - \mathbb{E} s_n(z) \to 0$ 几乎处处成立。

## Step 2 - Mean Convergence

对于任意固定的 $z \in \mathbb{C}_+$，当 $n \to \infty$ 时有 $\mathbb{E} s_n(z) \to s(z)$。

> 令 $\boldsymbol{\alpha}_{j}$ 表示矩阵 $\mathbf{X}_n$ 的第 $j$ 行，$\widetilde{\mathbf{X}}_{j}$ 表示 $\mathbf{X}_n$ 去掉第 $j$ 行之后的子矩阵，那么由引理，有
> $$
> s_{n}(z)
> = \frac{1}{p} \sum_{j=1}^{p} \left [ \frac{1}{n} \boldsymbol{\alpha}_{j}^{\top} \overline{\boldsymbol{\alpha}}_{j} - z - \frac{1}{n^2} \boldsymbol{\alpha}_{j}^{\top} \widetilde{\mathbf{X}}_{j}^{*}\left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1} \widetilde{\mathbf{X}}_{j} \overline{\boldsymbol{\alpha}}_{j} \right ]^{-1}
> $$
> 记 $y_n = p / n$，并设
> $$
> \varepsilon_{j} (z)
> = \frac{1}{n} \boldsymbol{\alpha}_{j}^{\top} \overline{\boldsymbol{\alpha}}_{j} - 1 - \frac{1}{n^2} \boldsymbol{\alpha}_{j}^{\top} \widetilde{\mathbf{X}}_{j}^{*}\left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1} \widetilde{\mathbf{X}}_{j} \overline{\boldsymbol{\alpha}}_{j} + y_n + y_n z \mathbb{E} s_n(z),
> $$
>
> 那么可以得到 $\mathbb{E} s_n(z)$ 关于的一元二次方程 $(\star)$：
>
> $$
> \mathbb{E} s_n(z) 
> = \frac{1}{p} \sum_{j=1}^{p} \mathbb{E} \left [ \frac{1}{1 - z - y_n - y_n z \mathbb{E} s_n(z) + \varepsilon_{j} (z)} \right ] = \frac{1}{1 - z - y_n - y_n z \mathbb{E} s_n(z)} + \delta_n (z),
> $$
> 其中
> $$
> \delta_n(z) = - \frac{1}{p} \sum_{j=1}^{p} \mathbb{E} \left [ \frac{\varepsilon_{j} (z)}{\big ( 1 - z - y_n - y_n z \mathbb{E} s_n(z) \big ) \big ( 1 - z - y_n - y_n z \mathbb{E} s_n(z) + \varepsilon_{j} (z) \big )} \right ]
> $$
> 求解方程关于 $\mathbb{E} s_n(z)$ 的一元二次方程 $(\star)$，可以得到
> $$
> \begin{align*}
> \widetilde{s}_{1}(z) & = \frac{1}{2 y_{n} z}\left[1-z-y_{n}+y_{n} z \delta_{n}(z) +\sqrt{\big (1-z-y_{n}-y_{n} z \delta_{n}(z) \big )^{2}-4 y_{n} z}\right] \\
> \widetilde{s}_{2}(z) & = \frac{1}{2 y_{n} z}\left[1-z-y_{n}+y_{n} z \delta_{n}(z) -\sqrt{\big(1-z-y_{n}-y_{n} z \delta_{n}(z) \big)^{2}-4 y_{n} z}\right]
> \end{align*}
> $$
>
> 对于任意固定的 $z \in \mathbb{C}_+$，若要证明 $\lim_{n \to \infty} \mathbb{E} s_n(z) = s(z)$，仅需证明
>
> + $\mathbb{E}s_n(z) = \widetilde{s}_1 (z)$，
> + $\lim_{n \to \infty} \delta_n(z) = 0$。

### Step 2.1

对于任意固定的 $u$，当 $v$ 足够大时总有 $\mathbb{E}s_n(z) = \widetilde{s}_1 (z)$。

> 对于固定的 $u$，注意到 $| s_n(z) | \leq 1/v$ 处处成立，因此当 $v \to \infty$ 时，有
> $$
> \left | z s_n (z) \right | 
> \leq \left | z \right | \cdot \left | s_n (z) \right | 
> \leq \frac{\sqrt{u^2 + v^2}}{v} \to 1.
> $$
> 这意味着对于足够大的 $v$，有 $\left | z \mathbb{E} s_n (z) \right | \leq \mathbb{E} \left | z  s_n (z) \right | \leq 2$。此时如果还有 $v \geq |1 - y_n| + 2 y_n$，那么
> $$
> \left | 1 - z - y_n - y_n z \mathbb{E} s_n (z) \right |
> \geq \left | z \right | - \left | 1 - y_n - y_n z \mathbb{E} s_n (z) \right |
> \geq |z| - \big ( \left | 1 - y_n \right | + 2 y_n \big ) 
> \geq 0,
> $$
> 根据 $(\star)$，此时
> $$
> \left | z \delta_n (z) \right | 
> \leq \left | z \mathbb{E} s_n (z) \right | + \frac{\left | z \right |}{\left | 1 - z - y_n - y_n z \mathbb{E} s_n (z) \right |}
> \leq 2 + \frac{\left | z \right |}{\left | z \right | - \left | 1 - y_n \right | - 2 y_n}
> $$
>
> 上式右端在 $v \to \infty$ 时趋于 $3$。总而言之，对于足够大的 $v$，有 $\left | z \delta_n (z) \right | \leq 4$。
>
> 另外注意到，对于 $\mathbb{R}$ 上的概率测度 $\mu$，如果 $\mu[0, \infty) = 1$，那么 $\mu$ 的 Stieltjes 变换 $s(\cdot)$ 满足：对于任意的 $y > 0$ 以及 $z = u + \mathrm{i} v \in \mathbb{C}_+$，
> $$
> \Im \big [ y + y z s(z) \big ] 
> = y \cdot \Im \left [ \int_{\mathbb{R}} \left ( 1 + \frac{z}{x - z} \right ) \mu (\mathrm{d} x) \right ]
> = y \int_{[0, \infty)} \frac{x v}{(x - u)^2 + v^2} \mu (\mathrm{d} x) 
> \geq 0.
> $$
>
> 考虑到 $\mathbf{S}_n = \mathbf{X}_n \mathbf{X}_n^* / n$ 非负定，将 $y_n$ 以及 $s_n$ 代入上式，得到
> $$
> \Im \big [ y_n + y_n z \mathbb{E} s_n(z) \big ] = \mathbb{E} \Im \big [ y_n + y_n z s_n(z) \big ] \geq 0, \quad \forall z \in \mathbb{C}_+.
> $$
> 这意味着对于任意固定的 $u$，当 $v$ 足够大时总有 $\mathbb{E} s_n(z) = \widetilde{s}_1 (z)$：这是由于如前所述，当 $v$ 足够大时，利用 $\left | z \delta_n (z) \right | \leq 4$ 以及平方根虚部非负的约定，有
> $$
> \Im \big [ y_n + y_n z \widetilde{s}_2(z) \big ] 
> \leq \frac{1}{2} \Im \big [ 1 - z + y_n + y_n z \delta_n (z) \big ] 
> \leq - \frac{v}{2} + \frac{y_n}{2} \left | z \delta_n (z) \right | 
> \leq - \frac{v}{2} + 2 y_n,
> $$
>
> 而上式右端在 $v \to \infty$ 时总会小于零。

### Step 2.2

$\mathbb{E} s_n(z) = \widetilde{s}_1 (z)$ 对于任意的 $z \in \mathbb{C}_+$ 成立。

> 首先，$\mathbb{E} s_n (z)$ 在 $\mathbb{C}_+$ 上是连续的。事实上，对于任意的 $z = u + \mathrm{i} v \in \mathbb{C}_+$ 以及满足 $|\Delta z| \leq v/2$ 的 $\Delta z \in \mathbb{C}$，处处有
> $$
> \begin{align*}
> \left | s_n(z + \Delta z) - s_n(z) \right | 
> & = \left | \frac{1}{p} \sum_{j=1}^p \frac{\Delta z}{(\lambda_j - z - \Delta z)(\lambda_j - z)} \right | \\
> & \leq \frac{1}{p} \sum_{j=1}^p \frac{| \Delta z |}{| \lambda_j - z - \Delta z | \cdot | \lambda_j - z |} 
> \leq \frac{2}{v^2} | \Delta z |.
> \end{align*}
> $$
> 换言之，当 $|\Delta z| \to 0$ 时，有
> $$
> \big | \mathbb{E} s_n(z + \Delta z) - \mathbb{E} s_n(z) \big |
> \leq \mathbb{E} \big | s_n(z + \Delta z) - s_n(z) \big |
> \leq \frac{2}{v^2} | \Delta z | \to 0.
> $$
> 因此，如果 $s_n(z) = \widetilde{s}_1 (z)$ 不是对于所有的 $z \in \mathbb{C}_+$ 成立，那么必定存在 $z_0 \in \mathbb{C}_+$ 使得 $\widetilde{s}_1 (z_0) = \widetilde{s}_2 (z_0)$。这意味着
> $$
> \mathbb{E} s_n(z_0) = \widetilde{s}_1 (z_0) = \widetilde{s}_2 (z_0) 
> = \frac{1 - z_0 - y_{n} + y_{n} z_0 \delta_{n}(z_0)}{2 y_{n} z_0}
> $$
> 结合 $(\star)$，可以推出
> $$
> \mathbb{E} s_n(z_0) = \frac{1 - z_0 - y_{n}}{y_{n} z_0} + \frac{1}{z_0 - 1 + y_n + y_n z_0 \mathbb{E} s_n(z_0)}
> $$
> 对于右端第二项，再度利用 $\Im \big [ y_n + y_n z_0 \mathbb{E} s_n(z_0) \big ] \geq 0$ 以及 $\Im z_0 > 0$，可知该项虚部为负。至于第一项
> $$
> \frac{1 - z_0 - y_{n}}{y_{n} z_0} = \frac{1 - y_{n}}{y_{n} z_0} - \frac{1}{y_n},
> $$
> 易知 $y_n \in (0, 1]$ 时该项虚部非正。换言之，当 $y_n \in (0, 1]$ 时，使得 $\widetilde{s}_1 (z_0) = \widetilde{s}_2 (z_0)$ 的 $z_0$ 不存在，否则 $\Im \mathbb{E} s_n(z_0) < 0$，这与 $\mathbb{E} s_n(z_0)$ 的虚部非负矛盾。
>
> 对于 $y_n \in (1, \infty)$ 的情形，首先注意到由上上式，有
> $$
> \big ( z_0 - 1 + y_n + y_n z_0 \mathbb{E} s_n(z_0) \big )^2 = y_n z_0
> $$
> 如前所述，左端括号内虚部大于 $0$，因此
> $$
> z_0 - 1 + y_n + y_n z_0 \mathbb{E} s_n(z_0) = \sqrt{y_n z_0} = \sqrt{y_n} \sqrt{z_0}
> $$
> 记 $\underline{s}_n (z)$ 表示矩阵 $\mathbf{X}^\* \mathbf{X} / n$ 谱分布的 Stieltjes 变换，注意到 $\mathbf{X}^\* \mathbf{X} / n$ 与 $\mathbf{S}_n = \mathbf{X}_n \mathbf{X}_n^\* / n$ 具有相同的非零特征根，因此
> $$
> s_{n} (z) = \frac{n}{p} \underline{s}_n(z) - \left ( 1 - \frac{n}{p} \right ) \frac{1}{z}
> $$
> 令 $z = z_0$ 并对两端取期望，得到
> $$
> \begin{align*}
> \mathbb{E} \underline{s}_n(z_0) 
> & = y_n \mathbb{E} s_n(z_0) + \frac{y_n - 1}{z_0} 
> = \frac{y_n - 1 + y_n z_0 \mathbb{E} s_n(z_0)}{z_0} \\
> & = \frac{\sqrt{y_n} \sqrt{z_0} - z_0}{z_0} 
> = \frac{\sqrt{y_n}}{\sqrt{z_0}} - 1
> \end{align*}
> $$
> 这显然是矛盾的，因为上式左端虚部非负，而右端虚部为负数。

### Step 2.3

对于任意的 $z \in \mathbb{C}_+$，当 $n \to \infty$ 时有 $\delta_n(z) \to 0$。

> 固定任意 $z \in \mathbb{C}_+$，对 $\delta_n (z)$ 作如下分解：
> $$
> \begin{align*}
> \delta_{n} (z)
> = & \ -\frac{1}{p} \sum_{j=1}^{p} \left [ \frac{\mathbb{E} \varepsilon_{j}(z)}{\left(1-z-y_{n}-y_{n} z \mathbb{E} s_{n}(z)\right)^{2}} \right] \\
> & \ +\frac{1}{p} \sum_{k=1}^{p} \mathbb{E} \left[ \frac{\varepsilon_{j}^{2}(z)}{\left(1-z-y_{n}-y_{n} z \mathbb{E} s_{n}(z)\right)^{2}\left(1-z-y_{n}-y_{n} z \mathbb{E} s_{n}(z)+\varepsilon_{j}(z)\right)}\right].
> \end{align*}
> $$
>
> 对于上式右端中的分母：
>
> **(1)** 如前所述，$\Im \big [ y_n + y_n z \mathbb{E} s_n(z) \big ] \geq 0$，因此
> $$
> \big | 1 - z - y_n - y_n z \mathbb{E} s_n(z) \big | 
> \geq - \Im \big [ 1 - z - y_n - y_n z \mathbb{E} s_n(z) \big ]
> \geq v.
> $$
> **(2)** 另一方面，注意到 $\boldsymbol{\alpha}_{j}^{\top} \overline{\boldsymbol{\alpha}}_{j} = \sum_{k=1}^n \left | x_{jk} \right |^2$ 为实数，并利用引理 [MA-1]，可以推出
> $$
> \begin{align*}
> & \ \big | 1 - z - y_n - y_n z \mathbb{E} s_n(z) + \varepsilon_j (z) \big | 
> \geq - \Im \big [ 1 - z - y_n - y_n z \mathbb{E} s_n(z) + \varepsilon_j (z) \big ] \\
> = & \ \Im \left [ z + \frac{1}{n^2} \boldsymbol{\alpha}_{j}^{\top} \widetilde{\mathbf{X}}_{j}^{*}\left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1} \widetilde{\mathbf{X}}_{j} \overline{\boldsymbol{\alpha}}_{j} - \frac{1}{n} \boldsymbol{\alpha}_{j}^{\top} \overline{\boldsymbol{\alpha}}_{j} \right ] \\
> = & \ v \left ( 1 + \frac{1}{n^2} \boldsymbol{\alpha}_{j}^{\top} \widetilde{\mathbf{X}}_{j}^{*} \left [ \left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*} - u \mathbf{I}_{p-1}\right)^{2} + v^2 \mathbf{I}_{p-1} \right ]^{-1} \widetilde{\mathbf{X}}_{j} \overline{\boldsymbol{\alpha}}_{j} \right ) \geq v.
> \end{align*}
> $$
> 由此可以得到
> $$
> | \delta_{n} (z) | \leq \frac{1}{p v^2} \sum_{j=1}^{p} \left | \mathbb{E} \varepsilon_{j}(z) \right | + \frac{1}{p v^3} \sum_{j=1}^{p} \mathbb{E} \left | \varepsilon_{j}(z) \right |^2.
> $$
> 对于第二项，对其作如下分解：用 $\widetilde{\mathbb{E}}_j$ 表示给定 $\{ \boldsymbol{\alpha}_{1}, \cdots, \boldsymbol{\alpha}_{j-1}, \boldsymbol{\alpha}_{j+1}, \cdots, \boldsymbol{\alpha}_{p} \}$ 的条件期望，那么
> $$
> \begin{align*}
> \mathbb{E} \big | \varepsilon_{j} (z) \big |^2 
> & = \mathbb{E} \big | \varepsilon_{j} (z) - \mathbb{E} \varepsilon_{j} (z) \big |^2 + \big | \mathbb{E} \varepsilon_{j} (z) \big |^2 \\
> & = \mathbb{E} \left | \varepsilon_{j} (z) - \widetilde{\mathbb{E}}_j \varepsilon_{j} (z) \right |^2 + \mathbb{E} \left | \widetilde{\mathbb{E}}_j \varepsilon_{j} (z) - \mathbb{E} \varepsilon_{j} (z) \right |^2 + 
> \big | \mathbb{E} \varepsilon_{j} (z) \big |^2,
> \end{align*}
> $$
> 这里最后一步基于：若随机变量 $X,Y$ 满足 $\mathbb{E} |X|, \mathbb{E} |XY| < \infty$，$X$ 为 $\mathcal{F}$-可测的以及 $\mathbb{E} [Y | \mathcal{F} ] = 0$，那么
> $$
> \mathbb{E} [XY] = \mathbb{E} \big [ \mathbb{E} [XY | \mathcal{F} ] \big ]
> = \mathbb{E} \big [ X \cdot \mathbb{E} [Y | \mathcal{F} ] \big ] = 0.
> $$
> 于是乎，接下来只需要给出 $\left | \mathbb{E} \varepsilon_{j}(z) \right |$，$\mathbb{E} \left | \varepsilon_{j} (z) - \widetilde{\mathbb{E}}_j \varepsilon_{j} (z) \right |^2$ 以及 $ \mathbb{E} \left | \widetilde{\mathbb{E}}_j \varepsilon_{j} (z) - \mathbb{E} \varepsilon_{j} (z) \right |^2$ 的收敛性。

#### Step 2.3.1

> 根据假设，
> $$
> \mathbb{E} \left[ \boldsymbol{\alpha}_{j}^{\top} \overline{\boldsymbol{\alpha}}_{j} \right] = \mathbb{E} \left[ \sum_{k=1}^n \left | x_{jk} \right |^2 \right] = n,
> \quad \text{ and } \quad
> \mathbb{E} \left[ \overline{\boldsymbol{\alpha}}_{j}\boldsymbol{\alpha}_{j}^{\top} \right] = \mathbf{I}_n
> $$
> 再注意到 $\boldsymbol{\alpha}_{j}$ 与 $\widetilde{\mathbf{X}}_{j}$ 之间的独立性，可以推出
> $$
> \begin{align*}
> \left | \mathbb{E} \varepsilon_{j} (z) \right |
> & = \left | - \frac{1}{n^2} \mathbb{E} \operatorname{tr} \left [ \boldsymbol{\alpha}_{j}^{\top} \widetilde{\mathbf{X}}_{j}^{*}\left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1} \widetilde{\mathbf{X}}_{j} \overline{\boldsymbol{\alpha}}_{j} \right ] + y_n + y_n z \mathbb{E} s_n(z) \right | \\
> & = \left | - \frac{1}{n} \mathbb{E} \operatorname{tr} \left [ \left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1} \frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*} \right ] + y_n + y_n z \mathbb{E} s_n(z) \right | \\
> & = \left | - \frac{1}{n} \operatorname{tr} \mathbf{I}_{p-1} - \frac{1}{n} \mathbb{E} \operatorname{tr} \left [ \left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1} z \mathbf{I}_{p-1} \right ] + y_n + y_n z \mathbb{E} s_n(z) \right | \\
> & \leq \frac{1}{n} + \frac{|z|}{n} \mathbb{E} \left | \operatorname{tr} (\mathbf{S}_n - z \mathbf{I}_p)^{-1} - \operatorname{tr} \left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1} \right | \\
> & \leq \frac{1}{n} + \frac{|z|}{nv},
> \end{align*}
> $$
> 这里最后一步应用了引理 [MA-3]。

#### Step 2.3.2

> 考虑矩阵
> $$
> \mathbf{A}_j(z) := \mathbf{I}_{n} - \frac{1}{n} \widetilde{\mathbf{X}}_{j}^{*}\left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1} \widetilde{\mathbf{X}}_{j}.
> $$
> 显然
> $$
> \varepsilon_{j} (z)
> = \frac{1}{n} \boldsymbol{\alpha}_{j}^{\top} \mathbf{A}_j(z) \overline{\boldsymbol{\alpha}}_{j} - 1 + y_n + y_n z \mathbb{E} s_n(z).
> $$
> 下面将 $\mathbf{A}_j(z)$ 的元素简记为 $\left ( a_{kl} \right )_{k,l = 1}^n$，那么
> $$
> \begin{align*}
> \varepsilon_{j} (z) - \widetilde{\mathbb{E}}_j \varepsilon_{j} (z)
> & = \frac{1}{n} \operatorname{tr} \left [ \mathbf{A}_j(z) \overline{\boldsymbol{\alpha}}_{j} \boldsymbol{\alpha}_{j}^{\top} \right ] - \frac{1}{n} \widetilde{\mathbb{E}}_j \operatorname{tr} \left [ \mathbf{A}_j(z) \overline{\boldsymbol{\alpha}}_{j} \boldsymbol{\alpha}_{j}^{\top} \right ] \\
> & = \frac{1}{n} \operatorname{tr} \left [ \mathbf{A}_j(z) \left ( \overline{\boldsymbol{\alpha}}_{j} \boldsymbol{\alpha}_{j}^{\top} - \mathbf{I}_n \right ) \right ] \\
> & = \frac{1}{n} \left[ \sum_{k=1}^{n} a_{kk} \left(\left|x_{jk} \right|^{2}-1\right)+\sum_{1 \leq k \neq l \leq n} a_{kl} x_{jk} \overline{x}_{jl}\right].
> \end{align*}
> $$
> 利用 $\mathbf{X}_n$ 各元素之间的独立性，经过简单计算可得
> $$
> \begin{align*}
> & \ \widetilde{\mathbb{E}}_j \left | \varepsilon_{j} (z) - \widetilde{\mathbb{E}}_j \varepsilon_{j} (z) \right |^2 \\
> = & \ \frac{1}{n^2} \left[ \sum_{k=1}^{n} | a_{kk} |^2 \mathbb{E} \left| \left|x_{jk} \right|^{2}-1\right|^2 + \sum_{1 \leq k \neq l \leq n} \left ( | a_{kl} |^2 \mathbb{E} |x_{jk}|^2 \mathbb{E} | x_{jl} |^2 + a_{kl} \overline{a}_{lk} \mathbb{E} x_{jk}^2 \mathbb{E} \overline{x}_{jl}^2 \right ) \right] \\
> \leq & \ \frac{1}{n^2} \left[ \sum_{k=1}^{n} | a_{kk} |^2 \left ( \mathbb{E} \left|x_{jk} \right|^{4}-1\right) + \sum_{1 \leq k \neq l \leq n} \left ( | a_{kl} |^2 + | a_{kl} \overline{a}_{lk} | \right ) \right] \\
> \leq & \ \frac{1}{n^2} \left[ \eta_n^2 n \sum_{k=1}^{n} | a_{kk} |^2 + 2 \sum_{k, l = 1}^{n} | a_{kl} |^2 \right].
> \end{align*}
> $$
> 这里倒数第二个不等号利用了 $\left| \mathbb{E} x_{jk}^2 \right | \leq \mathbb{E} |x_{jk}| ^2 = 1$，最后一个不等号则是使用了
> $$
> \mathbb{E} |x_{jk}| ^4 \leq \left ( \eta_n \sqrt{n} \right )^2 \mathbb{E} |x_{jk}| ^2 = \eta_n^2 n.
> $$
> 另一方面，假定 $\widetilde{\mathbf{X}}_{j} / \sqrt{n}$ 的 SVD 分解为 $\mathbf{U} \boldsymbol{\Sigma} \mathbf{V}^*$，此处 $\mathbf{U} \in \mathbb{C}^{(p-1) \times (p-1)}$ 而 $\mathbf{V} \in \mathbb{C}^{n \times n}$，其中奇异值为 $\sigma_1 \geq \sigma_2 \geq \cdots \geq \sigma_{p \wedge n}$。如果 $p < n$，则额外定义 $\sigma_{p+1} = \cdots = \sigma_{n} = 0$。此时可计算出
> $$
> \mathbf{A}_j(z) = \mathbf{V} \operatorname{diag} \left ( \frac{-z}{\sigma_1^2 - z}, \cdots, \frac{-z}{\sigma_n^2 - z} \right ) \mathbf{V}^*,
> $$
> 因此有
> $$
> | a_{kk} |
> \leq \max_{1 \leq l \leq n} \left | \frac{-z}{\sigma_l^2 - z} \right |
> \leq \max_{1 \leq l \leq n} \frac{|z|}{\Im [ z - \sigma_l^2 ]}
> \leq \frac{|z|}{v}，
> $$
> 以及
> $$
> \begin{align*}
> \sum_{k, l = 1}^{n} | a_{kl} |^2 
> & = \operatorname{tr} \left [ \mathbf{A}_j(z) \mathbf{A}^*_j(z) \right ] = \sum_{l=1}^n \frac{|z|^2}{(\sigma_l^2 - z)(\sigma_l^2 - \overline{z})} \\
> & = \sum_{l=1}^n \frac{|z|^2}{(\sigma_l^2 - u)^2 + v^2} \leq \frac{n |z|^2}{v^2}.
> \end{align*}
> $$
> 综上所述，
> $$
> \mathbb{E} \left | \varepsilon_{j} (z) - \widetilde{\mathbb{E}}_j \varepsilon_{j} (z) \right |^2 
> = \mathbb{E} \ \widetilde{\mathbb{E}}_j \left | \varepsilon_{j} (z) - \widetilde{\mathbb{E}}_j \varepsilon_{j} (z) \right |^2 \leq \frac{\eta_n^2 |z|^2}{v^2} + \frac{2 |z|^2}{n v^2}.
> $$

#### Step 2.3.3

> 首先注意到
> $$
> \begin{align*}
> \widetilde{\mathbb{E}}_j \varepsilon_{j} (z) - \mathbb{E} \varepsilon_{j} (z)
> & = \frac{1}{n} \widetilde{\mathbb{E}}_j \operatorname{tr} \left [ \mathbf{A}_j(z) \overline{\boldsymbol{\alpha}}_{j} \boldsymbol{\alpha}_{j}^{\top} \right ] - \frac{1}{n} \mathbb{E} \operatorname{tr} \left [ \mathbf{A}_j(z) \overline{\boldsymbol{\alpha}}_{j} \boldsymbol{\alpha}_{j}^{\top} \right ] \\
> & = \frac{1}{n} \operatorname{tr} \mathbf{A}_j(z) - \frac{1}{n} \mathbb{E} \operatorname{tr} \mathbf{A}_j(z),
> \end{align*}
> $$
> 其中
> $$
> \begin{align*}
> \operatorname{tr} \mathbf{A}_j(z) 
> & = \operatorname{tr} \mathbf{I}_n - \operatorname{tr} \left [ \frac{1}{n} \widetilde{\mathbf{X}}_{j}^{*}\left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1} \widetilde{\mathbf{X}}_{j} \right ] \\
> &= - \operatorname{tr} \left [ \left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1} z \mathbf{I}_{p-1} \right ]
> = - z \operatorname{tr} \left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1}
> \end{align*}
> $$
> 为了给出 $\left | \widetilde{\mathbb{E}}_j \varepsilon_{j} (z) - \mathbb{E} \varepsilon_{j} (z) \right |$ 的上界，可以利用类似于 Step 1 的鞅差分解方法。
>
> 简便起见，此处以 $j = 1$ 为例，用 $\check{\mathbb{E}}_i$ 表示给定 $\{ \boldsymbol{\alpha}_{i+1}, \cdots, \boldsymbol{\alpha}_{p} \}$ 的条件期望，并记
> $$
> \check{\mathbf{X}}_{i} = 
> \begin{bmatrix}
> \boldsymbol{\alpha}_{2}, \cdots, \boldsymbol{\alpha}_{i-1}, \boldsymbol{\alpha}_{i+1}, \cdots, \boldsymbol{\alpha}_{p}
> \end{bmatrix}^{\top},
> $$
> 即 $\mathbf{X}_n$ 去掉第 $j=1$ 行以及第 $i$ 行之后得到的子矩阵。此时有
> $$
> \begin{align*}
> \widetilde{\mathbb{E}}_1 \varepsilon_{1} (z) - \mathbb{E} \varepsilon_{1} (z) 
> & = \frac{1}{n} \operatorname{tr} \mathbf{A}_1(z) - \frac{1}{n} \mathbb{E} \operatorname{tr} \mathbf{A}_1(z) \\
> & = \frac{1}{n} \check{\mathbb{E}}_1 \operatorname{tr} \mathbf{A}_1(z) - \frac{1}{n} \check{\mathbb{E}}_p \operatorname{tr} \mathbf{A}_1(z) \\
> &= -\frac{z}{n} \sum_{i = 2}^p \left [ \big ( \check{\mathbb{E}}_{i-1} - \check{\mathbb{E}}_{i} \big ) \operatorname{tr} \left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1} \right ]
> \triangleq -\frac{z}{n} \sum_{i = 1}^p \gamma_i (z).
> \end{align*}
> $$
> 注意到对于所有的 $i = 2, \cdots, p$，
> $$
> \check{\mathbb{E}}_{i-1} \operatorname{tr} \left(\frac{1}{n} \check{\mathbf{X}}_{i} \check{\mathbf{X}}_{i}^{*} - z \mathbf{I}_{p-2}\right)^{-1}
> = \check{\mathbb{E}}_i \operatorname{tr} \left(\frac{1}{n} \check{\mathbf{X}}_{i} \check{\mathbf{X}}_{i}^{*} - z \mathbf{I}_{p-2}\right)^{-1}
> $$
> 因此
> $$
> \gamma_i (z) = \big ( \check{\mathbb{E}}_{i-1} - \check{\mathbb{E}}_i \big ) \left [ \operatorname{tr} \left(\frac{1}{n} \widetilde{\mathbf{X}}_{j} \widetilde{\mathbf{X}}_{j}^{*}-z \mathbf{I}_{p-1}\right)^{-1} - \operatorname{tr} \left(\frac{1}{n} \check{\mathbf{X}}_{i} \check{\mathbf{X}}_{i}^{*} - z \mathbf{I}_{p-2}\right)^{-1} \right ].
> $$
> 再度利用引理 [MA-3]，可以得到 $|\gamma_i (z)| \leq 2/v$。因此根据鞅差序列的 Burkholder 不等式，可以得到
> $$
> \mathbb{E} \left | \widetilde{\mathbb{E}}_1 \varepsilon_{1} (z) - \mathbb{E} \varepsilon_{1} (z) \right |^2 
> = \frac{|z|^2}{n^2} \mathbb{E} \left | \sum_{i=2}^p \gamma_i(z) \right |^2
> \leq \frac{K_2 |z|^2}{n^2} \mathbb{E} \left [ \sum_{i=2}^p | \gamma_i(z) |^2 \right ] 
> \leq \frac{K_2 |z|^2 p}{v^2 n^2} .
> $$

