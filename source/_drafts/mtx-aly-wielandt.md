---
title: mtx-aly-wielandt
tags: 
  - Eigenvalue
  - Hermitian Matrix
categories: Matrix Analysis
mathjax: true
---

## Hoffman-Wielandt 不等式

### 正规矩阵的特征值摄动

假设 $\mathbf{A}, B \in \mathcal{M}_n(\mathbb{C})$ 为正规矩阵，而 $\mathcal{S}_n$ 为集合 $\{ 1, \cdots, n \}$ 上的置换群，那么
$$
\min_{\pi \in \mathcal{S}_n} \sum_{i = 1}^n \left | \lambda_{\pi(i)} (\mathbf{A}) - \lambda_{i} (\mathbf{B}) \right |^2 
\leq \| \mathbf{A} - \mathbf{B} \|_F^2 
\leq \max_{\pi \in \mathcal{S}_n} \sum_{i = 1}^n \left | \lambda_{\pi(i)} (\mathbf{A}) - \lambda_{i} (\mathbf{B}) \right |^2.
$$

> **证明**：

### Hermite 矩阵的特征值摄动

假设 $\mathbf{A}, \mathbf{B} \in \mathcal{M}_n(\mathbb{C})$ 为 Hermite 矩阵，其特征值 $\lambda_{i}(\mathbf{A})$ 与 $\lambda_i(\mathbf{B})$ 都分别按降序排列，此处 $1 \leq i \leq n$。那么
$$
\sum_{i = 1}^n \left | \lambda_i (\mathbf{A}) - \lambda_{i} (\mathbf{B}) \right |^2 
\leq \| \mathbf{A} - \mathbf{B} \|_F^2.
$$

> **证明**：

### 一般矩阵的奇异值摄动

假设 $\mathbf{A}, \mathbf{B} \in \mathcal{M}_{m,n}(\mathbb{C})$，其奇异值 $\sigma_{i}(\mathbf{A})$ 与 $\sigma_i(\mathbf{B})$ 都分别按降序排列，此处 $1 \leq i \leq r = \min \{ m, n \}$。那么
$$
\sum_{i = 1}^n \left | \sigma_i (\mathbf{A}) - \sigma_{i} (\mathbf{B}) \right |^2 
\leq \| \mathbf{A} - \mathbf{B} \|_F^2.
$$

> **证明**：
>
> 设 $\mathbf{A}$ 的奇异值分解为 $\mathbf{A} = \sum_{i=1}^r \sigma_i(\mathbf{A}) \mathbf{u}_{i} \mathbf{v}_{i}^\*$，其中
>
> + $\mathbf{u}_{1}, \cdots, \mathbf{u}_{r} \in \mathbb{C}^m$ 满足 $\mathbf{u}_{i}^\*\mathbf{u}_{j} = \delta_{ij}$，
> + $\mathbf{v}_{1}, \cdots, \mathbf{v}_{r} \in \mathbb{C}^n$ 满足 $\mathbf{v}_{i}^\*\mathbf{v}_{j} = \delta_{ij}$。
>
> 注意到 $\mathbf{A} \mathbf{v}_i = \sigma_i(\mathbf{A}) \mathbf{u}_i$ 以及 $\mathbf{A}^{\*} \mathbf{u}_i = \sigma_i(\mathbf{A}) \mathbf{v}_i$，因此如果令
> $$
> \widehat{\mathbf{A}} := \begin{bmatrix}
> \mathbf{0}_{m \times m} & \mathbf{A} \\
> \mathbf{A}^* & \mathbf{0}_{n \times n}
> \end{bmatrix},
> $$
> 那么 $\widehat{\mathbf{A}}$ 为 Hermite 矩阵，并且对 $1 \leq i \leq r$，有
> $$
> \widehat{\mathbf{A}} \begin{bmatrix} \mathbf{u}_i \\ \mathbf{v}_i \end{bmatrix} 
> = \sigma_i(\mathbf{A}) \begin{bmatrix} \mathbf{u}_i \\ \mathbf{v}_i \end{bmatrix}
> \quad \text{ and } \quad
> \widehat{\mathbf{A}} \begin{bmatrix} \mathbf{u}_i \\ - \mathbf{v}_i \end{bmatrix} 
> = - \sigma_i(\mathbf{A}) \begin{bmatrix} \mathbf{u}_i \\ - \mathbf{v}_i \end{bmatrix}.
> $$
> 即 $\sigma_i(\mathbf{A})$ 和 $-\sigma_i(\mathbf{A})$ 都是 $\widehat{\mathbf{A}}$ 的特征值。另一方面，如果 $m \geq n$，那么存在 $\mathbf{u}_{r+1}, \cdots, \mathbf{u}_{m} \in \mathbb{C}^m$ 使得 $\mathbf{U} = [\mathbf{u}_{1}, \cdots, \mathbf{u}_{m}]$ 为酉矩阵。此时对 $r + 1 \leq i \leq m$，有
> $$
> \widehat{\mathbf{A}} \begin{bmatrix} \mathbf{u}_i \\ \mathbf{0}_{n \times 1} \end{bmatrix} 
> = \begin{bmatrix} \mathbf{0}_{m \times 1} \\ \mathbf{0}_{n \times 1} \end{bmatrix},
> $$
> 因此 $\widehat{\mathbf{A}}$ 的特征值按降序排列为
> $$
> \lambda_{i}(\widehat{\mathbf{A}}) = \begin{cases}
> \sigma_i(\mathbf{A}), & \quad \text{ if } 1 \leq i \leq r, \\
> 0, & \quad \text{ if } r + 1 \leq i \leq m+n-r, \\
> -\sigma_{m + n - i + 1}(\mathbf{A}), & \quad \text{ if } m+n-r \leq i \leq m+n.
> \end{cases}
> $$
> 上述结论在 $m < n$ 时也成立。类似地，定义 Hermite 矩阵
> $$
> \widehat{\mathbf{B}} := \begin{bmatrix}
> \mathbf{0}_{m \times m} & \mathbf{B} \\
> \mathbf{B}^* & \mathbf{0}_{n \times n}
> \end{bmatrix},
> $$
> 对 $\widehat{\mathbf{A}}$ 以及 $\widehat{\mathbf{B}}$ 应用 &&&&，可以得到
> $$
> 2 \sum_{i = 1}^r \left | \sigma_i (\mathbf{A}) - \sigma_{i} (\mathbf{B}) \right |^2
> = \sum_{i = 1}^{m+n} \left | \lambda_i (\widehat{\mathbf{A}}) - \lambda_{i} (\widehat{\mathbf{B}}) \right |^2
> \leq \left \| \widehat{\mathbf{A}} - \widehat{\mathbf{B}} \right \|_F^2
> = 2 \| \mathbf{A} - \mathbf{B} \|_F^2.
> $$

