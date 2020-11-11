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

以下约定，对所有出现的 Hermite 矩阵 $\mathbf{A} \in \mathcal{M}_n(\mathbb{C})$，其特征值按照非减顺序排列为

$$
\lambda_{1}(\mathbf{A}) \leq \lambda_{2}(\mathbf{A}) \leq \cdots \leq \lambda_{n-1}(\mathbf{A}) \leq \lambda_{n}(\mathbf{A}).
$$

## 加性摄动

### Weyl 不等式

**(Weyl inequality)** 设 $\mathbf{A}, \mathbf{B} \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，那么，
+ 对任意 $i = 1, \cdots, n$ 以及 $j = 0, \cdots, n-i$，有
  $$
  \lambda_i(\mathbf{A} + \mathbf{B}) \leq \lambda_{i + j}(\mathbf{A}) + \lambda_{n-j} (\mathbf{B}).
  $$
  其中等式成立当且仅当存在非零向量 $\mathbf{x} \in \mathbb{C}^n$，使得
  $$
  \mathbf{A}\mathbf{x} = \lambda_{i + j}(\mathbf{A}) \mathbf{x}, \quad \mathbf{B}\mathbf{x} =  \lambda_{n-j} (\mathbf{B}) \mathbf{x} \quad \text{ and } \quad (\mathbf{A} + \mathbf{B}) \mathbf{x} = \lambda_i(\mathbf{A} + \mathbf{B}) \mathbf{x}.
  $$
+ 对任意 $i = 1, \cdots, n$ 以及 $j = 1, \cdots, i$，有
  $$
  \begin{equation}
  \lambda_i(\mathbf{A} + \mathbf{B}) \geq \lambda_{i - j + 1}(\mathbf{A}) + \lambda_{j} (\mathbf{B}).
  \end{equation}
  $$
  其中等式成立当且仅当存在非零向量 $\mathbf{x} \in \mathbb{C}^n$，使得
  $$
  \mathbf{A}\mathbf{x} = \lambda_{i - j + 1}(\mathbf{A}) \mathbf{x}, \quad \mathbf{B}\mathbf{x} =  \lambda_{j} (\mathbf{B}) \mathbf{x} \quad \text{ and } \quad (\mathbf{A} + \mathbf{B}) \mathbf{x} = \lambda_i(\mathbf{A} + \mathbf{B}) \mathbf{x}.
  $$

###  推论 1：考虑矩阵特征值符号

如果 $\mathbf{B}$ 恰好有 $\pi$ 个正的特征值以及 $\nu$ 个负的特征值，那么
+ 对任意 $i = 1, \cdots, n - \pi$，有
  $$
  \lambda_i(\mathbf{A} + \mathbf{B}) \leq \lambda_{i + \pi}(\mathbf{A}).
  $$
  其中等式成立当且仅当 $\mathbf{B}$ 是奇异的以及存在非零向量 $\mathbf{x} \in \mathbb{C}^n$，使得
  $$
  \mathbf{A}\mathbf{x} = \lambda_{i + \pi}(\mathbf{A}) \mathbf{x}, \quad \mathbf{B}\mathbf{x} =  0 \quad \text{ and } \quad (\mathbf{A} + \mathbf{B}) \mathbf{x} = \lambda_i(\mathbf{A} + \mathbf{B}) \mathbf{x}.
  $$
+ 对任意 $i = \nu + 1,  \cdots, n$，有
  $$
  \lambda_i(\mathbf{A} + \mathbf{B}) \geq \lambda_{i - \nu}(\mathbf{A}).
  $$
  其中等式成立当且仅当 $\mathbf{B}$ 是奇异的以及存在非零向量 $\mathbf{x} \in \mathbb{C}^n$，使得
  $$
  \mathbf{A}\mathbf{x} = \lambda_{i - \nu}(\mathbf{A}) \mathbf{x}, \quad \mathbf{B}\mathbf{x} =  0 \quad \text{ and } \quad (\mathbf{A} + \mathbf{B}) \mathbf{x} = \lambda_i(\mathbf{A} + \mathbf{B}) \mathbf{x}.
  $$

### 推论 2：考虑矩阵秩

如果 $\mathbf{B}$ 是奇异的且 $\operatorname{rank} (\mathbf{B}) = r$，那么
+ 对任意 $i = 1, \cdots, n - r$，有
  $$
  \lambda_i(\mathbf{A} + \mathbf{B}) \leq \lambda_{i + r}(\mathbf{A}).
  $$
  其中等式成立当且仅当 $\lambda_{n-r}(\mathbf{B}) = 0$ 以及存在非零向量 $\mathbf{x} \in \mathbb{C}^n$，使得
  $$
  \mathbf{A}\mathbf{x} = \lambda_{i + r}(\mathbf{A}) \mathbf{x}, \quad \mathbf{B}\mathbf{x} =  0 \quad \text{ and } \quad (\mathbf{A} + \mathbf{B}) \mathbf{x} = \lambda_i(\mathbf{A} + \mathbf{B}) \mathbf{x}.
  $$
+ 对任意 $i = \nu + 1,  \cdots, n$，有
  $$
  \lambda_i(\mathbf{A} + \mathbf{B}) \geq \lambda_{i - \nu}(\mathbf{A}).
  $$
  其中等式成立当且仅当 $\mathbf{B}$ 是奇异的以及存在非零向量 $\mathbf{x} \in \mathbb{C}^n$，使得
  $$
  \mathbf{A}\mathbf{x} = \lambda_{i - \nu}(\mathbf{A}) \mathbf{x}, \quad \mathbf{B}\mathbf{x} =  0 \quad \text{ and } \quad (\mathbf{A} + \mathbf{B}) \mathbf{x} = \lambda_i(\mathbf{A} + \mathbf{B}) \mathbf{x}.
  $$

### 推论 3：关于 Hermite 矩阵的 $1$ 阶秩 Hermite 扰动的交错定理

**(Interlacing theorem for a rank-one Hermitian perturbation of a Hermitian matrix)** 假定 $n \geq 2$，设 $\mathbf{A} \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，$\mathbf{z} \in \mathbb{C}^n$ 为非零向量。那么，
+ 有交错不等式
  $$
  \lambda_1(\mathbf{A}) \leq \lambda_1(\mathbf{A} + \mathbf{z}\mathbf{z}^{*}) \leq \lambda_2(\mathbf{A}) \leq \cdots \leq \lambda_{n-1}(\mathbf{A} + \mathbf{z}\mathbf{z}^{*}) \leq \lambda_n(\mathbf{A}) \leq \lambda_n(\mathbf{A} + \mathbf{z}\mathbf{z}^{*}).
  $$
  + 对某个 $i = 1, \cdots, n$，等式 $\lambda_i(\mathbf{A} + \mathbf{z}\mathbf{z}^{*}) = \lambda_i(\mathbf{A})$ 成立当且仅当存在非零向量 $\mathbf{x} \in \mathbb{C}^n$，使得
    $$
    \mathbf{A}\mathbf{x} = \lambda_{i}(\mathbf{A}) \mathbf{x}, \quad \mathbf{z}^* \mathbf{x} =  0 \quad \text{ and } \quad (\mathbf{A} + \mathbf{z}\mathbf{z}^{*}) \mathbf{x} = \lambda_i(\mathbf{A} + \mathbf{z}\mathbf{z}^{*}) \mathbf{x}.
    $$
  + 对某个 $i = 1, \cdots, n-1$，等式 $\lambda_i(\mathbf{A} + \mathbf{z}\mathbf{z}^{*}) = \lambda_{i + 1}(\mathbf{A})$ 成立当且仅当存在非零向量 $\mathbf{x} \in \mathbb{C}^n$，使得
    $$
    \mathbf{A}\mathbf{x} = \lambda_{i + 1}(\mathbf{A}) \mathbf{x}, \quad \mathbf{z}^* \mathbf{x} =  0 \quad \text{ and } \quad (\mathbf{A} + \mathbf{z}\mathbf{z}^{*}) \mathbf{x} = \lambda_i(\mathbf{A} + \mathbf{z}\mathbf{z}^{*}) \mathbf{x}.
    $$
+ 有交错不等式
  $$
  \lambda_1(\mathbf{A} - \mathbf{z}\mathbf{z}^{*}) \leq \lambda_1(\mathbf{A}) \leq \lambda_2(\mathbf{A} - \mathbf{z} \mathbf{z}^*) \leq \cdots \leq \lambda_{n-1}(\mathbf{A}) \leq \lambda_n(\mathbf{A} - \mathbf{z}\mathbf{z}^{*}) \leq \lambda_n(\mathbf{A}).
  $$
  + 对某个 $i = 1, \cdots, n$，等式 $\lambda_i(\mathbf{A} - \mathbf{z}\mathbf{z}^{*}) = \lambda_i(\mathbf{A})$ 成立当且仅当存在非零向量 $\mathbf{x} \in \mathbb{C}^n$，使得
    $$
    \mathbf{A}\mathbf{x} = \lambda_{i}(\mathbf{A}) \mathbf{x}, \quad \mathbf{z}^* \mathbf{x} =  0 \quad \text{ and } \quad (\mathbf{A} - \mathbf{z}\mathbf{z}^{*}) \mathbf{x} = \lambda_i(\mathbf{A} - \mathbf{z}\mathbf{z}^{*}) \mathbf{x}.
    $$
  + 对某个 $i = 2, \cdots, n$，等式 $\lambda_i(\mathbf{A} - \mathbf{z}\mathbf{z}^{*}) = \lambda_{i - 1}(\mathbf{A})$ 成立当且仅当存在非零向量 $\mathbf{x} \in \mathbb{C}^n$，使得
    $$
    \mathbf{A}\mathbf{x} = \lambda_{i - 1}(\mathbf{A}) \mathbf{x}, \quad \mathbf{z}^* \mathbf{x} =  0 \quad \text{ and } \quad (\mathbf{A} - \mathbf{z}\mathbf{z}^{*}) \mathbf{x} = \lambda_i(\mathbf{A} - \mathbf{z}\mathbf{z}^{*}) \mathbf{x}.
    $$

### 推论 4：单调定理

**(Monotonicity theorem)** 假定 $\mathbf{A}, \mathbf{B} \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵并且 $\mathbf{B}$ 半正定，那么对任意 $i = 1, \cdots, n$，有
$$
\lambda_i(\mathbf{A} + \mathbf{B}) \geq \lambda_{i}(\mathbf{A}).
$$
其中等式成立当且仅当 $\mathbf{B}$ 是奇异的以及存在非零向量 $\mathbf{x} \in \mathbb{C}^n$，使得
$$
\mathbf{A}\mathbf{x} = \lambda_{i}(\mathbf{A}) \mathbf{x}, \quad \mathbf{B}\mathbf{x} =  0 \quad \text{ and } \quad (\mathbf{A} + \mathbf{B}) \mathbf{x} = \lambda_i(\mathbf{A} + \mathbf{B}) \mathbf{x}.
$$

## 加边摄动

### Cauchy 交错定理

**(Cauchy interlacing theorem)** 假定 $\mathbf{B} \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，$y \in \mathbb{C}^n$ 以及 $a \in \mathbb{R}$。如果令
$$
\mathbf{A}=\left[\begin{array}{ll}
\mathbf{B} & \mathbf{y} \\
\mathbf{y}^{T} & a
\end{array}\right] \in \mathcal{M}_{n+1}(\mathbb{C}),
$$
那么有交错不等式
$$
\lambda_1(\mathbf{A}) \leq \lambda_1(\mathbf{B}) \leq \lambda_2(\mathbf{A}) \leq \cdots \leq \lambda_n(\mathbf{A}) \leq \lambda_n(\mathbf{B}) \leq \lambda_{n + 1}(\mathbf{A}).
$$
+ 对某个 $i = 1, \cdots, n$，等式 $\lambda_i(\mathbf{A}) = \lambda_i(\mathbf{B})$ 成立当且仅当存在非零向量 $\mathbf{z} \in \mathbb{C}^n$，使得
  $$
  \mathbf{B}\mathbf{z} = \lambda_{i}(\mathbf{B}) \mathbf{z}, \quad \mathbf{y}^*\mathbf{z} =  0 \quad \text{ and } \quad \mathbf{B} \mathbf{z} = \lambda_i(\mathbf{A}) \mathbf{z}.
  $$
+ 对某个 $i = 1, \cdots, n$，等式 $\lambda_{i+1}(\mathbf{A}) = \lambda_{i}(\mathbf{B})$ 成立当且仅当存在非零向量 $\mathbf{z} \in \mathbb{C}^n$，使得
  $$
  \mathbf{B}\mathbf{z} = \lambda_{i}(\mathbf{B}) \mathbf{z}, \quad \mathbf{y}^*\mathbf{z} =  0 \quad \text{ and } \quad \mathbf{B} \mathbf{z} = \lambda_{i+1}(\mathbf{A}) \mathbf{z}.
  $$

### 包容原理

**(Inclusion principle)** 假设 $\mathbf{A} = [a_{ij}]_{i,j=1}^n \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，分划成
$$
\mathbf{A}=\left[\begin{array}{ll}
\mathbf{B} & \mathbf{C} \\
\mathbf{C}^{*} & \mathbf{D}
\end{array}\right], \quad \text{ where } \mathbf{B} \in \mathcal{M}_m(\mathbb{C}), \ \mathbf{C} \in \mathcal{M}_{m, n - m}(\mathbb{C}), \ \mathbf{D} \in \mathcal{M}_{n - m}(\mathbb{C}).
$$
**结论 1：**对任意 $i = 1, \cdots, m$，有
$$
\lambda_i(\mathbf{A}) \leq \lambda_i(\mathbf{B}) \leq \lambda_{i + n - m}(\mathbf{A}).
$$
+ 其中下界中的不等式成立当且仅当存在非零向量 $\boldsymbol{\xi} \in \mathbb{C}^m$，使得
  $$
  \mathbf{B} \boldsymbol{\xi} = \lambda_{i}(\mathbf{B}) \boldsymbol{\xi}, \quad \mathbf{C}^*\boldsymbol{\xi} =  0 \quad \text{ and } \quad \mathbf{B} \boldsymbol{\xi} = \lambda_i(\mathbf{A}) \boldsymbol{\xi}.
  $$
+ 上界中的不等式成立当且仅当存在非零向量 $\boldsymbol{\xi} \in \mathbb{C}^m$，使得
  $$
  \mathbf{B}\boldsymbol{\xi} = \lambda_{i}(\mathbf{B}) \boldsymbol{\xi}, \quad \mathbf{C}^*\boldsymbol{\xi} =  0 \quad \text{ and } \quad \mathbf{B} \boldsymbol{\xi} = \lambda_{i+n-m}(\mathbf{A}) \boldsymbol{\xi}.
  $$

**结论 2：**

+ 假设对某组 $i = 1, \cdots, m$ 以及 $r = 1, \cdots, i$，有
  $$
  \lambda_{i-r+1}(\mathbf{A}) = \cdots =  \lambda_i(\mathbf{A}) = \lambda_i(\mathbf{B}),
  $$
  那么 $\lambda_{i-r+1}(\mathbf{B}) = \cdots = \lambda_i(\mathbf{B})$，并且存在标准正交向量 $\boldsymbol{\xi}_1, \cdots, \boldsymbol{\xi}_r \in \mathbb{C}^m$ 使得对所有的 $k = 1, \cdots, r$，有
  $$
  \mathbf{B}\boldsymbol{\xi}_k = \lambda_{i}(\mathbf{B}) \boldsymbol{\xi}_k \quad \text{ and } \quad \mathbf{C}^*\boldsymbol{\xi}_k = 0.
  $$
+ 假设对某组 $i = 1, \cdots, m$ 以及 $r = 1, \cdots, m - i + 1$，有
  $$
  \lambda_{i+ n - m}(\mathbf{A}) = \cdots =  \lambda_{i + n - m + r - 1}(\mathbf{A}) = \lambda_i(\mathbf{B}),
  $$
  那么 $\lambda_{i}(\mathbf{B}) = \cdots = \lambda_{i + r - 1}(\mathbf{B})$，并且存在标准正交向量 $\boldsymbol{\xi}_1, \cdots, \boldsymbol{\xi}_r \in \mathbb{C}^m$ 使得对所有的 $k = 1, \cdots, r$，有
  $$
  \mathbf{B}\boldsymbol{\xi}_k = \lambda_{i}(\mathbf{B}) \boldsymbol{\xi}_k \quad \text{ and } \quad \mathbf{C}^*\boldsymbol{\xi}_k = 0.
  $$

**结论 3：**有下列不等式成立：
$$
\sum_{i=1}^m \lambda_{i}(\mathbf{A}) \leq \sum_{i=1}^m a_{ii} \leq \sum_{i=1}^m \lambda_{n - m + i}(\mathbf{A})
$$
如果上述不等式中有一个不等号成为等号，那么就有 $\mathbf{C} = 0$，从而 $\mathbf{A} = \mathbf{B} \oplus \mathbf{D}$。

### Poincaré 分离定理

**(Poincaré separation theorem)** 假设 $\mathbf{A} \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，$\mathbf{u}_1, \cdots, \mathbf{u}_m \in \mathbb{C}^n$ 标准正交。令
$$
\mathbf{B}_m = \left [\mathbf{u}^*_i \mathbf{A} \mathbf{u}_j \right]_{i,j=1}^m \in \mathcal{M}_m(\mathbb{C}),
$$
那么对任意 $i = 1, \cdots, m$，有
$$
\lambda_i(\mathbf{A}) \leq \lambda_i(\mathbf{B}) \leq \lambda_{i + n - m}(\mathbf{A}).
$$
