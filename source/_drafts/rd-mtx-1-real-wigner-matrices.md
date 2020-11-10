---
title: rd-mtx-1-real-wigner-matrices
tags: 
  - Eigenvalue
  - Wigner Matrix
  - Semicircle Law
categories: Random Matrix
mathjax: true
---

阅读笔记：<u>Matrix analysis</u> [Horn, Roger A., and Charles R. Johnson].

<!--more-->

## 实 Wigner 矩阵

考虑两族独立同分布的实随机变量列：$\{ Z_{i, j} \}_{1 \leq i < j}$ 以及 $\{ Y_{i} \}_{i \geq 1}$，使得

+ $\mathbb{E} Z_{1,2} = \mathbb{E} Y_{1} = 0$，
+ $\mathbb{E} Z_{1,2}^2 = 1$。

对每个正整数 $N \geq 1$，定义 $N$ 维实对称矩阵 $X_N$，使得
$$
X_N (j, i) = X_N (i, j) = 
\begin{cases}
Z_{i,j} / \sqrt{N}, & \text{ if } i < j, \\
Y_i / \sqrt{N}, & \text{ if } i = j.
\end{cases}
$$
称 $X_N$ 为 **$N$ 维实 Wigner 矩阵 (real Wigner matrix)**。实 Wigner 矩阵列 $\{X_N\}_{N \geq 1}$ 即为本文的讨论对象。

用 $\{\lambda_i^N \}_{1 \leq i \leq N}$ 表示实 Wigner 矩阵 $X_N$ 的特征值，其中 $\lambda_1^N \leq \lambda_2^N \leq \cdots \leq \lambda_N^N$。定义 $X_N$ 特征值的**经验分布 (empirical distribution)** 为
$$
L_N = \frac{1}{N} \sum_{i=1}^N \delta_{\lambda_{i}^N}.
$$

定义**半圆律 (semicircle law)** 为实直线 $\mathbb{R}$ 上的概率分布 $\sigma(x) dx$，其中 $\sigma(x)$ 为密度函数 
$$
\sigma(x) = \frac{1}{2\pi} \sqrt{4 - x^2} \mathbf{1}_{|x| \leq 2}.
$$
定义半圆律的 $k$ 阶矩为 $m_k:= \langle \sigma, x^k \rangle$，那么对所有的 $k \geq 1$，有
$$
m_{2k} = C_k, \quad m_{2k + 1} = 0,
$$
其中 $C_k$ 为 Catalan 数。

## Catalan 数及其组合解释

对 $k \in \mathbb{N}$, 定义 $k$ 阶 **Catalan 数 (Catalan numbers)** 为
$$
C_k = \frac{1}{k+1} {2k \choose k} = \frac{(2k)!}{(k+1)! k!}.
$$

+ 递推公式：
  $$
  C_{k} = \sum_{j = 1}^{k} C_{k - j} C_{j - 1}, \quad \forall k \geq 1.
  $$
+ 生成函数：对 $|z| < 1/4$，有
  $$
  G(z) = \sum_{k=0}^\infty C_k z^k = \frac{1 - \sqrt{1 - 4z}}{2z}.
  $$

### Dyck 路径

Catalan 数 $C_k$ 计算了**长度为 $2k$ 的 Dyck 路径**的数量：

称整数序列 $\{ S_n \}_{0 \leq n \leq l}$ 为长度为 $l$ 的 **Bernoulli 游走 (Bernoulli walk)**，如果

+ $S_0 = 0$，
+ 对所有的 $0 \leq n \leq l-1$ 都有 $|S_{n+1} - S_n| = 1$。

给定 Bernoulli 游走 $\{ S_n \}_{0 \leq n \leq l}$，称其为一条 **Dyck 路径 (Dyck path)**，如果

+ 对所有的 $0 \leq n \leq l$ 都有 $S_n \geq 0$。
+ $S_l = 0$。

### RT-树

Catalan 数 $C_k$ 计算了**边数为 $k$ 的 RT-树**的数量：

**RT-树 (rooted planar tree)** 是一个无环平面图，以某个特定顶点作为根，并且对每个顶点，其后代节点被赋予特定顺序。一个递归式的定义如下：

+ 仅有一个顶点的无环平面图是 RT-树。
+ 如果 $T_1, \ldots, T_k$ 是一列有序的 RT-树，其根分别为 $r_1, \ldots, r_k$，那么可以将一个未出现过的顶点 $r$ 作为根，并按顺序将 $r_i$ 作为 $r$ 的后代节点，此时，得到的平面图 $T$ 是 RT-树。

### 非交叉划分

Catalan 数 $C_k$ 计算了 **$\mathscr{K}_{k}$ 的非交叉划分**的数量：

集合 $\mathscr{K}_{k} = \{ 1, \ldots, k \}$ 的一个划分称为**交叉的 (crossing)**，如果存在 $a, b, c, d \in [k]$ 使得 $a < b < c <d$ 并且 $a, c$ 属于一个分区而 $b, d$ 属于另一个分区。$\mathscr{K}_{k}$ 的一个划分如果不出现上述这种交叉的情况，就称其为**非交叉的 (non-crossing)**。

## Wigner 定理

对实 Wigner 矩阵列 $\{X_N\}_{N \geq 1}$，如果对所有的 $k \geq 1$ 都有
$$
r_{k}:=\max \left(E\left|Z_{1,2}\right|^{k}, E\left|Y_{1}\right|^{k}\right)<\infty,
$$
那么其特征值经验分布列 $\{L_N\}_{N \geq 1}$ **依概率弱收敛 (converges weakly in probability)** 于半圆律，换言之，对任意 $\varepsilon > 0$ 以及 $\mathbb{R}$ 上的实值有界连续函数 $f \in C_b(\mathbb{R})$，有
$$
\lim_{N \to \infty} \mathbb{P} \left( | \langle L_N, f \rangle - \langle \sigma, f \rangle | > \varepsilon \right) = 0.
$$

### 证明架构

定义概率分布 $\bar{L}_N = \mathbb{E} L_N$，作为 $C_b(\mathbb{R})$ 上的线性泛函，其满足
$$
\langle \bar{L}_N, f \rangle = \mathbb{E} \langle L_N, f \rangle, \quad \forall f \in C_b(\mathbb{R}).
$$
记 $m_k^N = \langle \bar{L}_N, x^k \rangle$ 为分布 $\bar{L}_N$ 的 $k$ 阶矩。

**引理 1**：对任意 $k \in \mathbb{N}$，有
$$
\lim_{N \to \infty} m_k^N = m_k.
$$
**引理 2**：对任意 $k \in \mathbb{N}$ 以及 $\varepsilon > 0$，有
$$
\lim_{N \to \infty} \mathbb{P} \left( | \langle \bar{L}_N, x^k \rangle - \langle L_N, x^k \rangle | > \varepsilon \right) = 0.
$$

**引理 3**：对任意常数 $\varepsilon > 0$ 以及 $B > 4$，有
$$
\lim_{N \to \infty} \mathbb{P}\left(\langle L_{N},|x|^{k} \mathbf{1}_{|x|>B}\rangle>\varepsilon\right) = 0, \quad \forall k \in \mathbb{N}.
$$

### 引理 1 证明

$$
\begin{equation}
	\bar{T}_{\mathbf{i}, \mathbf{i}^\prime}^N 
	:= \mathbb{E} \left[ T_{\mathbf{i}}^N T_{\mathbf{i}^\prime}^N \right] 
	- \mathbb{E} T_{\mathbf{i}}^N \mathbb{E} T_{\mathbf{i}^\prime}^N
\end{equation}
$$

$$
T_{\mathbf{i}}^N := \mathbb{E} \left[ X_N(i_1, i_2) X_N(i_2, i_3) \cdots X_N(i_{k-1}, i_k) X_N(i_k, i_1) \right]
$$

$$
\bar{T}_{\mathbf{i}}^N := \mathbb{E} T_{\mathbf{i}}^N
$$

### 引理 2 证明

注意到
$$
\left \langle L_N, x^k \right \rangle = \frac{1}{N} \sum_{i=1}^N \left( \lambda_{i}^{N} \right)^k = \frac{1}{N} \operatorname{tr} \left( X^k \right) = \frac{1}{N} \sum_{\mathbf{i}} T_{\mathbf{i}}^N
$$

$$
\mathbb{E} \left [ \left \langle L_N, x^k \right \rangle ^2 \right ] - \left \langle \bar{L}_N, x^k \right \rangle^2 
= \frac{1}{N^2} \sum_{\mathbf{i}, \mathbf{i}^\prime} \bar{T}_{\mathbf{i}, \mathbf{i}^\prime}^N .
$$



$$
\begin{align*}
\bar{T}_{\mathbf{i}, \mathbf{i}^{\prime}}^{N}
= & \ \frac{1}{N^{k}} \left[
\prod_{e \in E^c ( a_{\mathbf{i}, \mathbf{i}^{\prime}} )} \mathbb{E}  Z_{1,2}^{N(e, a_{\mathbf{i}, \mathbf{i}^{\prime}} )}
\prod_{e \in E^s ( a_{\mathbf{i}, \mathbf{i}^{\prime}} )} Y_{1}^{N(e, a_{\mathbf{i}, \mathbf{i}^{\prime}} )} \right. \\
& - \left. \prod_{e \in E^c ( w_{\mathbf{i}} )} \mathbb{E}  Z_{1,2}^{N(e, w_{\mathbf{i}} )}
\prod_{e \in E^s ( w_{\mathbf{i}} )} \mathbb{E}  Y_{1}^{N(e, w_{\mathbf{i}} )}
\prod_{e \in E^c ( w_{\mathbf{i}^{\prime}} )} \mathbb{E}  Z_{1,2}^{N(e, w_{\mathbf{i}^{\prime}} )}
\prod_{e \in E^s ( w_{\mathbf{i}^{\prime}} )} \mathbb{E}  Y_{1}^{N(e, w_{\mathbf{i}^{\prime}} )}
\right]
\end{align*}
$$


因此，$\bar{T}_{\mathbf{i}, \mathbf{i}^{\prime}}^{N} = 0$ 除非

+ 对所有的 $e \in E ( a_{\mathbf{i}, \mathbf{i}}^{\prime} )$，有 $N(e, a_{\mathbf{i}, \mathbf{i}}^{\prime} ) \geq 2$。
+ $E ( w_{\mathbf{i}} ) \cap E ( w_{\mathbf{i}^{\prime}} )$ 非空。

$$
\begin{align*}
\mathbb{E} \left [ \left \langle L_N, x^k \right \rangle ^2 \right ] - \left \langle \bar{L}_N, x^k \right \rangle^2 
= & \ \sum_{t=1}^{2k} \frac{P_{N, t}}{N^{k+2}} \sum_{a = (w, w^\prime) \in \mathcal{A}_{k, t}} \left[ \prod_{e \in E^c ( a )} \mathbb{E}  Z_{1,2}^{N(e, a )}
\prod_{e \in E^s ( a )} Y_{1}^{N(e, a )} \right. \\
& - \left. \prod_{e \in E^c ( w )} \mathbb{E}  Z_{1,2}^{N(e, w )}
\prod_{e \in E^s ( w )} \mathbb{E}  Y_{1}^{N(e, w )}
\prod_{e \in E^c ( w^{\prime} )} \mathbb{E}  Z_{1,2}^{N(e, w^{\prime} )}
\prod_{e \in E^s ( w^{\prime} )} \mathbb{E}  Y_{1}^{N(e, w^{\prime} )}
\right]
\end{align*}
$$

由于 $t < k+2$ 时，${P_{N, t}} / {N^{k+2}} \to 0$，因此只需证明 $t \geq k+2$ 时，$\mathcal{A}_{k, t}$ 为空集。

如果 $a = (w, w^\prime) \in \mathcal{A}_{k, t}$，那么 $G(a)$ 为连通图，因为 $E ( w ) \cap E ( w^{\prime} ) \not= \varnothing$。注意 $G(a)$ 有 $t$ 个顶点以及至多 $k$ 条边 (因为每条边至少被通过两次)，所以除非 $t - 1 \leq k$，否则这样的图不存在，即 $\mathcal{A}_{k, t}$ 为空集。

### 引理 3 证明

根据 Chebyshev 不等式，对任意实值随机变量 $X$，有 $\mathbb{P}\left(|X| >\varepsilon\right) \leq \mathbb{E}|X| / \varepsilon$，于是
$$
\begin{align*}
\mathbb{P}\left(\langle L_{N},|x|^{k} \mathbf{1}_{|x|>B}\rangle>\varepsilon\right) 
& \leq \frac{1}{\varepsilon} \mathbb{E} \langle L_{N},|x|^{k} \mathbf{1}_{|x|>B} \rangle \\
& \leq \frac{1}{\varepsilon B^k} \mathbb{E} \langle L_{N},|x|^{2k} \mathbf{1}_{|x|>B} \rangle \\
& \leq \frac{1}{\varepsilon B^k} \langle\bar{L}_{N}, x^{2 k} \rangle.
\end{align*}
$$

对上式两端同时取上极限，并利用**引理 1**，可以推出
$$
\underset{N \to \infty}{\lim \sup} \ \mathbb{P}\left(\langle L_{N},|x|^{k} \mathbf{1}_{|x|>B}\rangle>\varepsilon\right) \leq \lim_{N \to \infty} \frac{1}{\varepsilon B^k} \langle\bar{L}_{N}, x^{2 k} \rangle = \frac{1}{\varepsilon B^k} \langle \sigma, x^{2 k} \rangle = \frac{C_k}{\varepsilon B^k}.
$$
注意到对所有的 $k \in \mathbb{N}$ 都有 $C_k \leq 4^k$，因此如果 $B > 4$，那么上式右端关于 $k$ 就是递减趋于 $0$ 的。再注意到上式左端事实上关于 $k$ 是递增的，因此，
$$
\lim_{N \to \infty} \mathbb{P}\left(\langle L_{N},|x|^{k} \mathbf{1}_{|x|>B}\rangle>\varepsilon\right) = 0, \quad \forall k \in \mathbb{N}.
$$

### Wigner 定理证明

固定常数 $B > 4$，例如 $B = 5$。对任意 $\mathbb{R}$ 上的实值有界连续函数 $f \in C_b(\mathbb{R})$，根据 Weierstrass 逼近定理，存在多项式 $Q_{\varepsilon}(x) = \sum_{k=0}^K c_k x^k$ 使得
$$
| Q_\varepsilon (x) - f(x) | \leq {\varepsilon} / {6}, \quad \forall -B \leq x \leq B.
$$
注意到 $\sigma(x)$ 的支撑位于 $[-B, B]$ 内，于是
$$
\begin{align*}
& \ \langle L_N, f \rangle - \langle \sigma, f \rangle \\
= & \ \langle L_N, f \cdot \mathbf{1}_{|x| \leq B} \rangle - \langle \sigma, f \cdot \mathbf{1}_{|x| \leq B} \rangle + \langle L_N, f \cdot \mathbf{1}_{|x| > B} \rangle \\
= & \ \langle L_N, (f - Q_{\varepsilon}) \cdot \mathbf{1}_{|x| \leq B} \rangle - \langle L_N, Q_{\varepsilon} \cdot \mathbf{1}_{|x| > B} \rangle + \left[ \langle L_N, Q_{\varepsilon} \rangle - \langle \bar{L}_N, Q_{\varepsilon} \rangle \right] \\
& + \left[ \langle \bar{L}_N, Q_{\varepsilon} \rangle - \langle \sigma, Q_{\varepsilon} \rangle \right] + \langle \sigma, (Q_{\varepsilon} - f) \cdot \mathbf{1}_{|x| \leq B} \rangle + \langle L_N, f \cdot \mathbf{1}_{|x| > B} \rangle \\
:= & \ I_1 - I_2 + I_3 + I_4 + I_5 + I_6.
\end{align*}
$$
其中

+ 由于 $|f - Q_{\varepsilon}| \cdot \mathbf{1}_{|x| \leq B} \leq \mathbf{1}_{|x| \leq B}$，于是
  $$
  |I_1| \leq \frac{\varepsilon}{6} \langle L_N, \mathbf{1}_{|x| \leq B} \rangle \leq \frac{\varepsilon}{6}, \quad \forall N\in \mathbb{N}.
  $$

+ 再次利用**引理 3**，可以推出
  $$
  \mathbb{P} \left( |I_2| > \varepsilon / 6 \right) = \mathbb{P} \left( | \langle L_N, Q_{\varepsilon} \cdot \mathbf{1}_{|x| > B} \rangle | > \varepsilon / 6\right) \to 0. \quad (N \to \infty)
  $$

+ 根据**引理 2**，则有
  $$
  \mathbb{P} \left( |I_3| > \varepsilon / 6 \right) = \mathbb{P} \left( |\langle L_N, Q_{\varepsilon} \rangle - \langle \bar{L}_N, Q_{\varepsilon} \rangle | > \varepsilon / 6 \right) \to 0. \quad (N \to \infty)
  $$

+ 根据**引理 1**，
  $$
  \langle \bar{L}_N, Q_{\varepsilon} \rangle = \sum_{k=0}^K c_k m_k^N \to \sum_{k=0}^K c_k m_k = \langle \sigma, Q_{\varepsilon} \rangle. \quad (N \to \infty)
  $$
  因此当 $N$ 足够大时，$|I_4| \leq \varepsilon / 6$.

+ 再次利用 $\sigma(x)$ 的支撑位于 $[-B, B]$ 内这一事实，可以得到
  $$
  |I_5| = |\langle \sigma, (Q_{\varepsilon} - f) \cdot \mathbf{1}_{|x| \leq B} \rangle| \leq |\langle \sigma, \varepsilon \mathbf{1}_{|x| \leq B} \rangle| = \varepsilon.
  $$

+ 最后，由于 $f$ 是有界的，因此 $0 < 1 + \lVert f \rVert_{\infty} < \infty$，于是根据**引理 3** 中的 $k = 0$ 情形，可以得到
  $$
  \mathbb{P} \left( |I_6| > \varepsilon / 6 \right) \leq \mathbb{P} \left( \langle L_N, \mathbf{1}_{|x| > B} \rangle > \frac{\varepsilon}{6(1 + \lVert f \rVert_{\infty})} \right) \to 0. \quad (N \to \infty)
  $$

综上所述，对足够大的 $N$，有
$$
\begin{align*}
\mathbb{P} \left( | \langle L_N, f \rangle - \langle \sigma, f \rangle | > \varepsilon \right)
& = \mathbb{P} \left( | I_1 - I_2 + I_3 + I_4 + I_5 + I_6 | > \varepsilon \right) \\
& \leq \mathbb{P} \left( | I_2 | > \varepsilon / 6 \right) + \left( | I_3 | > \varepsilon / 6 \right) + \left( | I_4 | > \varepsilon / 6 \right) + \left( | I_6 | > \varepsilon / 6 \right),
\end{align*}
$$
令 $N \to \infty$，即得所需结论：
$$
\lim_{N \to \infty} \mathbb{P} \left( | \langle L_N, f \rangle - \langle \sigma, f \rangle | > \varepsilon \right) = 0.
$$
