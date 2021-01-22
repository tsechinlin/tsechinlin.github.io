---
title: Lemmas for Proofs in Random Matrix
date: 2020-12-29 19:46:26
categories: Random Matrix
mathjax: true
---

[Notes] <u>Spectral analysis of large dimensional random matrices</u> by Zhidong Bai & Jack W. Silverstein.

<!--more-->

## Lemmas - Matrix Analysis

### [MA-1]

Suppose that $\mathbf{A} \in \mathbb{C}^{n \times n}$ is a Hermitian matrix. Then for any $\mathbf{x} \in \mathbb{C}^{n}$ and $z = u + \mathrm{i} v \in \mathbb{C}_+$, we have
$$
\left | \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-2} \mathbf{x} \right | 
\leq \mathbf{x}^* \left [ \left ( \mathbf{A} - u \mathbf{I}_n \right )^{2} + v^2 \mathbf{I}_n \right ]^{-1} \mathbf{x} 
= \frac{1}{v} \Im \left [ \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \right ].
$$

> **证明**：由于 $\mathbf{A}$ 为 Hermite 矩阵，可以假设 $\mathbf{A} = \mathbf{U} \operatorname{diag} ( \lambda_1, \cdots, \lambda_n) \mathbf{U}^\*$，其中 $\mathbf{U} \in \mathbb{C}^{n \times n}$ 为酉矩阵，而 $\lambda_1, \cdots, \lambda_n \in \mathbb{R}$ 为 $\mathbf{A}$ 的实特征根。此时如果记 $\mathbf{U}^\* \mathbf{x} \triangleq \mathbf{y} = (y_1, \cdots, y_n)$，那么
> $$
> \begin{align*}
> \left | \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-2} \mathbf{x} \right | 
> & = \left | \mathbf{y}^* \operatorname{diag} \left( (\lambda_1 - z)^{-2}, \cdots, (\lambda_n - z)^{-2} \right) \mathbf{y} \right | \\
> & \leq \sum_{k=1}^n \left |(\lambda_k - z)^{-2} \right | | y_k |^2 
> = \sum_{k=1}^n \left [ (\lambda_k - u)^{2} + v^2 \right ]^{-1} | y_k |^2 \\
> & = \mathbf{x}^* \left [ \left ( \mathbf{A} - u \mathbf{I}_n \right )^{2} + v^2 \mathbf{I}_n \right ]^{-1} \mathbf{x}.
> \end{align*}
> $$
> 至于右端的等式，注意到
> $$
> \begin{align*}
> \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} 
> & = \mathbf{y}^* \operatorname{diag} \left( (\lambda_1 - z)^{-1}, \cdots, (\lambda_n - z)^{-1} \right) \mathbf{y} \\
> & \leq \sum_{k=1}^n (\lambda_k - z)^{-1} | y_k |^2 
> = \sum_{k=1}^n \frac{(\lambda_k - u) + \mathrm{i} v}{(\lambda_k - u)^{2} + v^2} | y_k |^2 ,
> \end{align*}
> $$
> 因此
> $$
> \Im \left [ \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \right ] 
> = v \sum_{k=1}^n \left [ (\lambda_k - u)^{2} + v^2 \right ]^{-1} | y_k |^2 
> = v \cdot \mathbf{x}^* \left [ \left ( \mathbf{A} - u \mathbf{I}_n \right )^{2} + v^2 \mathbf{I}_n \right ]^{-1} \mathbf{x}.
> $$

### [MA-2]

Let $\mathbf{A} \in \mathbb{C}^{n \times n}$ be a matrix with the form
$$
\mathbf{A} = \begin{bmatrix}
\mathbf{B} & \mathbf{a} \\
\mathbf{a}^* & c
\end{bmatrix},
$$
where $\mathbf{B} \in \mathbb{C}^{(n-1) \times (n-1)}$ and $\mathbf{a} \in \mathbb{C}^{n-1}$. If $\mathbf{B}$ is invertible with $d := c - \mathbf{a}^* \mathbf{B}^{-1} \mathbf{a} \not = 0$, then $\mathbf{A}$ is invertible with
$$
\mathbf{A}^{-1} 
= \begin{bmatrix}
\mathbf{B}^{-1} + \mathbf{B}^{-1} \mathbf{a} \mathbf{a}^* \mathbf{B}^{-1} / d & -\mathbf{B}^{-1} \mathbf{a} /d \\
- \mathbf{a}^* \mathbf{B}^{-1} / d & 1/d
\end{bmatrix}.
$$
Consequently,
$$
\operatorname{tr} \mathbf{A}^{-1} - \operatorname{tr} \mathbf{B}^{-1} = \frac{1 + \mathbf{a}_n^* \mathbf{B}^{-2} \mathbf{a}_n}{c - \mathbf{a}^* \mathbf{B}^{-1} \mathbf{a}}.
$$

> **证明**：考虑到
>$$
> \begin{bmatrix}
> \mathbf{I}_{n-1} & \mathbf{0} \\
> -\mathbf{a}^* \mathbf{B}^{-1} & 1
> \end{bmatrix}
> \begin{bmatrix}
> \mathbf{B} & \mathbf{a} \\
> \mathbf{a}^* & c
> \end{bmatrix}
> \begin{bmatrix}
> \mathbf{I}_{n-1} & - \mathbf{B}^{-1} \mathbf{a} \\
> \mathbf{0} & 1
> \end{bmatrix}
> = 
> \begin{bmatrix}
> \mathbf{B} & \mathbf{0} \\
> \mathbf{0} & d
> \end{bmatrix},
> $$
> 上式右端可逆，因此
> $$
> \begin{align*}
> \mathbf{A}^{-1} & = 
> \begin{bmatrix}
> \mathbf{I}_{n-1} & - \mathbf{B}^{-1} \mathbf{a} \\
> \mathbf{0} & 1
> \end{bmatrix}
> \begin{bmatrix}
> \mathbf{B} & \mathbf{0} \\
> \mathbf{0} & d
> \end{bmatrix}^{-1}
> \begin{bmatrix}
> \mathbf{I}_{n-1} & \mathbf{0} \\
> -\mathbf{a}^* \mathbf{B}^{-1} & 1
> \end{bmatrix} \\ 
> & = \begin{bmatrix}
> \mathbf{B}^{-1} + \mathbf{B}^{-1} \mathbf{a}_n d^{-1} \mathbf{a}_n^* \mathbf{B}^{-1} & -\mathbf{B}^{-1} \mathbf{a}_n d^{-1} \\
> - d^{-1} \mathbf{a}_n^* \mathbf{B}^{-1} & d^{-1}
> \end{bmatrix}.
> \end{align*}
> $$
> 
>最后，
> $$
> \operatorname{tr} \mathbf{A}^{-1} - \operatorname{tr} \mathbf{B}^{-1} = \frac{1}{d} + \frac{1}{d} \operatorname{tr} \left ( \mathbf{B}^{-1} \mathbf{a}_n \mathbf{a}_n^* \mathbf{B}^{-1} \right ) 
> = \frac{1}{d} \left ( 1 + \mathbf{a}_n^* \mathbf{B}^{-2} \mathbf{a}_n \right ).
> $$

### [MA-3]

Let $\mathbf{A} \in \mathbb{C}^{n \times n}$ be a Hermitian matrix and $\mathbf{A}_{k}$ be the $k$-th major submatrix of order $(n-1)$. Then for any $z = u + \mathrm{i} v \in \mathbb{C}_+$,
$$
\operatorname{tr} \left(\mathbf{A} - z \mathbf{I}_n \right)^{-1} - \operatorname{tr} \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-1} = \frac{1 + \boldsymbol{\alpha}_k^* \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-2} \boldsymbol{\alpha}_k}{a_{kk} - z - \boldsymbol{\alpha}_k^* \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-1} \boldsymbol{\alpha}_k},
$$
where $\boldsymbol{\alpha}_k$ denotes the $k$-th column of $\mathbf{A}$ with $a_{kk}$ removed. Consequently,
$$
\left | \operatorname{tr} \left(\mathbf{A} - z \mathbf{I}_n \right)^{-1} - \operatorname{tr} \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-1} \right | \leq \frac{1}{v}.
$$

> **证明**：首先，由于 $\mathbf{A}_{k}$ 为 Hermite 矩阵且 $z \in \mathbb{C}_+$，因此 $\mathbf{A}_k - z \mathbf{I}_{n-1}$ 可逆。另一方面，令
> $$
> d := a_{kk} - z - \boldsymbol{\alpha}_k^* \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-1} \boldsymbol{\alpha}_k,
> $$
> 借助引理 [MA-1] 以及 $v > 0$，可以得出
> $$
> \Im d 
> = - v - \Im \left [ \boldsymbol{\alpha}_k^* \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-1} \boldsymbol{\alpha}_k \right ] 
> \leq - v - v \left | \boldsymbol{\alpha}_k^* \left ( \mathbf{A}_{k} - z \mathbf{I}_{n-1} \right )^{-2} \boldsymbol{\alpha}_k \right | < 0.
> $$
> 于是 $d \not= 0$。这样一来，第一个结论可以通过引理 [MA-2] 得到。至于第二个结论，仅需注意到
> $$
> \begin{align*}
> \left | \operatorname{tr} \left(\mathbf{A} - z \mathbf{I}_n \right)^{-1} - \operatorname{tr} \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-1} \right | 
> & = \frac{1}{ \left | d \right |} \left | 1 + \boldsymbol{\alpha}_k^* \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-2} \boldsymbol{\alpha}_k \right | \\
> & \leq \frac{1}{\left | \Im d\right |} \left ( 1 + \left | \boldsymbol{\alpha}_k^* \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-2} \boldsymbol{\alpha}_k \right | \right ) 
> \leq \frac{1}{v}.
> \end{align*}
> $$

### [MA-4]

Suppose that $\mathbf{A} \in \mathbb{C}^{n \times n}$ is an invertible matrix. Let $\boldsymbol{\alpha}, \boldsymbol{\beta} \in \mathbb{C}^n$ be vectors with $1 + \boldsymbol{\beta}^{\*} \mathbf{A}^{-1} \boldsymbol{\alpha} \not= 0$. Then the matrix $\mathbf{A} + \boldsymbol{\alpha} \boldsymbol{\beta}^{\*}$ is invertible with
$$
\left(\mathbf{A}+\boldsymbol{\alpha} \boldsymbol{\beta}^{*}\right)^{-1}=\mathbf{A}^{-1}-\frac{\mathbf{A}^{-1} \boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1}}{1+\boldsymbol{\beta}^{*} \mathbf{A}^{-1} \boldsymbol{\alpha}}.
$$
Consequently,
$$
\operatorname{tr} \left(\mathbf{A}+\boldsymbol{\alpha} \boldsymbol{\beta}^{*}\right)^{-1} - \operatorname{tr} \mathbf{A}^{-1} 
= - \frac{\boldsymbol{\beta}^{*} \mathbf{A}^{-2} \boldsymbol{\alpha}}{1+\boldsymbol{\beta}^{*} \mathbf{A}^{-1} \boldsymbol{\alpha}}.
$$

> **证明**：记 $\mathbf{E} = \mathbf{A}^{-1} \boldsymbol{\alpha} \boldsymbol{\beta}^{\*} \mathbf{A}^{-1} / \left ( 1+\boldsymbol{\beta}^{\*} \mathbf{A}^{-1} \boldsymbol{\alpha} \right )$，那么
> $$
> \begin{align*}
> \left ( \mathbf{A}+\boldsymbol{\alpha} \boldsymbol{\beta}^{*} \right )
> \left ( \mathbf{A}^{-1}- \mathbf{E} \right )
> & = \mathbf{I}_n + \boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1} - \frac{\boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1} + \boldsymbol{\alpha} \left ( \boldsymbol{\beta}^{*} \mathbf{A}^{-1} \boldsymbol{\alpha} \right ) \boldsymbol{\beta}^{*} \mathbf{A}^{-1}}{1+\boldsymbol{\beta}^{*} \mathbf{A}^{-1} \boldsymbol{\alpha}} \\
> & = \mathbf{I}_n + \boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1} - \boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1} 
> = \mathbf{I}_n.
> \end{align*}
> $$
> 类似可证 $\left ( \mathbf{A}^{-1}- \mathbf{E} \right ) \left ( \mathbf{A}+\boldsymbol{\alpha} \boldsymbol{\beta}^{\*} \right ) = \mathbf{I}_n$。至于第二个等式，仅需注意到
> $$
> \operatorname{tr} \left [ \mathbf{A}^{-1} \boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1} \right ] 
> = \boldsymbol{\beta}^{*} \mathbf{A}^{-2} \boldsymbol{\alpha}.
> $$

### [MA-5]

Let $\mathbf{A} \in \mathbb{C}^{n \times n}$ be a Hermitian matrix and $\mathbf{x} \in \mathbb{C}^n$. Then for any $z = u + \mathrm{i} v \in \mathbb{C}_+$,
$$
\operatorname{tr} \left(\mathbf{A} + \mathbf{x} \mathbf{x}^* - z \mathbf{I}_n \right)^{-1} - \operatorname{tr} \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1} = \frac{\mathbf{x}^* \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-2} \mathbf{x}}{1 + \mathbf{x}^* \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1} \mathbf{x}},
$$
Consequently,
$$
\left | \operatorname{tr} \left(\mathbf{A} + \mathbf{x} \mathbf{x}^* - z \mathbf{I}_n \right)^{-1} - \operatorname{tr} \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1} \right | \leq \frac{1}{v}.
$$

> **证明**：仅需考虑 $\mathbf{x} \not= 0$ 的情形。首先由于 $\mathbf{A}$ 为 Hermite 矩阵且 $z \in \mathbb{C}_+$，因此 $\mathbf{A} - z \mathbf{I}_{n}$ 可逆。另一方面，令
> $$
> d := 1 + \mathbf{x}^* \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1} \mathbf{x},
> $$
> 借助引理 [MA-1] 以及 $v > 0$，可以得出
> $$
> \Im d 
> = \Im \left [ \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \right ]
> = v \cdot \mathbf{x}^* \left [ \left ( \mathbf{A} - u \mathbf{I}_n \right )^{2} + v^2 \mathbf{I}_n \right ]^{-1} \mathbf{x} > 0.
> $$
> 于是 $d \not= 0$。这样一来，第一个结论可以通过引理 [MA-4] 得到。至于第二个结论，再度应用引理 [MA-1] 即可：
> $$
> \begin{align*}
> \left | \operatorname{tr} \left(\mathbf{A} + \mathbf{x} \mathbf{x}^* - z \mathbf{I}_n \right)^{-1} - \operatorname{tr} \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1} \right | 
> & = \frac{1}{ \left | d \right |} \left | \mathbf{x}^* \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-2} \mathbf{x} \right | \\
> & \leq \frac{1}{\left | \Im d\right |} \left | \mathbf{x}^* \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-2} \mathbf{x} \right |
> \leq \frac{1}{v}.
> \end{align*}
> $$

## Lemmas - Convergence of Random Variables

## Lemmas - Probability Inequalities

## Lemmas - Levy Distance

## Lemmas - Stieltjes Transform
