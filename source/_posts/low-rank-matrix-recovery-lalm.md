---
title: Low Rank Matrix Recovery - Linearized ALM for Nuclear Norm Minimization
date: 2019-11-11 01:47:30
tags:  
  - Nuclear Norm
  - Low Rank Matrix Recovery
categories: Optimization
mathjax: true
---

核范数的最小化问题算法，参考 <u>Linearized augmented Lagrangian and alternating direction methods for nuclear norm minimization</u> [J Yang, X Yuan] 中的第三部分。

<!--more-->

## Problem

$$
\begin{alignat*}{2}
\min \quad & \|X\|_*  \\ 
\mbox{s.t.} \quad 
& \mathcal{A}X = b
\end{alignat*}
$$

其中 $X \in \mathbb{R}^{m \times n}$ 为决策变量，$\mathcal{A}: \mathbb{R}^{m\times n} \rightarrow \mathbb{R}^p$ 为给定线性算子，$b \in \mathbb{R}^p$ 给定。

## Motivation

To be complete

## Algorithm

给定参数：

+ $\beta$：增广 Lagrangian 函数中惩罚项因子
+ $\tau$：近端参数 Proximal parameter

迭代步骤为：
$$
\begin{aligned} 
X^{k+1} &= \mathop{\arg\min}\limits_{X} \left[ \|X\|_{*}+\frac{\beta}{2 \tau}\left\|X-\left(X^{k}-\tau g^{k}\right)\right\|_{F}^{2} \right]= \mathcal{D}_{\tau / \beta}\left(X^{k}-\tau g^{k}\right)  \\
\lambda^{k+1} &=\lambda^{k}+\beta\left(b-\mathcal{A} X^{k+1}\right) \end{aligned}
$$

其中 $g^{k}:=\mathcal{A}^{\*}\left(\mathcal{A} X^{k}-b^{k}\right)=\mathcal{A}^{\*}\left(\mathcal{A} X^{k}-b-\lambda^{k} / \beta\right)$。

在 $X^{k+1}$ 的迭代公式中，左边的式子在收敛性分析中比较重要，右端的式子给出了闭形式解 closed-form solution，可以通过 SVD 分解来计算。

## Convergence Analysis

总体结论就是，当 $\tau$ 取合适的值时，对于任意固定的 $\beta > 0$，以及任意的初值 $X_0 \in \mathbb{R}^{m \times n}$ 以及 $\lambda_0 \in \mathbb{R}^p$，算法迭代得到的序列最终收敛于最优解。

### 最优性条件

原问题必定有最优解 (**Why?**)，所以根据最优性条件：$\exists X^* \in \mathcal{A}^{-1}(b)$，使得
$$
0 \in \partial\left\|X^{*}\right\|_{*} + N_{\mathcal{A}^{-1}(b)}(X^*)
$$
其中左边表示次梯度，右边是 normal cone。

> 非光滑凸问题的最优性条件参见 <u>Nonlinear Optimization</u> [Andrzej Ruszczynski] 中 3.5 节 Optimality Conditions for Convex Problems 中的 THEOREM 3.33. (**有时间补一下证明**)

注意到事实上：(**有时间补一下最后一步的证明**)
$$
\begin{split}
N_{\mathcal{A}^{-1}(b)}(X^*) 
&= [\mathcal{A}^{-1}(b) - X^*]^{\circ} \\ 
&= [\mathcal{A}^{-1}(0)]^{\circ} \\
&= \left\{ \mathcal{A}^*\lambda: \lambda \in \mathbb{R}^n \right\}
\end{split}
$$
其中 $\operatorname{cone}(S)$ 表示由集合 $S$ 生成的锥，$S^\circ$ 表示 $S$ 的 polar cone。

于是可以该条件等价于存在 $\lambda^* \in \mathbb{R}^p$ 使得
$$
\mathcal{A}^{*} \lambda^{*} \in \partial\left\|X^{*}\right\|_{*}
$$
并且这个条件是充分的，也就是说，如果存在 $X^{\*} \in \mathbb{R}^{m \times n}, \lambda^\* \in \mathbb{R}^p$ 使得
$$
\mathcal{A}^{*} \lambda^{*} \in \partial\left\|X^{*}\right\|_{*}, \quad \mathcal{A}X = b
$$
那么 $X^*$ 为该问题的解。

> 核范数的次梯度为 (后面的证明中基本不会用到)
> $$
> \partial\|X\|_{*}=\left\{U V^{\top}+W: W \in \mathbb{R}^{m\times n} , U^{\top} W=0, W V=0,\|W\|_{2} \leq 1\right\}
> $$
> 其中 $X = U \Sigma V^T$ 为 SVD 分解，$U \in \mathbb{R}^{m \times r}, V \in \mathbb{R}^{n \times r}$ 为列向量标准正交的矩阵，$\Sigma$ 为 $r$ 阶对角阵，$r$ 为矩阵的秩。

### 引理 1

假设 $X^\* \in \mathbb{R}^{m \times n}, \lambda^\* \in \mathbb{R}^p$ 满足条件
$$
\mathcal{A}^{*} \lambda^{*} \in \partial\left\|X^{*}\right\|_{*}, \quad \mathcal{A}X^* = b
$$
固定 $\beta > 0, \tau > 0$，对任意给定的初值 $X_0 \in \mathbb{R}^{m \times n}$ 以及 $\lambda_0 \in \mathbb{R}^p$，迭代公式 (LALM)
$$
\begin{aligned} 
X^{k+1} &= \mathop{\arg\min}\limits_{X} \left[ \|X\|_{*}+\frac{\beta}{2 \tau}\left\|X-\left(X^{k}-\tau g^{k}\right)\right\|_{F}^{2} \right]= \mathcal{D}_{\tau / \beta}\left(X^{k}-\tau g^{k}\right)  \\
\lambda^{k+1} &=\lambda^{k}+\beta\left(b-\mathcal{A} X^{k+1}\right) \end{aligned}
$$
所给出的序列 $\{(X^k, \lambda^k)\}$ 满足
$$
\begin{aligned} \frac{1}{\beta}\left(\lambda^{k+1}-\lambda^{*}\right)^{\top}\left(\lambda^{k}-\lambda^{k+1}\right) &+\frac{\beta}{\tau}\left\langle X^{k+1}-X^{*}, X^{k}-X^{k+1}\right\rangle \\ & \geq\left(\lambda^{k}-\lambda^{k+1}\right)^{\top} \mathcal{A}\left(X^{k}-X^{k+1}\right) \end{aligned}
$$
**证明**：

在 $X^{k+1}$ 的定义中，可以看到她是无约束优化问题的解，且目标函数为凸函数，所以其满足最优性条件 (充要条件)
$$
0 \in \partial\left\|X^{k+1}\right\|_{*} + \frac{\beta}{\tau}\left[X^{k+1}-\left(X^{k}-\tau g^{k}\right)\right]
$$

> 关于无约束凸问题的最优性条件，参见 <u>Nonlinear Optimization</u> [Andrzej Ruszczynski] 中 3.2 节 Unconstrained Minima of Convex Functions 中的 THEOREM 3.5 (**有时间补一下证明**)

利用
$$
\begin{split}g^{k} &= \mathcal{A}^{*}\left(\mathcal{A} X^{k}-b^{k}\right) \\ &= \mathcal{A}^{*}\left(\mathcal{A} X^{k}-b-\lambda^{k} / \beta\right) \\&= \mathcal{A}^{*}\left(\mathcal{A} X^{k}-b-\lambda^{k+1} / \beta + b - \mathcal{A} X^{k+1} \right) \\&= -\mathcal{A}^{*}\lambda^{k+1}/\beta - \mathcal{A}^{*} \mathcal{A} (X^{k+1} - X^k)\end{split}
$$

代入 $X^{k+1}$ 满足的最优性条件：
$$
\begin{split}&-\frac{\beta}{\tau}\left[X^{k+1}-\left(X^{k}-\tau g^{k}\right)\right] \\=& \frac{\beta}{\tau}\left(I-\tau \mathcal{A}^{*} \mathcal{A}\right)\left(X^{k}-X^{k+1}\right)+\mathcal{A}^{*} \lambda^{k+1} \in \partial\left\|X^{k+1}\right\|_{*}\end{split}
$$
注意到 $\mathcal{A}^{\*} \lambda^{\*} \in \partial \left\lVert X^{\*} \right\rVert_{\*}$，可以推出
$$
\left\langle X^{k+1}-X^{*}, \ \frac{\beta}{\tau}\left(I-\tau \mathcal{A}^{*} \mathcal{A}\right)\left(X^{k}-X^{k+1}\right)+\mathcal{A}^{*}\left(\lambda^{k+1}-\lambda^{*}\right)\right\rangle \geq 0
$$

> 这是由于对于任意凸函数 $f: \mathbb{R}^n \rightarrow {\mathbb{R}}$，以及 $x, y \in \operatorname{dom} f$，如果
> $$
> g_x \in \partial f(x), \quad g_y \in \partial f(y)
> $$
> 那么根据次梯度的定义
> $$
> f(y) \geq f(x) + \langle g_x, y-x \rangle, \quad f(x) \geq f(y) + \langle g_y, x-y \rangle
> $$
> 两边相加即可得到 $\langle g_x - g_y, x-y \rangle \geq 0$

对上式做适当计算
$$
\begin{split}
0 &\leq \left\langle X^{k+1}-X^{*}, \ \frac{\beta}{\tau}\left(I-\tau \mathcal{A}^{*} \mathcal{A}\right)\left(X^{k}-X^{k+1}\right)+\mathcal{A}^{*}\left(\lambda^{k+1}-\lambda^{*}\right)\right\rangle \\
&= \frac{\beta}{\tau}\left\langle X^{k+1}-X^{*}, \ X^{k}-X^{k+1}\right\rangle + \left\langle X^{k+1}-X^{*}, \ -\beta \mathcal{A}^{*} \mathcal{A}\left(X^{k}-X^{k+1}\right)+\mathcal{A}^{*}\left(\lambda^{k+1}-\lambda^{*}\right)\right\rangle \\
&= \frac{\beta}{\tau}\left\langle X^{k+1}-X^{*}, \ X^{k}-X^{k+1}\right\rangle + \left\langle \mathcal{A}(X^*-X^{k+1}), \ \beta \mathcal{A}\left(X^{k}-X^{k+1}\right)-\left(\lambda^{k+1}-\lambda^{*}\right)\right\rangle
\end{split}
$$
利用 $\mathcal{A}(X^* - A^{k+1}) = b - \mathcal{A}X^{k+1} = (\lambda^{k+1} - \lambda^k) / \beta$，可以进一步推出
$$
\begin{split}
0 &\leq  \frac{\beta}{\tau}\left\langle X^{k+1}-X^{*}, \ X^{k}-X^{k+1}\right\rangle + \left\langle \frac{\lambda^{k+1}-\lambda^{k}}{\beta}, \ \beta \mathcal{A}\left(X^{k}-X^{k+1}\right)-\left(\lambda^{k+1}-\lambda^{*}\right)\right\rangle \\
&= \frac{\beta}{\tau}\left\langle X^{k+1}-X^{*}, \ X^{k}-X^{k+1}\right\rangle + \frac{1}{\beta} \left\langle {\lambda^{k}-\lambda^{k+1}}, \ \lambda^{k+1}-\lambda^{*}\right\rangle - \left\langle {\lambda^{k}-\lambda^{k+1}}, \  \mathcal{A}\left(X^{k}-X^{k+1}\right)\right\rangle
\end{split}
$$
引理 1 证毕。

### 引入内积

在空间 $\mathbb{R}^{m \times n} \times \mathbb{R}^{p}$ 引入内积：$\forall u = (X, \lambda), v = (Y, \zeta) \in \mathbb{R}^{m \times n} \times \mathbb{R}^{p}$
$$
\langle u, v\rangle_{G}=\frac{\beta}{\tau}\langle X, Y\rangle+\frac{1}{\beta} \lambda^{\top} \zeta
$$
不难验证这是一个内积 (非负性，定性，齐次性，可加性，交换律)。

其诱导的范数满足
$$
\left\lVert u \right\rVert_G^2 = \langle u, u \rangle_G = \frac{\beta}{\tau} \|X\|_F^2+ \frac{1}{\beta} \|\lambda\|^2
$$
在定义了这个内积之后，引理 1 的结论可以简写成：
$$
\left\langle u^{k+1}-u^{*}, u^{k}-u^{k+1}\right\rangle_{G} \geq\left(\lambda^{k}-\lambda^{k+1}\right)^{\top} \mathcal{A}\left(X^{k}-X^{k+1}\right)
$$
其中 $u^k = (X^k, \lambda^k)$。

### 引理 2

沿用引理 1 的记号，并令 $u^k = (X^k, \lambda^k), \ u^{\*} = (X^\*, \lambda^\*)$，在引理 1 的条件下，如果还有
$$
0 < \tau < 1/\rho(\mathcal{A}^{*}\mathcal{A})
$$
其中 $1/\rho(\mathcal{A}^{\*}\mathcal{A})$ 表示 $\mathcal{A}^{\*}\mathcal{A}$ 的谱半径，那么

+ $\left\lVert u^k-u^* \right\rVert_G$ 非增，所以其收敛 (单调，有下界)
+ $\left\lVert u^k-u^{k+1} \right\rVert_G \rightarrow 0$
+ $\{u_k\}$ 包含于一个紧集中

**证明**：

第三条实际上是第一条的简单推论：因为 $\left\lVert u^k-u^* \right\rVert_G$ 有界。

对引理 1 的结论作适当变形，
$$
\begin{split}
\left(\lambda^{k}-\lambda^{k+1}\right)^{\top} \mathcal{A}\left(X^{k}-X^{k+1}\right) &\leq \left\langle u^{k+1}-u^{*}, u^{k}-u^{k+1}\right\rangle_{G} \\
& = \left\langle u^{k}-u^{*} + u^{k+1}-u^{k}, u^{k}-u^{k+1}\right\rangle_{G} \\
& = \left\langle u^{k}-u^{*}, u^{k}-u^{k+1}\right\rangle_{G} - \left\lVert u^k-u^{k+1} \right\rVert_G^2
\end{split}
$$
于是
$$
\begin{split} 
& \left\|u^{k}-u^{*}\right\|_{G}^{2}-\left\|u^{k+1}-u^{*}\right\|_{G}^{2} \\
=& \left\langle u^{k} + u^{k+1} -2u^{*}, u^{k}-u^{k+1}\right\rangle_{G} \\
=& 2\left\langle u^{k}-u^{*}, u^{k}-u^{k+1}\right\rangle_{G}-\left\|u^{k}-u^{k+1}\right\|_{G}^{2} \\ 
\geq & 2\left\|u^{k}-u^{k+1}\right\|_{G}^{2}+2\left(\lambda^{k}-\lambda^{k+1}\right)^{\top} \mathcal{A}\left(X^{k}-X^{k+1}\right)-\left\|u^{k}-u^{k+1}\right\|_{G}^{2} \\
=& \frac{\beta}{\tau}\left\|X^{k}-X^{k+1}\right\|_{F}^{2}+\frac{1}{\beta}\left\|\lambda^{k}-\lambda^{k+1}\right\|^{2}+2\left(\lambda^{k}-\lambda^{k+1}\right)^{T} \mathcal{A}\left(X^{k}-X^{k+1}\right) 
\end{split}
$$
定义 $\delta := 1 - \tau \rho(\mathcal{A}^{*}\mathcal{A}) > 0$，以及
$$
\eta := \frac{1}{\beta(1 + \delta)} > 0
$$
那么
$$
\begin{split} 
&\left\|u^{k}-u^{*}\right\|_{G}^{2}-\left\|u^{k+1}-u^{*}\right\|_{G}^{2} \\
\geq & \frac{\beta}{\tau}\left\|X^{k}-X^{k+1}\right\|_{F}^{2}+\left(\frac{1}{\beta}-\eta\right)\left\|\lambda^{k}-\lambda^{k+1}\right\|^{2}-\frac{1}{\eta}\left\|\mathcal{A}\left(X^{k}-X^{k+1}\right)\right\|^{2} \\ 
\geq &\left(\frac{\beta}{\tau}-\frac{\rho\left(\mathcal{A}^{*} \mathcal{A}\right)}{\eta}\right)\left\|X^{k}-X^{k+1}\right\|_{F}^{2}+\left(\frac{1}{\beta}-\eta\right)\left\|\lambda^{k}-\lambda^{k+1}\right\|^{2} \\
=& \frac{\beta \delta^{2}}{\tau}\left\|X^{k}-X^{k+1}\right\|_{F}^{2}+\frac{\delta}{\beta(1+\delta)}\left\|\lambda^{k}-\lambda^{k+1}\right\|^{2} \\ 
\geq & \nu\left\|u^{k}-u^{k+1}\right\|_{G}^{2}
\end{split}
$$
其中 $\nu := \operatorname{min}(\delta^2, \delta/(1+\delta)) > 0$

> **第一步**利用不等式：
> $$
> 2a^T b = 2(\eta^{1/2}a)^T\left(\frac{b}{\eta^{1/2}}\right) \geq -\eta \|a\|^2-\frac{\|b\|^2}{\eta}
> $$
> **第二步**利用谱半径性质 $\forall X \in \mathbb{R}^{m \times n}$，有
> $$
> \|\mathcal{A}X\|^2 \leq \rho(\mathcal{A}^{*}\mathcal{A}) \|X\|^2
> $$
> 这是由于 $\|\mathcal{A}X\|^2 = \langle X, \mathcal{A}^{\*}\mathcal{A}X \rangle$，由于 $\mathcal{A}^{\*}\mathcal{A}$ 自伴，根据实谱定理，存在一组标准正交基使得基元素为 $\mathcal{A}^{*}\mathcal{A}$ 的特征向量，将 $X$ 按这组基展开，根据谱范数的定义不难验证上面的不等式。
>
> **第三步**利用 $\rho(\mathcal{A}^{*}\mathcal{A}) = (1-\delta)/\tau$ 即可。

到这里就已经证明了 $\left\lVert u^k-u^* \right\rVert_G$ 非增，所以其收敛。于是
$$
\left\|u^{k}-u^{*}\right\|_{G}^{2}-\left\|u^{k+1}-u^{*}\right\|_{G}^{2} \rightarrow 0, \quad k \rightarrow \infty
$$
由于 $\nu >0$，所以 $\left\lVert u^k-u^{k+1} \right\rVert_G^{2} \rightarrow 0$，引理 2 证毕。

### 收敛性结论

对于任意给定 $\beta > 0$, 以及给定的初值 $X_0 \in \mathbb{R}^{m \times n}$ 以及 $\lambda_0 \in \mathbb{R}^p$，当 $0 < \tau < 1/\rho(\mathcal{A}^{\*}\mathcal{A})$ 成立时，LALM 迭代公式得到的序列 $\{(X^k, \lambda^k)\}$ 收敛于 $(X^\*, \lambda^\*)$，其中 $X^\*$ 为问题的最优解。

**证明**：

沿用引理 2 的符号，由于 $\left\lVert u^k-u^{k+1} \right\rVert_G \rightarrow 0$，所以
$$
X^k - X^{k+1} \rightarrow 0, \quad \lambda^k - \lambda^{k+1} \rightarrow 0
$$
因为 $\lambda^k = \lambda^{k-1} + \beta (b - \mathcal{A}X^k)$，所以 $\mathcal{A}X^k \rightarrow b$。

因为 $\{u_k\}$ 包含于一个紧集中，所以存在其一个收敛子列 $\left\{ u^{k_j} \right\}$ 收敛至 $\hat{u} =\left(\hat{X} ; \hat{\lambda}\right)$，下面证明 $\left(\hat{X} ; \hat{\lambda}\right)$ 满足原优化问题的最优性条件，即
$$
\mathcal{A}^{*} \hat{\lambda} \in \partial\left\|\hat{X}\right\|_{*}, \quad \mathcal{A}\hat{X} = b
$$
由于 $\mathcal{A}X^k \rightarrow b$，所以 $\mathcal{A}X^{k_j} \rightarrow b$，从而 $\mathcal{A}\hat{X} = b$

然后，在引理 1 的证明中，我们根据 $X_{k+1}$ 迭代公式中的最优性条件得到了
$$
\frac{\beta}{\tau}\left(I-\tau \mathcal{A}^{*} \mathcal{A}\right)\left(X^{k}-X^{k+1}\right)+\mathcal{A}^{*} \lambda^{k+1} \in \partial\left\|X^{k+1}\right\|_{*}
$$
将 $\lambda^{k+1} =\lambda^{k}+\beta\left(b-\mathcal{A} X^{k+1}\right)$ 代入可以得到：
$$
\frac{\beta}{\tau}\left(I-\tau \mathcal{A}^{*} \mathcal{A}\right)\left(X^{k}-X^{k+1}\right)+\mathcal{A}^{*} \lambda^{k}+\beta\mathcal{A}^{*}\left(b-\mathcal{A} X^{k+1}\right) \in \partial\left\|X^{k+1}\right\|_{*}
$$
由于 $X^{k_j} \rightarrow \hat{X}, X^k - X^{k+1} \rightarrow 0$，所以 $X^{k_j+1} \rightarrow \hat{X}$，于是在上式对 $k_j$ 取极限，可以得到
$$
\mathcal{A}^{*} \hat{\lambda} \in \partial \| \hat{X} \|_*
$$

> 这里论文中是直接取极限，不过右边是一个集合，其极限意义不明，但根据次微分定义将其写开还是可以证明的。对于凸函数 $f: \mathbb{R}^n \rightarrow {\mathbb{R}}$，假设 $x_k \in \operatorname{dom} f$，以及
> $$
> g_k \in \partial f(x_k)
> $$
> 即 $\forall y \in \mathbb{R}^n$，有
> $$
> f(y) \geq f(x_k) + \langle g_k, y - x_k \rangle
> $$
> 如果 $k \rightarrow \infty$ 时，$x_k \rightarrow x \in \operatorname{dom} f$，以及 $g_k \rightarrow g$，那么对于任意固定的 $y \in \mathbb{R}^n$ (由于凸函数连续)，
> $$
> f(y) \geq f(x) + \langle g, y - x \rangle
> $$
> 即 $g \in \partial f(x)$

所以 $\left(\hat{X} ; \hat{\lambda}\right)$ 的确满足原优化问题的最优性条件，注意到引理 2 的第一个结论对于任意一对满足最优性条件的 $(X^\*, \lambda^\*)$ 成立，所以 $\left\lVert u^k-\hat{u} \right\rVert_G$ 非增，由于
$$
\left\lVert u^{k_j}-\hat{u} \right\rVert_G \rightarrow 0, \quad j \rightarrow \infty
$$
所以
$$
\left\lVert u^{k}-\hat{u} \right\rVert_G \rightarrow 0, \quad k \rightarrow \infty
$$
至此收敛性证毕。