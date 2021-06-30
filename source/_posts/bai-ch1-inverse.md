---
title: Lemmas - Inverse of Matrices
date: 2020-12-29 19:46:26
categories: Random Matrix
mathjax: true
---

[Notes] <u>Spectral analysis of large dimensional random matrices</u> by Zhidong Bai & Jack W. Silverstein.

<!--more-->

## [IM-1]

Suppose that $\mathbf{A} \in \mathbb{C}^{n \times n}$ is a Hermitian matrix. Then for any $z = u + \mathrm{i} v \in \mathbb{C}_+$, we have
$$
\big \| \left ( \mathbf{A} - z \mathbf{I}_n \right)^{-1} \big \|_{\mathrm{op}} \leq \frac{1}{v}.
$$


> **Proof**: 
> $$
> \begin{align*}
> \big \| \left ( \mathbf{A} - z \mathbf{I}_n \right)^{-1} \big \|_{\mathrm{op}}^2 
> & = \max_{\mathbf{x} \in \mathbb{S}^{n-1}} \big \| \left ( \mathbf{A} - z \mathbf{I}_n \right)^{-1} \mathbf{x} \big \|_{2}^2
> = \max_{\mathbf{x} \in \mathbb{S}^{n-1}} \ \mathbf{x}^* \left ( \mathbf{A} - \bar{z} \mathbf{I}_n \right)^{-1} \left ( \mathbf{A} - z \mathbf{I}_n \right)^{-1} \mathbf{x} \\
> &= \max_{\mathbf{x} \in \mathbb{S}^{n-1}} \ \mathbf{x}^* \big [ \left ( \mathbf{A} - u \mathbf{I}_n \right )^{2} + v^2 \mathbf{I}_n \big ]^{-1} \mathbf{x} \leq \frac{1}{v^2}.
> \end{align*}
> $$

## [IM-2]

Assume that $\mathbf{A} \in \mathbb{C}^{n \times n}$ is a nonnegative definite Hermitian matrix, and $m(z)$ is the Stieltjes transform of a p.d.f. Then, for any $z = u + \mathrm{i} v \in \mathbb{C}_+$,
$$
\big \|\left( m(z) \mathbf{A}+\mathbf{I}_n\right)^{-1}\big\|_{\mathrm{op}} \leq \max \left ( 2, \frac{4}{v} \|\mathbf{A}\|_{\mathrm{op}} \right ).
$$

> **Proof**:
>
> Since $\mathbf{A}$ is Hermitian and nonnegative definite, we can write $\mathbf{A} = \mathbf{U} \operatorname{diag} ( \lambda_1, \cdots, \lambda_n) \mathbf{U}^\*$, where $\mathbf{U} \in \mathbb{C}^{n \times n}$ is unitary and $\lambda_k \geq 0$ for each $k \in [n]$. In this case,
> $$
> \left(m(z) \mathbf{A}+\mathbf{I}_n\right)^{-1} = \mathbf{U} \operatorname{diag} \left( (m(z) \lambda_1 + 1)^{-1}, \cdots, ( m(z)\lambda_n + 1)^{-1} \right) \mathbf{U}^*.
> $$
> By **[ST-?]**, we know that for any $\lambda \geq 0$, it holds that
> $$
> \frac{1}{|m(z) \lambda + 1|} \leq \max \left ( 2, \frac{4}{v} \lambda \right ),
> $$
> which implies that
> $$
> \begin{align*}
> \big\| \left(m(z) \mathbf{A}+\mathbf{I}_n\right)^{-1}\big\|_{\mathrm{op}}^2 
> & = \max_{\mathbf{x} \in \mathbb{S}^{n-1}} \big \| \left(m(z) \mathbf{A}+\mathbf{I}_n\right)^{-1} \mathbf{x} \big \|_2^2
> \leq \max_{k \in [n]} \frac{1}{|m(z) \lambda_k + 1|^2} \\
> & \leq \max_{k \in [n]} \left \{ \max \left ( 4, \frac{16}{v^2} \lambda_k^2 \right ) \right \} 
> = \max \left ( 4, \frac{16}{v^2} \|\mathbf{A}\|_{\mathrm{op}}^2 \right ).
> \end{align*}
> $$

## [IM-3]

Suppose that $\mathbf{A} \in \mathbb{C}^{n \times n}$ is a Hermitian matrix. Then for any $\mathbf{x} \in \mathbb{C}^{n}$ and $z = u + \mathrm{i} v \in \mathbb{C}_+$, we have
$$
\big | \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-2} \mathbf{x} \big | 
\leq \mathbf{x}^* \big [ \left ( \mathbf{A} - u \mathbf{I}_n \right )^{2} + v^2 \mathbf{I}_n \big ]^{-1} \mathbf{x} 
= \frac{1}{v} \Im \big [ \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big ].
$$

+ If $\mathbf{x} \not = \mathbf{0}$, then
    $$
    \Im \big [ \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big ] > 0.
    $$

+ If $\mathbf{A}$ is nonnegative definite, then
    $$
    \Im \big [ z \cdot \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big ] \geq 0.
    $$

> **Proof**: 
>
> Since $\mathbf{A}$ is Hermitian, we can write $\mathbf{A} = \mathbf{U} \operatorname{diag} ( \lambda_1, \cdots, \lambda_n) \mathbf{U}^\*$, where $\mathbf{U} \in \mathbb{C}^{n \times n}$ is unitary and $\lambda_k \in \mathbb{R}$ for each $k \in [n]$. Let $\mathbf{U}^\* \mathbf{x} \triangleq \mathbf{y} = (y_1, \cdots, y_n)$.
>
> **[Part 1]** The first inequality follows from
> $$
> \begin{align*}
> \big | \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-2} \mathbf{x} \big | 
> & = \left | \mathbf{y}^* \operatorname{diag} \left( (\lambda_1 - z)^{-2}, \cdots, (\lambda_n - z)^{-2} \right) \mathbf{y} \right | \\
> & \leq \sum_{k=1}^n \left | \frac{1}{(\lambda_k - z)^2} \right | | y_k |^2 
> = \sum_{k=1}^n \frac{1}{(\lambda_k - u)^{2} + v^2} | y_k |^2 \\
> & = \mathbf{x}^* \big [ \left ( \mathbf{A} - u \mathbf{I}_n \right )^{2} + v^2 \mathbf{I}_n \big ]^{-1} \mathbf{x}.
> \end{align*}
> $$
> **[Part 2]** As for the equality in the right hand side, note that we have
> $$
> \begin{align*}
> \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} 
> & = \mathbf{y}^* \operatorname{diag} \left( (\lambda_1 - z)^{-1}, \cdots, (\lambda_n - z)^{-1} \right) \mathbf{y} \\
> & = \sum_{k=1}^n \frac{1}{\lambda_k - z} | y_k |^2 
> = \sum_{k=1}^n \frac{(\lambda_k - u) + \mathrm{i} v}{(\lambda_k - u)^{2} + v^2} | y_k |^2 .
> \end{align*}
> $$
> Therefore,
> $$
> \Im \big [ \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big ] 
> = v \sum_{k=1}^n \frac{1}{(\lambda_k - u)^{2} + v^2} | y_k |^2 
> = v \cdot \mathbf{x}^* \big [ \left ( \mathbf{A} - u \mathbf{I}_n \right )^{2} + v^2 \mathbf{I}_n \big ]^{-1} \mathbf{x}.
> $$
> **[Part 3]** The matrix $\big [ \left ( \mathbf{A} - u \mathbf{I}_n \right )^{2} + v^2 \mathbf{I}_n \big ]^{-1}$ is positive definite since its eigenvalues are all positive,
> $$
> \frac{1}{(\lambda_k - u)^{2} + v^2} > 0, \quad \text{ for } k \in [n].
> $$
> Therefore, when $\mathbf{x} \not = \mathbf{0}$, by the equality in part 2 we know that
> $$
> \Im \big [ \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big ] = v \cdot \mathbf{x}^* \big [ \left ( \mathbf{A} - u \mathbf{I}_n \right )^{2} + v^2 \mathbf{I}_n \big ]^{-1} \mathbf{x} > 0.
> $$
> **[Part 4]** Note that
> $$
> \begin{align*}
> z \cdot \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} 
> & = \mathbf{y}^* \operatorname{diag} \left( (\lambda_1 - z)^{-1}, \cdots, (\lambda_n - z)^{-1} \right) \mathbf{y} \\
> & = \sum_{k=1}^n \frac{z}{\lambda_k - z} | y_k |^2 
> = \sum_{k=1}^n \left ( \frac{\lambda_k}{\lambda_k - z} - 1 \right ) | y_k |^2 .
> \end{align*}
> $$
> When $\mathbf{A}$ is nonnegative definite, we have $\lambda_k \geq 0$ for each $k \in [n]$, which implies
> $$
> \Im \big [ z \cdot \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big ] =  \sum_{k=1}^n \frac{\lambda_k v}{(\lambda_k - u)^{2} + v^2} | y_k |^2 \geq 0.
> $$

## [IM-4]

Let $\mathbf{A} \in \mathbb{C}^{n \times n}$ be a matrix taking the form
$$
\mathbf{A} = \begin{bmatrix}
\mathbf{B} & \mathbf{a} \\
\mathbf{a}^* & c
\end{bmatrix},
$$
where $\mathbf{B} \in \mathbb{C}^{(n-1) \times (n-1)}$ and $\mathbf{a} \in \mathbb{C}^{n-1}$. If $\mathbf{B}$ is invertible and $d := c - \mathbf{a}^* \mathbf{B}^{-1} \mathbf{a} \not = 0$, then $\mathbf{A}$ is invertible with
$$
\mathbf{A}^{-1} 
= \begin{bmatrix}
\mathbf{B}^{-1} + \mathbf{B}^{-1} \mathbf{a} d^{-1} \mathbf{a}^* \mathbf{B}^{-1} & -\mathbf{B}^{-1} \mathbf{a} d^{-1} \\
- d^{-1} \mathbf{a}^* \mathbf{B}^{-1} & d^{-1}
\end{bmatrix}.
$$
Consequently,
$$
\operatorname{tr} \mathbf{A}^{-1} - \operatorname{tr} \mathbf{B}^{-1} = \frac{1 + \mathbf{a}^* \mathbf{B}^{-2} \mathbf{a}}{c - \mathbf{a}^* \mathbf{B}^{-1} \mathbf{a}}.
$$

> **Proof**: 
>
> Diagonalizing the block matrix $\mathbf{A}$ by
> $$
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
> \end{bmatrix}.
> $$
> Since $d > 0$, we can take inverse for the both sides, which gives
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
> \mathbf{B}^{-1} + \mathbf{B}^{-1} \mathbf{a} d^{-1} \mathbf{a}^* \mathbf{B}^{-1} & -\mathbf{B}^{-1} \mathbf{a} d^{-1} \\
> - d^{-1} \mathbf{a}^* \mathbf{B}^{-1} & d^{-1}
> \end{bmatrix}.
> \end{align*}
> $$
>
> For the second statement, note that the trace of $\mathbf{A}^{-1}$ can be written as the sum of traces of its diagonal blocks,
> $$
> \operatorname{tr} \mathbf{A}^{-1} = \operatorname{tr} \mathbf{B}^{-1} + \frac{1}{d} \operatorname{tr} \left ( \mathbf{B}^{-1} \mathbf{a} \mathbf{a}^* \mathbf{B}^{-1} \right ) + \frac{1}{d}
> = \operatorname{tr} \mathbf{B}^{-1} + \frac{1}{d} \left ( 1 + \mathbf{a}^* \mathbf{B}^{-2} \mathbf{a} \right ).
> $$

## [IM-5]

Let $\mathbf{A} \in \mathbb{C}^{n \times n}$ be a Hermitian matrix and $\mathbf{A}_{k}$ be the $k$-th principle submatrix of order $(n-1)$, i.e. the submatrix obtained by removing the $k$-th row and column. Then for any $z = u + \mathrm{i} v \in \mathbb{C}_+$,
$$
\left | \operatorname{tr} \left(\mathbf{A} - z \mathbf{I}_n \right)^{-1} - \operatorname{tr} \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-1} \right | \leq \frac{1}{v}.
$$
> **Proof**:
>
> Note that $\mathbf{A}_{k}$ is also Hermitian. Since $z \in \mathbb{C}_+$, the matrix $\mathbf{A}_k - z \mathbf{I}_{n-1}$ is invertible. Define
> $$
> d := a_{kk} - z - \boldsymbol{\alpha}_k^* \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-1} \boldsymbol{\alpha}_k,
> $$
> where $\boldsymbol{\alpha}_k$ denotes the $k$-th column of $\mathbf{A}$ with $a_{kk}$ removed.
>
> Note $a_{kk} \in \mathbb{R}$ since $\mathbf{A}$ is Hermitian. Hence, by **[IM-3]**, we have
> $$
> \Im d 
> = - v - \Im \left [ \boldsymbol{\alpha}_k^* \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-1} \boldsymbol{\alpha}_k \right ] 
> \leq - v < 0.
> $$
> which implies $d \not= 0$. Applying **[IM-4]**, we obtain
> $$
> \operatorname{tr} \left(\mathbf{A} - z \mathbf{I}_n \right)^{-1} - \operatorname{tr} \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-1} = \frac{1}{d} \big [ 1 + \boldsymbol{\alpha}_k^* \left( \mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-2} \boldsymbol{\alpha}_k \big ].
> $$
> Consequently,
> $$
> \begin{align*}
> \left | \operatorname{tr} \left(\mathbf{A} - z \mathbf{I}_n \right)^{-1} - \operatorname{tr} \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-1} \right | 
> & \leq \frac{1 + \big | \boldsymbol{\alpha}_k^* \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-2} \boldsymbol{\alpha}_k \big |}{ \left | \Im d \right |} \\ 
> & \leq \frac{1 + \big | \boldsymbol{\alpha}_k^* \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-2} \boldsymbol{\alpha}_k \big |}{v + \Im \big [ \boldsymbol{\alpha}_k^* \left(\mathbf{A}_k - z \mathbf{I}_{n-1} \right)^{-1} \boldsymbol{\alpha}_k \big ] } \leq \frac{1}{v} .
> \end{align*}
> $$

## [IM-6]

Suppose that $\mathbf{A} \in \mathbb{C}^{n \times n}$ is an invertible matrix. Let $\boldsymbol{\alpha}, \boldsymbol{\beta} \in \mathbb{C}^n$ be vectors with $1 + \boldsymbol{\beta}^{\*} \mathbf{A}^{-1} \boldsymbol{\alpha} \not= 0$. Then the matrix $\mathbf{A} + \boldsymbol{\alpha} \boldsymbol{\beta}^{\*}$ is invertible with
$$
\left(\mathbf{A}+\boldsymbol{\alpha} \boldsymbol{\beta}^{*}\right)^{-1}=\mathbf{A}^{-1}-\frac{\mathbf{A}^{-1} \boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1}}{1+\boldsymbol{\beta}^{*} \mathbf{A}^{-1} \boldsymbol{\alpha}}.
$$
Consequently, we have
$$
\boldsymbol{\beta}^* \left(\mathbf{A}+\boldsymbol{\alpha} \boldsymbol{\beta}^{*}\right)^{-1} = \frac{1}{1+\boldsymbol{\beta}^{*} \mathbf{A}^{-1} \boldsymbol{\alpha}} \boldsymbol{\beta}^{*} \mathbf{A}^{-1},
$$
and
$$
\operatorname{tr} \left(\mathbf{A}+\boldsymbol{\alpha} \boldsymbol{\beta}^{*}\right)^{-1} - \operatorname{tr} \mathbf{A}^{-1} 
= - \frac{\boldsymbol{\beta}^{*} \mathbf{A}^{-2} \boldsymbol{\alpha}}{1+\boldsymbol{\beta}^{*} \mathbf{A}^{-1} \boldsymbol{\alpha}}.
$$

> **Proof**: 
>
> Note that
> $$
> \begin{align*}
> \left ( \mathbf{A}+\boldsymbol{\alpha} \boldsymbol{\beta}^{*} \right )
> \left ( \mathbf{A}^{-1} - \frac{\mathbf{A}^{-1} \boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1}}{1+\boldsymbol{\beta}^{*} \mathbf{A}^{-1} \boldsymbol{\alpha}} \right )
> & = \mathbf{I}_n + \boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1} - \frac{\boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1} + \boldsymbol{\alpha} \left ( \boldsymbol{\beta}^{*} \mathbf{A}^{-1} \boldsymbol{\alpha} \right ) \boldsymbol{\beta}^{*} \mathbf{A}^{-1}}{1+\boldsymbol{\beta}^{*} \mathbf{A}^{-1} \boldsymbol{\alpha}} \\
> & = \mathbf{I}_n + \boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1} - \boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1} 
> = \mathbf{I}_n.
> \end{align*}
> $$
> Similarly, it can be shown that
> $$
> \left ( \mathbf{A}^{-1} - \frac{\mathbf{A}^{-1} \boldsymbol{\alpha} \boldsymbol{\beta}^{*} \mathbf{A}^{-1}}{1+\boldsymbol{\beta}^{*} \mathbf{A}^{-1} \boldsymbol{\alpha}} \right ) \left ( \mathbf{A}+\boldsymbol{\alpha} \boldsymbol{\beta}^{*} \right ) = \mathbf{I}_n.
> $$
> Therefore, the first statement follows.

## [IM-7]

Let $\mathbf{A}, \mathbf{B} \in \mathbb{C}^{n \times n}$ be Hermitian matrices and $\mathbf{x} \in \mathbb{C}^n$. For any $z = u + \mathrm{i} v \in \mathbb{C}_+$, define
$$
\mathbf{D} := \left(\mathbf{A} + \mathbf{x} \mathbf{x}^* - z \mathbf{I}_n \right)^{-1} - \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1}.
$$
Then we have
$$
\left | \operatorname{tr} \mathbf{D} \right |  \leq \frac{1}{v},
$$
and
$$
\left | \operatorname{tr} (\mathbf{B} \mathbf{D}) \right |  \leq \frac{1}{v} \| \mathbf{B} \|_{\mathrm{op}}.
$$

> **Proof**:
>
> We only need to consider the case where $\mathbf{x} \not= \mathbf{0}$.
>
> Since $\mathbf{A}$ is Hermitian and $z \in \mathbb{C}_+$, we know that $\mathbf{A} - z \mathbf{I}_{n}$ is invertible. By **[IM-3]**, we have
> $$
> \big | 1 + \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big |
> \geq \Im \big [ \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big ] > 0.
> $$
> Therefore, by **[IM-6]** we have
> $$
> \mathbf{D}
> = - \frac{\left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1} \mathbf{x} \mathbf{x}^{*} \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1}}{1+\mathbf{x}^{*} \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1} \mathbf{x}}.
> $$
> **[Part 1]** Using **[IM-3]**, we can obtain
> $$
> \left | \operatorname{tr} \mathbf{D} \right | 
> = \frac{\big | \mathbf{x}^* \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-2} \mathbf{x} \big |}{\big | 1 + \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big |}
> \leq \frac{\big | \mathbf{x}^* \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-2} \mathbf{x} \big |}{\Im \big [ \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big ]} \leq \frac{1}{v}.
> $$
> **[Part 2]**
> $$
> \left | \operatorname{tr} (\mathbf{B} \mathbf{D}) \right | 
> = \frac{\big | \mathbf{x}^* \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1} \mathbf{B} \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1} \mathbf{x} \big |}{\big | 1 + \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big |}
> \leq \frac{\| \mathbf{B} \|_{\mathrm{op}} \big \| \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1} \mathbf{x} \big \|_2 \big \| \left(\mathbf{A} - \bar{z} \mathbf{I}_{n} \right)^{-1} \mathbf{x} \big \|_2 }{\Im \big [ \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big ]}.
> $$
> Note that
> $$
> \left(\mathbf{A} - \bar{z} \mathbf{I}_{n} \right)^{-1} \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1} = \big [ \left(\mathbf{A} - u \mathbf{I}_{n} \right)^2 + v^2 \mathbf{I}_{n} \big ]^{-1} = \left(\mathbf{A} - z \mathbf{I}_{n} \right)^{-1} \left(\mathbf{A} - \bar{z} \mathbf{I}_{n} \right)^{-1}.
> $$
> Therefore, by using **[IM-3]** again, we have
> $$
> \left | \operatorname{tr} (\mathbf{B} \mathbf{D}) \right | 
> \leq \frac{\mathbf{x}^* \big [ \left(\mathbf{A} - u \mathbf{I}_{n} \right)^2 + v^2 \mathbf{I}_{n} \big ]^{-1} \mathbf{x}}{\Im \big [ \mathbf{x}^* \left ( \mathbf{A} - z \mathbf{I}_n \right )^{-1} \mathbf{x} \big ]} \| \mathbf{B} \|_{\mathrm{op}} = \frac{1}{v} \| \mathbf{B} \|_{\mathrm{op}}.
> $$

## [IM-8]

Assume that $\mathbf{A}, \mathbf{B} \in \mathbb{C}^{n \times n}$ are Hermitian matrices. Let $z_1, z_2 \in \mathbb{C}_+$ with $\min ( \Im z_1, \Im z_2) \geq v > 0$. Define
$$
\mathbf{D} := \left ( \mathbf{A} - z_1 \mathbf{I}_n \right)^{-1} - \left(\mathbf{A} - z_2 \mathbf{I}_{n} \right)^{-1}.
$$
Then,
$$
\left | \operatorname{tr} (\mathbf{B} \mathbf{D}) \right | 
\leq \frac{n |z_1 - z_2|}{v^2} \| \mathbf{B} \|_{\mathrm{op}} ,
$$
and for any $\mathbf{x} \in \mathbb{C}^n$, it holds that
$$
\left | \mathbf{x}^* \mathbf{B} \mathbf{D} \mathbf{x} \right | \leq \frac{|z_1 - z_2|}{v^2} \| \mathbf{B} \|_{\mathrm{op}} \| \mathbf{x} \|_2^2.
$$

> **Proof**:
>
> Note that the matrix $\mathbf{D}$ can be written as
> $$
> \begin{align*}
> \mathbf{D} 
> & = \left ( \mathbf{A} - z_1 \mathbf{I}_n \right)^{-1}  \big [ \left(\mathbf{A} - z_2 \mathbf{I}_{n} \right) - \left ( \mathbf{A} - z_1 \mathbf{I}_n \right) \big ] \left(\mathbf{A} - z_2 \mathbf{I}_{n} \right)^{-1} \\
> & = (z_1 - z_2) \left ( \mathbf{A} - z_1 \mathbf{I}_n \right)^{-1} \left(\mathbf{A} - z_2 \mathbf{I}_{n} \right)^{-1}.
> \end{align*}
> $$
> Therefore, by **[IM-1]** we have
> $$
> \| \mathbf{D} \|_{\mathrm{op}} 
> = |z_1 - z_2| \big \| \left ( \mathbf{A} - z_1 \mathbf{I}_n \right)^{-1} \big \|_{\mathrm{op}} \big \| \left ( \mathbf{A} - z_2 \mathbf{I}_n \right)^{-1} \big \|_{\mathrm{op}}
> \leq \frac{|z_1 - z_2|}{\Im z_1 \Im z_2} \leq \frac{|z_1 - z_2|}{v^2}.
> $$
> The two statements follow from $\left | \operatorname{tr} (\mathbf{B} \mathbf{D}) \right | 
> \leq n \lVert \mathbf{B} \rVert_{\mathrm{op}} \lVert \mathbf{D} \rVert_{\mathrm{op}}$ and $\left | \mathbf{x}^* \mathbf{B} \mathbf{D} \mathbf{x} \right | \leq \lVert \mathbf{D} \rVert_{\mathrm{op}} \lVert \mathbf{B} \rVert_{\mathrm{op}} \lVert \mathbf{x} \rVert_2^2$.

## [IM-9]

Assume that $\mathbf{A}, \mathbf{B} \in \mathbb{C}^{n \times n}$ are Hermitian matrices with $\mathbf{A}$ nonnegative definite. For $z = u + \mathrm{i} v \in \mathbb{C}_+$, let $m_1(z), m_2(z)$ be Stieltjes transforms of any two p.d.f.'s. Define
$$
\mathbf{D} := \left ( m_{1}(z) \mathbf{A}+\mathbf{I}_n \right)^{-1} - \left ( m_{2}(z) \mathbf{A}+\mathbf{I}_n \right)^{-1}.
$$
Then,
$$
\left | \operatorname{tr} (\mathbf{B} \mathbf{D}) \right | 
\leq n |m_{1}(z) - m_{2}(z)| \| \mathbf{A} \|_{\mathrm{op}} \| \mathbf{B} \|_{\mathrm{op}} \max \left ( 4, \frac{16}{v^2} \|\mathbf{A}\|_{\mathrm{op}}^2 \right ),
$$
and for any $\mathbf{x} \in \mathbb{C}^n$, it holds that
$$
\left | \mathbf{x}^* \mathbf{B} \mathbf{D} \mathbf{x} \right |
\leq |m_{1}(z) - m_{2}(z)| \| \mathbf{A} \|_{\mathrm{op}} \| \mathbf{B} \|_{\mathrm{op}} \| \mathbf{x} \|_2^2 \max \left ( 4, \frac{16}{v^2} \|\mathbf{A}\|_{\mathrm{op}}^2 \right ).
$$

> **Proof**:
>
> Note that the matrix $\mathbf{D}$ can be written as
> $$
> \begin{align*}
> \mathbf{D} 
> & = \left ( m_{1}(z) \mathbf{A}+\mathbf{I}_n \right)^{-1} \big [ \left ( m_{2}(z) \mathbf{A}+\mathbf{I}_n \right) - \left ( m_{1}(z) \mathbf{A}+\mathbf{I}_n \right) \big ] \left ( m_{2}(z) \mathbf{A}+\mathbf{I}_n \right)^{-1} \\
> & = (m_{2}(z) - m_{1}(z)) \left ( m_{1}(z) \mathbf{A}+\mathbf{I}_n \right)^{-1} \mathbf{A} \left ( m_{2}(z) \mathbf{A}+\mathbf{I}_n \right)^{-1}.
> \end{align*}
> $$
> Therefore, by **[IM-2]** we have
> $$
> \begin{align*}
> \| \mathbf{D} \|_{\mathrm{op}} 
> & \leq |m_{1}(z) - m_{2}(z)| \big \| \left ( m_{1}(z) \mathbf{A}+\mathbf{I}_n \right)^{-1} \big \|_{\mathrm{op}} \| \mathbf{A} \|_{\mathrm{op}}  \big \| \left ( m_{2}(z) \mathbf{A}+\mathbf{I}_n \right)^{-1} \big \|_{\mathrm{op}} \\
> & \leq |m_{1}(z) - m_{2}(z)| \| \mathbf{A} \|_{\mathrm{op}} \max \left ( 4, \frac{16}{v^2} \|\mathbf{A}\|_{\mathrm{op}}^2 \right ).
> \end{align*}
> $$
> The two statements follow from $\left | \operatorname{tr} (\mathbf{B} \mathbf{D}) \right | 
>\leq n \lVert \mathbf{B} \rVert_{\mathrm{op}} \lVert \mathbf{D} \rVert_{\mathrm{op}}$ and $\left | \mathbf{x}^* \mathbf{B} \mathbf{D} \mathbf{x} \right | \leq \lVert \mathbf{D} \rVert_{\mathrm{op}} \lVert \mathbf{B} \rVert_{\mathrm{op}} \lVert \mathbf{x} \rVert_2^2$.


