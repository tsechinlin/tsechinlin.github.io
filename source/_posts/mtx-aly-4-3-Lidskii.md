---
title: "矩阵分析 - Hermite 矩阵中的优化关系"
date: 2020-07-31 11:30:02
tags:
  - Eigenvalue
  - Hermitian Matrix
categories: Matrix Analysis
mathjax: true
---

阅读笔记：<u>Matrix analysis</u> [Horn, Roger A., and Charles R. Johnson].

<!--more-->

本篇约定对所有出现的 Hermite 矩阵 $A = [a_{ij}]_{i,j=1}^n \in \mathcal{M}_n(\mathbb{C})$，其特征值组成的向量记为 $\lambda(A) = [\lambda_i(A)]_{i=1}^n \in \mathbb{R}^n$，主对角线元素组成的向量则记为 $d(A) = [a_{ii}]_{i=1}^n \in \mathbb{R}^n$。

## 向量的优化关系

### 单调重排

给定 $z = [z_i]_{i=1}^n \in \mathbb{R}^n$，
+ 存在 $\{ 1, \cdots, n \}$ 上的一个置换 $\sigma$，使得
  $$
  z_{\sigma(1)} \geq z_{\sigma(2)} \geq \cdots \geq z_{\sigma(n-1)} \geq z_{\sigma(n)}.
  $$
  记 $z_i^{\downarrow} = z_{\sigma(i)}$，称向量 $z^{\downarrow} = [z_i^{\downarrow}]_{i=1}^n \in \mathbb{R}^n$ 为 $z$ 的**非增重排 (nonincreasing rearrangement)**。
+ 存在 $\{ 1, \cdots, n \}$ 上的一个置换 $\tau$，使得
  $$
  z_{\tau(1)} \leq z_{\tau(2)} \leq \cdots \leq z_{\tau(n-1)} \leq z_{\tau(n)}.
  $$
  记 $z_i^{\uparrow} = z_{\tau(i)}$，称向量 $z^{\uparrow} = [z_i^{\uparrow}]_{i=1}^n \in \mathbb{R}^n$ 为 $z$ 的**非减重排 (nondecreasing rearrangement)**。

**性质**

+ 设 $x, y \in \mathbb{R}^n$，那么 $(x^\downarrow + y^\downarrow)^\downarrow = x^\downarrow + y^\downarrow$ 与 $(x^\uparrow + y^\uparrow)^\uparrow = x^\uparrow + y^\uparrow$ 都成立。
+ 设 $x \in \mathbb{R}^n$，那么 $(-x)^\downarrow = - (x^\uparrow)$。

### 双随机矩阵

矩阵 $S = [s_{ij}]_{i,j=1}^n \in \mathcal{M}_n(\mathbb{R})$ 为**双随机的 (doubly stochastic)**，如果
+ $S$ 为非负矩阵，即对所有的 $i,j \in \{ 1, \cdots, n \}$，有 $s_{ij} \geq 0$，
+ $S$ 的每一行、每一列的和都为 $1$，即 $S 1_n = 1_n$ 以及 $1_n^\top S = 1_n^\top$，这里 $1_n$ 表示长度为 $n$，每一项都为 $1$ 的向量。

**性质**

+ $\mathcal{M}_n(\mathbb{R})$ 中所有的双随机矩阵构成一个闭凸集。
+ 假设 $S, P_1, P_2 \in \mathcal{M}_n(\mathbb{R})$，如果 $S$ 为双随机的，$P_1, P_2$ 为置换矩阵，那么 $P_1 S P_2$ 也是双随机的。
+ **(Birkhoff–von Neumann theorem)** 矩阵 $S =  \in \mathcal{M}_n(\mathbb{R})$ 是双随机的，当且仅当存在置换矩阵 $P_1, \cdots, P_N \in \mathcal{M}_n(\mathbb{R})$ 以及正实数 $t_1, \cdots, t_N \in \mathbb{R}_+$，使得
  $$
  \sum_{i=1}^N t_i = 1 \quad \text{ and } \quad S = \sum_{i=1}^N t_i P_i.
  $$
  此外，这里可以使置换矩阵的数量满足 $N \leq n^2 - n +1$。 

### 优化

给定向量 $x, y \in \mathbb{R}^n$，称 $x$ **优化 (majorizes)** $y$，如果对所有的 $k = 1, \cdots, n$，都有
$$
\max _{1 \leq i_{1}<\cdots<i_{k} \leq n} \sum_{j=1}^{k} x_{i_{j}} \geq \max _{1 \leq i_{1} < \cdots < i_{k} \leq n} \sum_{j=1}^{k} y_{i_{j}}
$$
并且在 $k = n$ 时等号成立。

**单调重排与优化**

给定向量 $x, y \in \mathbb{R}^n$，下列命题等价：
+ $x$ 优化 $y$。
+ 对所有的 $k = 1, \cdots, n$，都有 $\sum_{i=1}^k x_i^{\downarrow} \geq \sum_{i=1}^k y_i^{\downarrow}$，并且在 $k = n$ 时等号成立。
+ 对所有的 $k = 1, \cdots, n$，都有 $\sum_{i=1}^k x_i^{\uparrow} \leq \sum_{i=1}^k y_i^{\uparrow}$，并且在 $k = n$ 时等号成立。

**双随机矩阵与优化**

给定向量 $x, y \in \mathbb{R}^n$，下列命题等价：
+ $x$ 优化 $y$。
+ 存在双随机矩阵 $S \in \mathcal{M}_n(\mathbb{R})$ 使得 $y = Sx$。
+ 存在若干个置换矩阵 $P_1, \cdots, P_N$ 以及正实数 $t_1, \cdots, t_N \in \mathbb{R}_+$，使得
  $$
  \sum_{i=1}^N t_i = 1 \quad \text{ and } \quad y = \sum_{i=1}^N t_i P_i x.
  $$

**性质**

+ 给定向量 $x, y \in \mathbb{R}^n$，设 $P, Q \in \mathcal{M}_n(\mathbb{C})$ 为置换矩阵，那么 $x$ 优化 $y$ 当且仅当 $Px$ 优化 $Qy$。
+ 给定向量 $x, y, w \in \mathbb{R}^n$，假设 $x$ 优化 $y$，那么
  $$
  \sum_{i=1}^{n} w_i^{\downarrow} x_{i}^{\uparrow} \leq \sum_{i=1}^{n} w_i^{\downarrow} y_{i} \leq \sum_{i=1}^{n} w_i^{\downarrow} x_{i}^{\downarrow}
  $$
  对 $k = 1, \cdots, n$，令 $\hat{X}_k = \sum_{i=1}^{k} x_{i}^{\downarrow}$，$\check{X}_k = \sum_{i=1}^{k} x_{i}^{\uparrow}$ 以及 $Y_k = \sum_{i=1}^{k} y_{i}$。那么，
  + 上式中右端的等号成立当且仅当对所有的 $k = 1, \cdots, n - 1$，有
    $$
    (w_k^{\downarrow} - w_{k + 1}^{\downarrow}) (\hat{X}_k - Y_k) = 0.
    $$
  + 上式中左端的等号成立当且仅当对所有的 $k = 1, \cdots, n - 1$，有
    $$
    (w_k^{\downarrow} - w_{k + 1}^{\downarrow}) (\check{X}_k - Y_k) = 0.
    $$

## Hermite 矩阵中的优化关系

### Schur–Horn 定理：Hermite 矩阵的特征值优化其主对角线

**(Schur–Horn theorem)** 假设 $A \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，那么其特征值组成的向量 $\lambda(A)$ 优化其主对角线元素组成的向量 $d(A)$，即对所有的 $k = 1, \cdots, n$，都有
$$
\sum_{i=1}^n \lambda_i(A)^{\downarrow} \geq \sum_{i=1}^n d_i(A)^{\downarrow},
$$
其中当 $k = n$ 时等号成立。如果对某个 $k \in \{ 1, \cdots, n-1 \}$，上述不等式成为等式，那么 $A$ 置换相似于 $B \oplus D$，其中 $B \in \mathcal{M}_k(\mathbb{C})$ 而 $D \in \mathcal{M}_{n-k}(\mathbb{C})$。

### Schur–Horn 逆定理

给定向量 $x, y \in \mathbb{R}^n$，并假设 $x$ 优化 $y$。令 $\lambda = \operatorname{diag}(x) \in \mathcal{M}_n(\mathbb{R})$，那么存在实正交矩阵 $Q \in \mathcal{M}_n(\mathbb{R})$ 使得 $d (Q^\top \Lambda Q) = y$。也就是说，存在是对称矩阵 $A = Q^\top \Lambda Q$，使得 $\lambda(A) = x$ 以及 $d(A) = y$。

### Schur–Horn 定理的推广：矩阵 Hermite 部分的特征值优化其特征值的  Hermite 部分

假设 $A \in \mathcal{M}_n(\mathbb{C})$，那么其 Hermite 部分 $H(A) = (A + A^\*) / 2$ 的特征值 $\lambda(H(A))$ 使 $\operatorname{Re} \lambda(A)$ 优化。

### Schur–Horn 逆定理的推广

给定 $x \in \mathbb{R}^n$ 以及 $z \in \mathbb{C}^n$，如果 $x$ 优化 $\operatorname{Re}z$，那么存在 $A \in \mathcal{M}_n(\mathbb{C})$ 使得 $z_1, \cdots, z_n$ 为 $A$ 的特征值，而 $x_1, \cdots, x_n$ 为 $H(A) = (A + A^\*) / 2$ 的特征值。

### Fan 不等式与 Lidskii 不等式：Hermite 矩阵和中的优化关系

假设 $A, B \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，那么
+ **(Fan)** $\lambda(A)^\downarrow + \lambda(B)^\downarrow$ 优化 $\lambda(A + B)$。
+ **(Lidskii)** 
  + $\lambda(A + B)$ 优化 $\lambda(A)^\downarrow + \lambda(B)^\uparrow$。
  + $\lambda(B)$ 优化 $\lambda(A + B)^\downarrow - \lambda(A)^\downarrow$。

### Hermite 矩阵内积上下界

假设 $A, B \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，那么
$$
\sum_{i=1}^{n} \lambda_{i}(A)^{\downarrow} \lambda_{i}(B)^{\uparrow} \leq \operatorname{tr} (A B) \leq \sum_{i=1}^{n} \lambda_{i}(A)^{\downarrow} \lambda_{i}(B)^{\downarrow}
$$
如果上式中任意一个不等式成为等式，那么 $A$ 与 $B$ 交换。
+ 如果右边的不等式成为等式，那么存在酉矩阵 $U \in \mathcal{M}_n(\mathbb{C})$ 使得
  $$
  A = U \operatorname{diag}(\lambda(A)^\downarrow)U^∗, \quad B = U \operatorname{diag}(\lambda(B)^\downarrow)U^∗.
  $$
+ 如果左边的不等式成为等式，那么存在酉矩阵 $U \in \mathcal{M}_n(\mathbb{C})$ 使得
  $$
  A = U \operatorname{diag}(\lambda(A)^\downarrow)U^∗, \quad B = U \operatorname{diag}(\lambda(B)^\uparrow)U^∗.
  $$
