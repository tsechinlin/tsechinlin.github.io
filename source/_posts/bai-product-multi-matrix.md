---
title: Enumerative Combinatorics with Multiple Matrices
date: 2021-01-20 17:26:14
tags: 
  - Multiple Matrix
  - Graph Theory
  - Enumerative Combinatorics
categories: Random Matrix
mathjax: true
---

[Notes] <u>Spectral analysis of large dimensional random matrices</u> by Zhidong Bai & Jack W. Silverstein.

<!--more-->

## Definitions and Notations

### 多重指标 Multiple Index

Let $t \in \mathbb{Z}_+$ and $n_1, \cdots, n_t \in \mathbb{Z}_+$ be positive integers. The tuple $\mathbf{n} = (n_1, \cdots, n_t)$ is called a **multiple dimension**.

If $\mathbf{i} = (i_1, \cdots, i_t)$ is a tuple taking values in $[\mathbf{n}] := [n_1] \times \cdots \times [n_t]$, then $\mathbf{i}$ is called a **multiple index** with dimension $\mathbf{n}$.

### 多重向量 Multiple Vector

A **multiple vector** $\mathbf{a} = ( a_{\mathbf{i}} )$ with dimension $\mathbf{n} = (n_1, \cdots, n_t)$ is a mapping from $[\mathbf{n}]$ to $\mathbb{C}$, that is, a collection of numbers indexed by $\mathbf{i} \in [\mathbf{n}]$.

The **norm** of the multiple vector $\mathbf{a}$ is defined by
$$
\| \mathbf{a} \| := \left ( \sum_{\mathbf{i} \in [\mathbf{n}]} | a_{\mathbf{i}} |^2 \right )^{1/2}.
$$

### 多重矩阵 Multiple Matrix

A **multiple matrix** $\mathbf{A} = ( a_{\mathbf{i}, \mathbf{j}} )$ with dimension $\mathbf{m} = (m_1, \cdots, m_s)$ and $\mathbf{n} = (n_1, \cdots, n_t)$ is a mapping from $[\mathbf{m}] \times [\mathbf{n}]$ to $\mathbb{C}$, that is, a collection of numbers indexed by $\mathbf{i} \in [\mathbf{m}]$ and $\mathbf{j} \in [\mathbf{n}]$.

The **norm** of the multiple matrix $\mathbf{A}$ is defined by
$$
\|\mathbf{A}\|
: = \sup_{\| \mathbf{g} \| = 1, \ \| \mathbf{h} \| = 1} 
\left|\sum_{\mathbf{i} \in [\mathbf{m}], \ \mathbf{j} \in [\mathbf{n}]} a_{\mathbf{i}, \mathbf{j}} g_{\mathbf{i}} h_{\mathbf{j}}\right|,
$$

here $\mathbf{g}$ and $\mathbf{h}$ are multiple vectors with dimensions $\mathbf{m}$ and $\mathbf{n}$, respectively.

+ The norm of the multiple matrix $\mathbf{A}$ can be equivalently defined by
    $$
    \|\mathbf{A}\|^2
    = \sup_{\| \mathbf{g} \| = 1} \sum_{\mathbf{j}} 
    \left|\sum_{\mathbf{i}} a_{\mathbf{i}, \mathbf{j}} g_{\mathbf{i}} \right|^2
    = \sup_{\| \mathbf{h} \| = 1} \sum_{\mathbf{i}} 
    \left|\sum_{\mathbf{j}} a_{\mathbf{i}, \mathbf{j}} h_{\mathbf{j}} \right|^2.
    $$
+ For any $\mathbf{g} \in \mathbb{C}^{[\mathbf{m}]}$ and $\mathbf{h} \in \mathbb{C}^{[\mathbf{n}]}$, we have 
    $$
    \sum_{\mathbf{j}} \left|\sum_{\mathbf{i}} a_{\mathbf{i}, \mathbf{j}} g_{\mathbf{i}} \right|^2 
    \leq \| \mathbf{A} \|^2 \| \mathbf{g} \|^2
    \quad \text{ and } \quad
    \sum_{\mathbf{i}} \left|\sum_{\mathbf{j}} a_{\mathbf{i}, \mathbf{j}} h_{\mathbf{j}} \right|^2 
    \leq \| \mathbf{A} \|^2 \| \mathbf{h} \|^2.
    $$

> **注**：
>
> 对于任意固定的满足 $\| \mathbf{g} \| = 1$ 的多重向量 $\mathbf{g} \in \mathbb{C}^{[\mathbf{m}]}$，如果 $\sum_{\mathbf{v}} \left| \sum_{\mathbf{u}} a_{\mathbf{u}, \mathbf{v}} g_{\mathbf{u}} \right|^2 \not= 0$，那么为了达到 $\|\mathbf{A}\|$ 定义中的最大值，只需取
> $$
> h_{\mathbf{j}} = \frac{\sum_{\mathbf{i}} a_{\mathbf{i}, \mathbf{j}} g_{\mathbf{i}}}{\sqrt{\sum_{\mathbf{v}}\left|\sum_{\mathbf{u}} a_{\mathbf{u}, \mathbf{v}} g_{\mathbf{u}}\right|^{2}}}.
> $$
> 同理，对于任意固定的满足 $\| \mathbf{h} \| = 1$ 的多重向量 $\mathbf{h} \in \mathbb{C}^{[\mathbf{n}]}$，如果 $\sum_{\mathbf{u}} \left|\sum_{\mathbf{v}} a_{\mathbf{u}, \mathbf{v}} h_{\mathbf{v}} \right|^2 \not= 0$，那么为了达到 $\|\mathbf{A}\|$ 定义中的最大值，只需取
> $$
> g_{\mathbf{i}}=\frac{\sum_{\mathbf{j}} a_{\mathbf{i}, \mathbf{j}} h_{\mathbf{j}}}{\sqrt{\sum_{\mathbf{u}}\left|\sum_{\mathbf{v}} a_{\mathbf{u}, \mathbf{v}} h_{\mathbf{v}}\right|^{2}}}.
> $$

### 有向图 Directed  Graph

Let $G = (V, E, f \times g)$ be a **directed graph** with $t$ vertices and $k$ edges, that is,

+ $V = [t] = \{ 1, \cdots, t \}$.
+ $E = \big \{ e_j : j \in [k] \big \} = \{ e_1, \cdots, e_k \}$.
+ $f \times g$ is a mapping from $[k]$ to $V \times V$, with the property that, for each $j \in [k]$, the $j$-th edge $e_j = \big( f(j), g(j) \big )$ goes from the vertex $f(j)$ to the vertex $g(j)$.

### 维度一致性约束 Consistent Dimension Restriction

Let $\big \{ \mathbf{T}^{(j)} : j \in [k] \big \}$ be a collection of matrices corresponding to the $k$ edges. We say that $\big \{ \mathbf{T}^{(j)} \big \}$ is subject to the **consistent dimension restriction** given by $G$ if

+ for each $a \in V$, there exists a positive integers $m_a$ associated with the vertex $a$, such that
+ for each $j \in [k]$, the dimension of matrix $\mathbf{T}^{(j)}$ is $m_{f(j)} \times m_{g(j)}$.

## $V_1$-based Graphs

### 图结构 Graph Structure

Consider a directed graph $G = (V, E, f \times g)$ with the following structures.

+ The vertex set of $G$ can be partitioned into $V = V_1 + V_2 + V_3$, where $V_1 = \{ 1, \cdots, s \}$, $V_2 = \{ s + 1, \cdots, t_1 \}$ and $V_3 = \{ t_1 + 1, \cdots, t \}$. Here $1 \leq s \leq t_1 < t$.
+ The end vertex of each edge is in $V_3$, i.e., for each $j \in [k]$, we have $g(j) \in V_3$.
+ The edges initiated from $V_1$, $V_2$, or $V_3$ are called the first, second, or third type edges, respectively. Without loss of generality, assume that 
    + the first $k_1$ edges of the graph $G$ are of the first type,
    + and the next $k_2$ edges are of the second type,
    + the last $k − k_1 − k_2$ are of the third type.
+ The graph $G$ is $V_1$-based, in the sense that
    + For any $a \in V_1$, there exists some vertex $b \in V_3$ such that $(a,b) \in E$.
    + For any $b \in V_3$, there exists some vertex $a \in V_1$ such that $(a,b) \in E$.

Below we assume that $\big \{ \mathbf{T}^{(j)} : j \in [k] \big \}$ is a collection of matrices satisfying the consistent dimension restriction given by $G$.

### 图关联多重矩阵 Graph-Associated Multiple Matrix

The **graph-associated multiple matrix** $\mathbf{T}(G)$ is defined by
$$
\mathbf{T}(G)_{\mathbf{u}, \mathbf{v}} = 
\prod_{j=1}^{k_1} t^{(j)}_{u_{f(j)}, v_{g(j)}} 
\prod_{j= k_1 + 1}^{k} t^{(j)}_{v_{f(j)}, v_{g(j)}}.
$$
where

+ $\mathbf{u} = (u_1, \cdots, u_s) \in [m_1] \times \cdots \times [m_{s}]$ is the left index,
+ $\mathbf{v} = (\mathbf{v}_1, \mathbf{v}_2)$ is the right index, with $\mathbf{v}_1 = (v_{s+1}, \cdots, v_{t_1})$ taking values in $[m_{s+1}] \times \cdots \times [m_{t_1}]$, and $\mathbf{v}_2 = (v_{t_1+1}, \cdots, v_{t})$ taking values in $[m_{t_1+1}] \times \cdots \times [m_{t}]$.

### Lemma [GM-1]

Assume that $\mathbf{A} = \big ( a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \big )$ is a multiple matrix with left index $\mathbf{i}$ independent of $\mathbf{u}, \mathbf{v}_1$ and $\mathbf{v}_2$. 

Define the product of $\mathbf{A}$ and $\mathbf{T} (G)$ by
$$
\big ( \mathbf{A} \cdot \mathbf{T} (G) \big )_{\mathbf{i}, \mathbf{v}} 
= \sum_{\mathbf{u}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \mathbf{T}(G)_{\mathbf{u}, \mathbf{v}}.
$$

Then, we have
$$
\left \| \mathbf{A} \cdot \mathbf{T} (G) \right \|
\leq \left \| \mathbf{A} \right \| \cdot \prod_{j= 1}^{k} \left \| \mathbf{T}^{(j)} \right \|_{\mathrm{op}}.
$$

### Proof for Lemma [GM-1]

> **证明**：
>
> 首先注意到，对任意的 $u \in [m_{f(j)}]$ 及 $v \in [m_{g(j)}]$，有
> $$
> \left \| \mathbf{T}^{(j)} \right \|_{\mathrm{op}} = \max_{\| \mathbf{x} \|_2 = 1, \ \| 
> \mathbf{y} \|_2 = 1} \left | \big \langle \mathbf{T}^{(j)} \mathbf{x}, \ \mathbf{y} \big \rangle \right |
> \geq \left | t^{(j)}_{u, v} \right |,
> $$
> 结合多重矩阵范数的定义，可以推出
> $$
> \begin{align*}
> \big \| \mathbf{A} \cdot \mathbf{T} (G) \big \|^2
> & = \sup_{\| \mathbf{g} \| = 1} \sum_{\mathbf{v}} 
> \left|\sum_{\mathbf{i}} g_{\mathbf{i}} \cdot \big ( \mathbf{A} \cdot \mathbf{T} (G) \big )_{\mathbf{i}, \mathbf{v}} \right|^2 \\
> & = \sup_{\| \mathbf{g} \| = 1} \sum_{\mathbf{v}_1} \sum_{\mathbf{v}_2} 
> \left|\sum_{\mathbf{i}} g_{\mathbf{i}} \sum_{\mathbf{u}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \mathbf{T}(G)_{\mathbf{u}, \mathbf{v}} \right|^2 \\
> & \leq \sup_{\| \mathbf{g} \| = 1} \sum_{\mathbf{v}_1} \sum_{\mathbf{v}_2} 
> \left|\sum_{\mathbf{i}} g_{\mathbf{i}} \sum_{\mathbf{u}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \prod_{j=1}^{k_1} t^{(j)}_{u_{f(j)}, v_{g(j)}} \right|^2 \cdot \prod_{j=k_1 + 1}^{k} \left \| \mathbf{T}^{(j)} \right \|_{\mathrm{op}}^2.
> \end{align*}
> $$
> 以下假定矩阵 $\mathbf{T}^{(j)}$ 的奇异值分解为 $\mathbf{T}^{(j)} = \mathbf{H}^{(j)} \boldsymbol{\Sigma}^{(j)} \big ( \boldsymbol{\Xi}^{(j)} \big )^*$，换言之，
> $$
> t_{u,v}^{(j)}=\sum_{\ell=1}^{r_{j}} \sigma_{\ell}^{(j)} \eta_{u,\ell}^{(j)} \overline{\xi}_{v,\ell}^{(j)},
> \quad \text{ for } u \in [m_{f(j)}] \text{ and } v \in [m_{g(j)}],
> $$
> 其中 $r_j = m_{f(j)} \wedge m_{g(j)}$。
>
> 记 $w_j = v_{g(j)}$ 并令 $\mathbf{w} = (w_1, \cdots, w_{k_1})$，考虑到对每个 $V_3$ 中的顶点，都至少有一条从 $V_1$ 出发的边以其为终点，因此对 $\mathbf{v}_2 \in [m_{t_1+1}] \times \cdots \times [m_t]$ 求和就相当于对 $\mathbf{w} \in [m_{g(1)}] \times \cdots \times [m_{g(k_1)}]$ 求和，但附加约束
> $$
> w_j = w_{j^\prime} 
> \quad \text{ if } \quad
> g(j) = g(j^\prime).
> $$
> 当待求和项非负时，去除上述约束可以使总和变大，因此
> $$
> \begin{align*}
> \sum_{\mathbf{v}_1} \sum_{\mathbf{v}_2} 
> \left|\sum_{\mathbf{i}} g_{\mathbf{i}} \sum_{\mathbf{u}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \prod_{j=1}^{k_1} t^{(j)}_{u_{f(j)}, v_{g(j)}} \right|^2
> & \leq \sum_{\mathbf{v}_1} \sum_{\mathbf{w}} 
> \left| \sum_{\mathbf{i}, \mathbf{u}} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \prod_{j=1}^{k_1} t^{(j)}_{u_{f(j)}, w_j} \right|^2 \\
> & \triangleq \sum_{\mathbf{v}_1} \sum_{\mathbf{w}} 
> \left| \sum_{\mathbf{i}, \mathbf{u}} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \sum_{\boldsymbol{\ell}} \sigma_{\boldsymbol{\ell}} \eta_{\mathbf{u}, \boldsymbol{\ell}} \overline{\xi}_{\mathbf{w}, \boldsymbol{\ell}} \right|^2,
> \end{align*}
> $$
>
> 其中多重指标 $\boldsymbol{\ell} = (\ell_1, \cdots, \ell_{k_1}) \in [r_1] \times \cdots \times [r_{k_1}]$，另外
> $$
> \sigma_{\boldsymbol{\ell}} 
> : = \prod_{j=1}^{k_1} \sigma_{\ell_j}^{(j)} 
> , \quad
> \eta_{\mathbf{u}, \boldsymbol{\ell}} 
> : = \prod_{j=1}^{k_1} \eta_{u_{f(j)}, \ell_j}^{(j)}, 
> \quad \text{ and } \quad 
> \xi_{\mathbf{w}, \boldsymbol{\ell}} 
> : = \prod_{j=1}^{k_1} \xi_{w_j, \ell_j}^{(j)}.
> $$
> 注意到 $\boldsymbol{\Xi}^{(j)}$ 为酉矩阵，因此对任意的 $\boldsymbol{\ell}$ 以及 $\boldsymbol{\ell}^\prime$，有
> $$
> \sum_{\mathbf{w}} \overline{\xi}_{\mathbf{w}, \boldsymbol{\ell}} \xi_{\mathbf{w}, \boldsymbol{\ell}^\prime}
> = \sum_{\mathbf{w}} \prod_{j=1}^{k_1} \overline{\xi}_{w_j, \ell_j}^{(j)} \xi_{w_j, \ell_j^\prime}^{(j)}
> = \prod_{j=1}^{k_1} \sum_{w_j} \overline{\xi}_{w_j, \ell_j}^{(j)} \xi_{w_j, \ell_j^\prime}^{(j)}
> = \prod_{j=1}^{k_1} \delta_{\ell_j, \ell_j^\prime}
> = \delta_{\boldsymbol{\ell}, \boldsymbol{\ell}^\prime}.
> $$
> 由于 $\sigma_{\boldsymbol{\ell}} \sum_{\mathbf{i}, \mathbf{u}} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \eta_{\mathbf{u}, \boldsymbol{\ell}}$ 与指标 $\mathbf{w}$ 无关， 利用上式以及 $\sigma_{\boldsymbol{\ell}} \leq \prod_{j=1}^{k_1} \left \| \mathbf{T}^{(j)} \right \|_{\mathrm{op}}$ 可以推出
> $$
> \begin{align*}
> \sum_{\mathbf{v}_1} \sum_{\mathbf{w}}
> \left| \sum_{\boldsymbol{\ell}} \overline{\xi}_{\mathbf{w}, \boldsymbol{\ell}} \left ( \sigma_{\boldsymbol{\ell}} \sum_{\mathbf{i}, \mathbf{u}} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \eta_{\mathbf{u}, \boldsymbol{\ell}} \right ) \right|^2
> & = \sum_{\mathbf{v}_1} \sum_{\boldsymbol{\ell}} \sigma_{\boldsymbol{\ell}}^2 \left | \sum_{\mathbf{i}, \mathbf{u}} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \eta_{\mathbf{u}, \boldsymbol{\ell}} \right |^2 \\
> & \leq \prod_{j = 1}^{k_1} \left \| \mathbf{T}^{(j)} \right \|_{\mathrm{op}}^2 \sum_{\mathbf{v}_1} \sum_{\boldsymbol{\ell}} \left | \sum_{\mathbf{i}, \mathbf{u}} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \eta_{\mathbf{u}, \boldsymbol{\ell}} \right |^2.
> \end{align*}
> $$
> 注意此处对于求和指标 $\boldsymbol{\ell}$ 的取值范围是 $[\mathbf{r}] = [r_1] \times \cdots \times [r_{k_1}]$。考虑到待求和项非负，因此将 $\boldsymbol{\ell}$ 的取值范围扩大为 $[\mathbf{m}_f] = [m_{f(1)}] \times \cdots \times [m_{f(k_1)}]$ 可以使总和变大。
>
> 考虑到 $\mathbf{H}^{(j)}$ 也是酉矩阵，因此对任意的 $\mathbf{u}$ 以及 $\mathbf{u}^\prime$，有
> $$
> \sum_{\boldsymbol{\ell} \in [\mathbf{m}_f]} \eta_{\mathbf{u}, \boldsymbol{\ell}} \overline{\eta}_{\mathbf{u}^\prime, \boldsymbol{\ell}}
> = \sum_{\boldsymbol{\ell} \in [\mathbf{m}_f]} \prod_{j=1}^{k_1} \eta_{u_{f(j)}, \ell_j}^{(j)} \overline{\eta}_{u_{f(j)}^\prime, \ell_j}^{(j)} 
> = \prod_{j=1}^{k_1} \sum_{\ell_j \in [m_{f(j)}]} \eta_{u_{f(j)}, \ell_j}^{(j)} \overline{\eta}_{u_{f(j)}^\prime, \ell_j}^{(j)}
> = \prod_{j=1}^{k_1} \delta_{u_{f(j)}, u_{f(j)}^\prime}
> = \delta_{\mathbf{u}, \mathbf{u}^\prime}.
> $$
> 这里最后一个等号成立是因为根据约定，$\big \{ f(j): j = 1, \cdots, k_1 \big \} = V_1$。
>
> 于是，结合上述两条论断，可以推出
> $$
> \begin{align*}
> \sum_{\mathbf{v}_1} \sum_{\boldsymbol{\ell} \in [\mathbf{r}]} \left | \sum_{\mathbf{u}} \eta_{\mathbf{u}, \boldsymbol{\ell}} \sum_{\mathbf{i}} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \right |^2
> & \leq \sum_{\mathbf{v}_1} \sum_{\boldsymbol{\ell} \in [\mathbf{m}_f]} \left | \sum_{\mathbf{u}} \eta_{\mathbf{u}, \boldsymbol{\ell}} \sum_{\mathbf{i}} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \right |^2 \\
> & = \sum_{\mathbf{v}_1} \sum_{\mathbf{u}} \left | \sum_{\mathbf{i}} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{u}, \mathbf{v}_1)} \right |^2
> \leq \| \mathbf{A} \|^2.
> \end{align*}
> $$
> 综上所述，原命题得证。

## Hierarchical Graphs

### 图结构 Graph Structure

Consider a directed graph $G = (V, E, f \times g)$ with the following structures.

+ $G$ has more than two vertices, and every edge of $G$ is part of a directional path from vertex $1$ to $2$.
+ The graph $G$ is **direction-consistent**, that is, it has no directional cycles.
+ Vertex $1$ meets with only arrow tails and vertex $2$ meets with only arrow heads, and all other vertices connect with both arrow heads and tails.
+ The degree of vertex $1$ is one, that is, there is only one edge adjacent with the vertex $1$.

Below we assume that $\big \{ \mathbf{T}^{(j)} : j \in [k] \big \}$ is a collection of matrices satisfying the consistent dimension restriction given by $G$.

### 图关联矩阵 Graph-Associated Matrix

The **graph-associated matrix** $\mathbf{T}(G)$ is a $m_1 \times m_2$ dimensional matrix defined by
$$
\mathbf{T}(G)_{i_1, i_2} = \sum_{i_a: a \in V \backslash \{ 1,2 \}} \prod_{j=1}^k t_{i_{f(j)}, i_{g(j)}}^{(j)}.
$$

### Lemma [GM-2]

The operator norm of the graph-associated matrix $\mathbf{T}(G)$ satisfies
$$
\left \| \mathbf{T}(G) \right \|_{\mathrm{op}} \leq \prod_{j= 1}^{k} \left \| \mathbf{T}^{(j)} \right \|_{\mathrm{op}}.
$$

### 层级描述 Hierarchical Description

By the structure of $G$, we can define a **height function** $h: V \to \mathbb{N}$ reflecting the hierarchical attributes of vertices.

+ $h(1) = 0$.
+ For a given vertex $a > 1$, there must be one but may be several directional paths from $1$ to $a$. 
    Define $h(a)$ to be the maximum number of edges among all the directional paths from $1$ to $a$.

For $\ell \in \mathbb{N}$, define the **contour sets** $H(\ell) = \{ a \in V: h(a) = \ell \}$, and let $\ell_0 = \max \{ \ell \in \mathbb{N}: H(\ell) \not= \varnothing \}$.

+ For $\ell \not= \ell^\prime$, we have $H(\ell) \cap H{(\ell^\prime)} = \varnothing$.
+ For any fixed $1 \leq \ell \leq \ell_0$ and any $b \in H{(\ell)}$, we can find a vertex $a \in H(\ell-1)$ such that $(a, b) \in E$.

For $\ell \in \mathbb{N}$, define the **level sets** $L(\ell) = \big \{ a \in V: h(a) \leq \ell \big \}$.

### 等高子图 Contour Subgraphs

For $2 \leq \ell \leq \ell_0$, consider the subgraph $G_H(\ell)$ induced by the edges with end vertex in $H(\ell)$.

Note that the vertices in this subgraph can be divided into two categories.

+ The first category involves the vertices that will not appear in $G_H(\ell^\prime)$ for any $\ell^\prime > \ell$,
    $$
    V(\ell) = 
    \left \{ a \in L(\ell - 1) \left | \
    \begin{array}{ll}
    \exists b \in H(\ell), & (a, b) \in E \\
    \forall c \in V \backslash L(\ell), & (a, c) \notin E
    \end{array}
    \right \} \right . .
    $$

+ The second category includes the vertices that may be used by $G_H(\ell^\prime)$ for some $\ell^\prime > \ell$,
    $$
    W(\ell) = H(\ell) +
    \left \{ a \in L(\ell - 1) \left | \
    \begin{array}{l}
    \exists b \in H(\ell), & (a, b) \in E \\
    \exists c \in V \backslash L(\ell), & (a, c) \in E
    \end{array}
    \right \} \right. .
    $$

**Properties**:

+ **[Property 1]** $V(\ell) \cap W(\ell) = \varnothing$ for all $2 \leq \ell \leq \ell_0$.

+ **[Property 2]** For any edge $e_j$, it holds that
    $$
    g(j) \in H(\ell)
    \quad \Leftrightarrow \quad
    \begin{cases}
    f(j) \in V(\ell) + W(\ell), \\ 
    g(j) \in W(\ell).
    \end{cases}
    $$

**Graph-Associated Multiple Matrix**

Now define the multiple indices
$$
\mathbf{v}(\ell) = (i_a)_{a \in V(\ell)} \quad \text{ and } \quad
\mathbf{w}(\ell) = (i_a)_{a \in W(\ell)},
$$
where $i_a$ takes values in $[m_a]$.

By the discussion above, we can introduce the multiple matrix associated with the subgraph $G_H(\ell)$, with left index $\mathbf{v}(\ell)$ and right index $\mathbf{w}(\ell)$,
$$
\mathbf{H}^{(\ell)}_{\mathbf{v}(\ell), \mathbf{w}(\ell)}
= \prod_{g(j) \in H(\ell)} t_{i_{f(j)}, i_{g(j)}}^{(j)}.
$$

### 水平子图 Level Subgraphs

For $1 \leq \ell \leq \ell_0$, consider the subgraph $G_L(\ell)$ induced by the edges with end vertex in $L(\ell)$.

Note that the set of vertices in $G_L(\ell)$ is exactly $L(\ell)$.

Again, $L(\ell)$ can be divided into two categories depending on whether they are used by contour subgraphs with higher level. Below vertex $1$ will be treated as a free vertex.

+ The first category involves the vertices that will appear in $G_H(\ell^\prime)$ for some $\ell^\prime > \ell$,
    $$
    U(\ell) = H(\ell) + \big \{ a \in L(\ell-1) : \exists c \in V \backslash L(\ell) \text{ such that } (a, c) \in E \big \}.
    $$
    By assumptions on the graph $G$, we know that $1 \notin U(\ell)$ for any $1 \leq \ell \leq \ell_0$.

+ The second category includes all the vertices that will not be used by $G_H(\ell^\prime)$ for any $\ell^\prime > \ell$, except the vertex $1$,
    $$
    R(\ell) = L(\ell) \backslash \big ( U(\ell) + \{ 1\} \big ).
    $$
    In other words,
    $$
    R(\ell) = \big \{ a \in L(\ell-1) : a \not= 1 \text{ and } \forall c \in V \backslash L(\ell) \text{, it holds that } (a, c) \in E \big \}.
    $$

**Properties**: For $2 \leq \ell \leq \ell_0$, 

+ **[Property 3]** $R(\ell - 1) \cap \big ( V(\ell) + W(\ell) \big ) = \varnothing$.

+ **[Property 4]** $R(\ell) = R(\ell - 1) + V(\ell)$.

+ **[Property 5]** $U(\ell - 1) = V(\ell) + \big ( W(\ell) \backslash H(\ell) \big ) + Q(\ell)$, where
    $$
    Q(\ell) :=
    \left \{ a \in L(\ell - 1) \left | \
    \begin{array}{ll}
    \forall b \in H(\ell), & (a, b) \notin E \\
    \exists c \in V \backslash L(\ell), & (a, c) \in E
    \end{array}
    \right \} \right . .
    $$

+ **[Property 6]** $U(\ell) = H(\ell) + \big ( W(\ell) \backslash H(\ell) \big ) + Q(\ell)$.

> **性质 3**：按照定义，$V(\ell) + W(\ell)$ 构成了子图 $G_H(\ell)$ 的顶点集，而 $R(\ell - 1)$ 中的顶点不能出现在 $\ell^\prime \geq \ell$ 的子图 $G_H(\ell^\prime)$ 中，因此这两个集合不相交。
>
> **性质 4**：注意到 $1 \notin V(\ell)$，并且 $V(\ell)$ 中的点不会出现在 $\ell^\prime >\ell$ 的子图 $G_H(\ell^\prime)$ 之中，因此 $V(\ell) \subset R(\ell)$。至于 $R(\ell - 1) \subset R(\ell)$，则是显然的。
>
> 另一方面，对于任意的 $a \in R(\ell)$，如果从 $a$ 出发可以连接到 $H(\ell)$ 中的某个顶点，那么 $a \in V(\ell)$。否则，$a$ 无法出现在 $G_H(\ell)$ 中，这意味着 $a \in R(\ell - 1)$。
>
> **性质 5**：考察任意的 $a \in U(\ell - 1)$，从 $a$ 出发必定可以连接到 $V \backslash L(\ell - 1)$ 中的某个顶点。
>
> + 如果 $a$ 无法连接到 $V \backslash L(\ell)$ 中的任意一个顶点，那么 $a \in V(\ell)$。
> + 否则，$a$ 可以连接到 $V \backslash L(\ell)$ 中的某个顶点，
>     + 如果 $a$ 也可以连接到 $H(\ell)$ 中的某个顶点，那么 $a \in W(\ell) \backslash H(\ell)$。
>     + 如果 $a$ 无法连接到 $H(\ell)$ 中的任意一个顶点，那么 $a \in Q(\ell)$。
>
> **性质 6**：考察任意的 $a \in U(\ell)$。
>
> + 如果 $h(a) = \ell$，那么 $a \in H(\ell)$。
> + 如果 $h(a) < \ell$，那么 $a$ 可以连接到 $V \backslash L(\ell)$ 中的某个顶点。
>     + 此时如果 $a$ 可以连接到 $H(\ell)$ 中的某个顶点，那么 $a \in W(\ell) \backslash H(\ell)$。
>     + 否则 $a$ 与 $H(\ell)$ 中的任意一个顶点都不相连，此时 $a \in Q(\ell)$。

**Graph-Associated Multiple Matrix**

Define the multiple indices
$$
\mathbf{r}(\ell) = (i_a)_{a \in R(\ell)} \quad \text{ and } \quad
\mathbf{u}(\ell) = (i_a)_{a \in U(\ell)},
$$
where $i_a$ takes values in $[m_a]$.

By the discussion above, we can define the multiple matrix associated with the subgraph $G_L(\ell)$, with left index $i_1$ and right index $\mathbf{u}(\ell)$,
$$
\mathbf{L}^{(\ell)}_{i_1, \mathbf{u}(\ell)}
= \sum_{\mathbf{r}(\ell)} \prod_{g(j) \in L(\ell)} t_{i_{f(j)}, i_{g(j)}}^{(j)}.
$$

### Proof for Lemma [GM-2]

> **证明**：
>
> 由 $G$ 的结构，显然有 $U(\ell_0) = \{ 2\}$ 以及 $R(\ell_0) = V \backslash \{ 1, 2 \} = \{ 3, \cdots, t \}$，因此 $\mathbf{T}(G)$ 就是 $\mathbf{L}^{(\ell_0)}$，而 $\left \| \mathbf{T}(G) \right \|_{\mathrm{op}}$ 其实就是 $\mathbf{L}^{(\ell_0)}$ 作为多重矩阵的范数 $\left \| \mathbf{L}^{(\ell_0)} \right \|$。
>
> 不失一般性，假设与顶点 $1$ 邻接的边是 $e_1$，那么 $U(1)$ 就是包含 $e_1$ 终点的单点集。另一方面，$R(1) = \varnothing$，因此 $\mathbf{L}^{(1)} = \mathbf{T}^{(1)}$。
>
> 对 $2 \leq \ell \leq \ell_0$，利用前面推出的顶点集之间的关系，可以得到
> $$
> \begin{align*}
> \mathbf{L}^{(\ell)}_{i_1, \mathbf{u}(\ell)} 
> & = \sum_{\mathbf{r}(\ell)} \prod_{g(j) \in L(\ell)} t_{i_{f(j)}, i_{g(j)}}^{(j)}
> = \sum_{\mathbf{v}(\ell)} \sum_{\mathbf{r}(\ell - 1)} \left ( 
> \prod_{g(j) \in H(\ell)} t_{i_{f(j)}, i_{g(j)}}^{(j)}
> \prod_{g(j) \in L(\ell-1)} t_{i_{f(j)}, i_{g(j)}}^{(j)} \right ) \\
> & = \sum_{\mathbf{v}(\ell)} \left ( \mathbf{H}^{(\ell)}_{\mathbf{v}(\ell), \mathbf{w}(\ell)} \sum_{\mathbf{r}(\ell - 1)} \prod_{g(j) \in L(\ell-1)} t_{i_{f(j)}, i_{g(j)}}^{(j)} \right ) \\
> & = \sum_{\mathbf{v}(\ell)} \mathbf{L}^{(\ell - 1)}_{i_1, \mathbf{u}(\ell - 1)} \mathbf{H}^{(\ell)}_{\mathbf{v}(\ell), \mathbf{w}(\ell)} ,
> \end{align*}
> $$
> 这里第二个等号利用了性质 4，第三个等号利用了性质 2 和 3。
>
> 沿用引理 [GM-1] 的符号和概念，对 $2 \leq \ell \leq \ell_0$，考察图 $\widetilde{G}_H(\ell)$，该图包含的边与 $G_H(\ell)$ 相同，但增加 $Q(\ell)$ 中的顶点作为孤立点。
>
> 如果将 $V(\ell)$，$\big ( W(\ell) \backslash H(\ell) \big ) + Q(\ell)$ 以及 $H(\ell)$ 分别视作图 $\widetilde{G}_H(\ell)$ 中的第一，二和三类顶点集，那么容易看出 $\widetilde{G}_H(\ell)$ 是以 $V(\ell)$ 为基的重边图，而 $\mathbf{H}^{(\ell)}$ 为与其关联的多重矩阵。
>
> 因此，根据性质 5 和 6，我们可以沿用 [GM-1] 中多重矩阵乘积的定义将 $\mathbf{L}^{(\ell)}$ 写成 $\mathbf{L}^{(\ell - 1)}$ 与 $\mathbf{H}^{(\ell)}$ 的乘积。此时再应用 [GM-1] 的结论，可以推出
> $$
> \big \| \mathbf{L}^{(\ell)} \big \| 
> = \big \| \mathbf{L}^{(\ell - 1)} \cdot \mathbf{H}^{(\ell)} \big \|
> \leq \big \| \mathbf{L}^{(\ell - 1)} \big \| \prod_{g(j) \in H(\ell)} \big \| \mathbf{T}^{(j)} \big \|_{\mathrm{op}} .
> $$
> 最后，对 $2 \leq \ell \leq \ell_0$ 归纳即得
> $$
> \left \| \mathbf{T}(G) \right \|_{\mathrm{op}} 
> = \left \| \mathbf{L}^{(\ell_0)} \right \| 
> \leq \left \| \mathbf{L}^{(1)} \right \| \prod_{\ell = 2}^{\ell_0} \prod_{g(j) \in H(\ell)} \left \| \mathbf{T}^{(j)} \right \| 
> = \prod_{j = 1}^{k} \left \| \mathbf{T}^{(j)} \right \|_{\mathrm{op}}.
> $$
