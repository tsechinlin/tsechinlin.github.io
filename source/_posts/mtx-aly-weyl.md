---
title: "矩阵分析 - Hermite 矩阵特征值不等式"
date: 2020-07-28 18:23:43
tags: 
  - Eigenvalue
  - Hermitian Matrix
categories: Matrix Analysis
mathjax: true
---

阅读笔记：<u>Matrix analysis</u> [Horn, Roger A., and Charles R. Johnson].

<!--more-->

本文约定对所有出现的 Hermite 矩阵 $A \in \mathcal{M}_n(\mathbb{C})$，其特征值按照非减顺序排列为 $\left \{ \lambda_i(A) \right \}_{i=1}^n$。

## 加性摄动

### Weyl 不等式

**(Weyl inequality)** 设 $A, B \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，那么，
+ 对任意 $i = 1, \cdots, n$ 以及 $j = 0, \cdots, n-i$，有
  $$
  \lambda_i(A + B) \leq \lambda_{i + j}(A) + \lambda_{n-j} (B).
  $$
  其中等式成立当且仅当存在非零向量 $x \in \mathbb{C}^n$，使得
  $$
  Ax = \lambda_{i + j}(A) x, \quad Bx =  \lambda_{n-j} (B) x \quad \text{ and } \quad (A + B) x = \lambda_i(A + B) x.
  $$
+ 对任意 $i = 1, \cdots, n$ 以及 $j = 1, \cdots, i$，有
  $$
  \begin{equation}
  \lambda_i(A + B) \geq \lambda_{i - j + 1}(A) + \lambda_{j} (B).
  \end{equation}
  $$
  其中等式成立当且仅当存在非零向量 $x \in \mathbb{C}^n$，使得
  $$
  Ax = \lambda_{i - j + 1}(A) x, \quad Bx =  \lambda_{j} (B) x \quad \text{ and } \quad (A + B) x = \lambda_i(A + B) x.
  $$

###  推论 1：考虑矩阵特征值符号

如果 $B$ 恰好有 $\pi$ 个正的特征值以及 $\nu$ 个负的特征值，那么
+ 对任意 $i = 1, \cdots, n - \pi$，有
  $$
  \lambda_i(A + B) \leq \lambda_{i + \pi}(A).
  $$
  其中等式成立当且仅当 $B$ 是奇异的以及存在非零向量 $x \in \mathbb{C}^n$，使得
  $$
  Ax = \lambda_{i + \pi}(A) x, \quad Bx =  0 \quad \text{ and } \quad (A + B) x = \lambda_i(A + B) x.
  $$
+ 对任意 $i = \nu + 1,  \cdots, n$，有
  $$
  \lambda_i(A + B) \geq \lambda_{i - \nu}(A).
  $$
  其中等式成立当且仅当 $B$ 是奇异的以及存在非零向量 $x \in \mathbb{C}^n$，使得
  $$
  Ax = \lambda_{i - \nu}(A) x, \quad Bx =  0 \quad \text{ and } \quad (A + B) x = \lambda_i(A + B) x.
  $$

### 推论 2：考虑矩阵秩

如果 $B$ 是奇异的且 $\operatorname{rank} (B) = r$，那么
+ 对任意 $i = 1, \cdots, n - r$，有
  $$
  \lambda_i(A + B) \leq \lambda_{i + r}(A).
  $$
  其中等式成立当且仅当 $\lambda_{n-r}(B) = 0$ 以及存在非零向量 $x \in \mathbb{C}^n$，使得
  $$
  Ax = \lambda_{i + r}(A) x, \quad Bx =  0 \quad \text{ and } \quad (A + B) x = \lambda_i(A + B) x.
  $$
+ 对任意 $i = \nu + 1,  \cdots, n$，有
  $$
  \lambda_i(A + B) \geq \lambda_{i - \nu}(A).
  $$
  其中等式成立当且仅当 $B$ 是奇异的以及存在非零向量 $x \in \mathbb{C}^n$，使得
  $$
  Ax = \lambda_{i - \nu}(A) x, \quad Bx =  0 \quad \text{ and } \quad (A + B) x = \lambda_i(A + B) x.
  $$

### 推论 3：关于 Hermite 矩阵的 $1$ 阶秩 Hermite 扰动的交错定理

**(Interlacing theorem for a rank-one Hermitian perturbation of a Hermitian matrix)** 假定 $n \geq 2$，设 $A \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，$z \in \mathbb{C}^n$ 为非零向量。那么，
+ 有交错不等式
  $$
  \lambda_1(A) \leq \lambda_1(A + zz^{*}) \leq \lambda_2(A) \leq \cdots \leq \lambda_{n-1}(A + zz^{*}) \leq \lambda_n(A) \leq \lambda_n(A + zz^{*}).
  $$
  + 对某个 $i = 1, \cdots, n$，等式 $\lambda_i(A + zz^{*}) = \lambda_i(A)$ 成立当且仅当存在非零向量 $x \in \mathbb{C}^n$，使得
    $$
    Ax = \lambda_{i}(A) x, \quad z^* x =  0 \quad \text{ and } \quad (A + zz^{*}) x = \lambda_i(A + zz^{*}) x.
    $$
  + 对某个 $i = 1, \cdots, n-1$，等式 $\lambda_i(A + zz^{*}) = \lambda_{i + 1}(A)$ 成立当且仅当存在非零向量 $x \in \mathbb{C}^n$，使得
    $$
    Ax = \lambda_{i + 1}(A) x, \quad z^* x =  0 \quad \text{ and } \quad (A + zz^{*}) x = \lambda_i(A + zz^{*}) x.
    $$
+ 有交错不等式
  $$
  \lambda_1(A - zz^{*}) \leq \lambda_1(A) \leq \lambda_2(A - z z^*) \leq \cdots \leq \lambda_{n-1}(A) \leq \lambda_n(A - zz^{*}) \leq \lambda_n(A).
  $$
  + 对某个 $i = 1, \cdots, n$，等式 $\lambda_i(A - zz^{*}) = \lambda_i(A)$ 成立当且仅当存在非零向量 $x \in \mathbb{C}^n$，使得
    $$
    Ax = \lambda_{i}(A) x, \quad z^* x =  0 \quad \text{ and } \quad (A - zz^{*}) x = \lambda_i(A - zz^{*}) x.
    $$
  + 对某个 $i = 2, \cdots, n$，等式 $\lambda_i(A - zz^{*}) = \lambda_{i - 1}(A)$ 成立当且仅当存在非零向量 $x \in \mathbb{C}^n$，使得
    $$
    Ax = \lambda_{i - 1}(A) x, \quad z^* x =  0 \quad \text{ and } \quad (A - zz^{*}) x = \lambda_i(A - zz^{*}) x.
    $$

### 推论 4：单调定理

**(Monotonicity theorem)** 假定 $A, B \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵并且 $B$ 半正定，那么对任意 $i = 1, \cdots, n$，有
$$
\lambda_i(A + B) \geq \lambda_{i}(A).
$$
其中等式成立当且仅当 $B$ 是奇异的以及存在非零向量 $x \in \mathbb{C}^n$，使得
$$
Ax = \lambda_{i}(A) x, \quad Bx =  0 \quad \text{ and } \quad (A + B) x = \lambda_i(A + B) x.
$$

## 加边摄动

### Cauchy 交错定理

**(Cauchy interlacing theorem)** 假定 $B \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，$y \in \mathbb{C}^n$ 以及 $a \in \mathbb{R}$。如果令
$$
A=\left[\begin{array}{ll}
B & y \\
y^{T} & a
\end{array}\right] \in \mathcal{M}_{n+1}(\mathbb{C}),
$$
那么有交错不等式
$$
\lambda_1(A) \leq \lambda_1(B) \leq \lambda_2(A) \leq \cdots \leq \lambda_n(A) \leq \lambda_n(B) \leq \lambda_{n + 1}(A).
$$
+ 对某个 $i = 1, \cdots, n$，等式 $\lambda_i(A) = \lambda_i(B)$ 成立当且仅当存在非零向量 $z \in \mathbb{C}^n$，使得
  $$
  Bz = \lambda_{i}(B) z, \quad y^*z =  0 \quad \text{ and } \quad B z = \lambda_i(A) z.
  $$
+ 对某个 $i = 1, \cdots, n$，等式 $\lambda_{i+1}(A) = \lambda_{i}(B)$ 成立当且仅当存在非零向量 $z \in \mathbb{C}^n$，使得
  $$
  Bz = \lambda_{i}(B) z, \quad y^*z =  0 \quad \text{ and } \quad B z = \lambda_{i+1}(A) z.
  $$

### 包容原理

**(Inclusion principle)** 假设 $A = [a_{ij}]_{i,j=1}^n \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，分划成
$$
A=\left[\begin{array}{ll}
B & C \\
C^{*} & D
\end{array}\right], \quad \text{ where } B \in \mathcal{M}_m(\mathbb{C}), \ D \in \mathcal{M}_{n - m}(\mathbb{C}), \ C \in \mathcal{M}_{m, n - m}(\mathbb{C}).
$$
**结论 1：**对任意 $i = 1, \cdots, m$，有
$$
\lambda_i(A) \leq \lambda_i(B) \leq \lambda_{i + n - m}(A).
$$
+ 其中下界中的不等式成立当且仅当存在非零向量 $\xi \in \mathbb{C}^m$，使得
  $$
  B \xi = \lambda_{i}(B) \xi, \quad C^*\xi =  0 \quad \text{ and } \quad B \xi = \lambda_i(A) \xi.
  $$
+ 上界中的不等式成立当且仅当存在非零向量 $\xi \in \mathbb{C}^m$，使得
  $$
  B\xi = \lambda_{i}(B) \xi, \quad C^*\xi =  0 \quad \text{ and } \quad B \xi = \lambda_{i+n-m}(A) \xi.
  $$

**结论 2：**

+ 假设对某组 $i = 1, \cdots, m$ 以及 $r = 1, \cdots, i$，有
  $$
  \lambda_{i-r+1}(A) = \cdots =  \lambda_i(A) = \lambda_i(B),
  $$
  那么 $\lambda_{i-r+1}(B) = \cdots = \lambda_i(B)$，并且存在标准正交向量 $\xi_1, \cdots, \xi_r \in \mathbb{C}^m$ 使得对所有的 $k = 1, \cdots, r$，有
  $$
  B\xi_k = \lambda_{i}(B) \xi_k \quad \text{ and } \quad C^*\xi_k = 0.
  $$
+ 假设对某组 $i = 1, \cdots, m$ 以及 $r = 1, \cdots, m - i + 1$，有
  $$
  \lambda_{i+ n - m}(A) = \cdots =  \lambda_{i + n - m + r - 1}(A) = \lambda_i(B),
  $$
  那么 $\lambda_{i}(B) = \cdots = \lambda_{i + r - 1}(B)$，并且存在标准正交向量 $\xi_1, \cdots, \xi_r \in \mathbb{C}^m$ 使得对所有的 $k = 1, \cdots, r$，有
  $$
  B\xi_k = \lambda_{i}(B) \xi_k \quad \text{ and } \quad C^*\xi_k = 0.
  $$

**结论 3：**有下列不等式成立：
$$
\sum_{i=1}^m \lambda_{i}(A) \leq \sum_{i=1}^m a_{ii} \leq \sum_{i=1}^m \lambda_{n - m + i}(A)
$$
如果上述不等式中有一个不等号成为等号，那么就有 $C = 0$，从而 $A = B \oplus D$。

### Poincaré 分离定理

**(Poincaré separation theorem)** 假设 $A \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，$u_1, \cdots, u_m \in \mathbb{C}^n$ 标准正交。令
$$
B_m = \left [u^*_i A u_j \right]_{i,j=1}^m \in \mathcal{M}_m(\mathbb{C}),
$$
那么对任意 $i = 1, \cdots, m$，有
$$
\lambda_i(A) \leq \lambda_i(B) \leq \lambda_{i + n - m}(A).
$$
