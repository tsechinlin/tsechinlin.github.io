---
title: 二次曲线线性规划 Conic Linear Programming (CLP)
date: 2019-11-08 20:26:08
tags:
  - Convex
  - Duality
categories: Optimization
mathjax: true
---

查阅 SDP 的弱对偶性时碰到的一类规划问题，参考 David G. Luenberger 和 Yinyu Ye 的 Linear and Nonlinear Programming 一书第六章。

<!--more-->

## 欧式空间 $\mathbb{R}^n$ 中的闭凸锥

__定义__

称 $K \subset \mathbb{R}^n$ 为闭凸锥 (闭集、凸集、锥)，若

+ $\forall \mathbf{x}, \mathbf{y} \in K$ 以及 $ \alpha, \beta \geq0$，有 $\alpha \mathbf{x} + \beta \mathbf{y} \in K$
+ $K$ 为闭集

通常用 $\mathbf{x} \leq_K \mathbf{y}$ 表示 $y - x \in K$。

__常用闭凸锥__

+ $n$-dimensional non-negative orthant
  $$
  \mathbb{R}_+^n = \{ \mathbf{x} \in \mathbb{R}^n : x_i \geq 0, i = 1, \cdots, n \}
  $$

+ positive semidefinite matrix cone
  $$
  \mathcal{S}^n_+ = \{ \mathbf{X} \in \mathbb{R}^{n \times n} : \mathbf{X} = \mathbf{X}^T, \text{and } \forall \mathbf{v} \in \mathbb{R}^n, \mathbf{v}^T\mathbf{X}\mathbf{v} \geq 0\}
  $$

+ the $p$-order cone (where $1 \leq p < \infty$)
  $$
  C_p = \{ (\mathbf{x}, u) \in \mathbb{R}^{n+1}: \|\mathbb{x}\|_p \leq u \}
  $$

__对偶锥__

对于任意的 $K \subset \mathbb{R}^n$，其对偶锥 (dual cone) 定义为：
$$
K^* = \{ \mathbf{y} \in \mathbb{R}^n: \langle \mathbf{x}, \mathbf{y} \rangle \geq 0, \quad \forall \mathbf{x} \in K \}
$$

+ $\mathbb{R}_+^n$ 与 $\mathcal{S}^n_+$ 是自对偶的，即对偶锥为本身
+ 对于 $1 < p < \infty$，$C_p$ 的对偶锥为 $C_q$，其中 $p^{-1} + q^{-1} = 1$

## 二次曲线线性规划 Conic Linear Programming (CLP)

假设 $\mathbf{C}, \mathbf{A}_i \in \mathbb{R}^{k \times n}, 1 \leq i \leq m$ 已知，另外 $\mathbf{b} \in \mathbb{R}^m$ 也给定，$K \subset \mathbb{R}^{k \times n}$ 为闭凸锥，称下述以 $\mathbf{X}$ 为自变量的优化问题为**二次曲线线性规划**问题：
$$
\begin{alignat*}{2}
\min \quad & \langle \mathbf{C},\mathbf{X} \rangle  \\ 
\mbox{s.t.} \quad 
& \langle \mathbf{A}_i,\mathbf{X} \rangle=b_{i}, i=1,2, \cdots, m, \\
& \mathbf{X} \in K
\end{alignat*}
$$

+ $K = \mathcal{S}^n_+$ 时，CLP 称为**半正定规划** (Semidefinite Programming, SDP)

+ $K = C_p, 1 \leq p < \infty$ 时，CLP 称为 $p$-阶锥规划 ($p$-order cone programming)，

  特别的，当 $p=2$ 时，称为**二阶锥规划** (second-order cone programming, SOCP)

使用线性算子 $\mathcal{A}:\mathbb{R}^{k\times n} \rightarrow \mathbb{R}^m$，使得 $\mathcal{A}X = \left[\langle \mathbf{A}_i,\mathbf{X} \rangle, \cdots, \langle \mathbf{A}_m,\mathbf{X} \rangle \right]^T$，则 CLP 可写成更为紧凑的形式：
$$
\begin{alignat*}{2}
\min \quad & \langle \mathbf{C},\mathbf{X} \rangle  \\ 
\mbox{s.t.} \quad 
& \mathcal{A}\mathbf{X} =\mathbf{b} \\
& \mathbf{X} \in K
\end{alignat*}
$$

### 待填坑

## 半正定规划 Semidefinite Programming (SDP)

给定 $n$ 阶对称实矩阵 $\mathbf{C}, \mathbf{A}_i \in \mathbb{R}^{n \times n}, 1 \leq i \leq m$，以及 $\mathbf{b} \in \mathbb{R}^m$，称下述以 $\mathbf{X}$ 为自变量的优化问题为**半正定规划**问题：
$$
\begin{alignat*}{2}
\min \quad & \langle \mathbf{C},\mathbf{X} \rangle  \\ 
\mbox{s.t.} \quad 
& \langle \mathbf{A}_i,\mathbf{X} \rangle=b_{i}, i=1,2, \cdots, m, \\
& \mathbf{X} \succeq \mathbf{0}
\end{alignat*}
$$
上述半正定规划的对偶问题为：
$$
\begin{alignat*}{2}
\max \quad & \langle \mathbf{b},\mathbf{y} \rangle  \\ 
\mbox{s.t.} \quad 
& \sum_{i=1}^m y_i\mathbf{A}_i \preceq \mathbf{C}
\end{alignat*}
$$

### 弱对偶性

> 对原问题 (Primal) 的任意可行解 $\mathbf{X}$ 以及对偶问题 (Dual) 的可行解 $\mathbf{y}$，下述不等式恒成立：
> $$
> \langle \mathbf{C},\mathbf{X} \rangle \geq \langle \mathbf{b},\mathbf{y} \rangle
> $$

即对偶问题的任意目标值提供了原问题最优值的下界。这个结论很容易证明：
$$
\begin{align*}
\langle \mathbf{C}, \mathbf{X} \rangle-\langle \mathbf{b}, \mathbf{y} \rangle 
&=\langle \mathbf{C}, \mathbf{X} \rangle-\sum_{i=1}^{m} y_{i} b_{i} \\ 
&=\langle \mathbf{C}, \mathbf{X} \rangle-\sum_{i=1}^{m} y_{i}\left\langle \mathbf{A}_i, \mathbf{X}\right\rangle \\
&=\left\langle \mathbf{C} - \sum_{i=1}^{m} y_{i} \mathbf{A}_{i}, \mathbf{X}\right\rangle \geq 0
\end{align*}
$$
其中最后一个不等式是由于半正定矩阵的乘积仍为半正定矩阵，其迹非负。
