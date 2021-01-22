---
title: Enumerative Combinatorics with Multiple Matrices - Definitions and Notations
date: 2021-01-22 09:50:29
tags: 
  - Graph Theory
  - Enumerative Combinatorics
categories: Random Matrix
mathjax: true
---

[Notes] <u>Spectral analysis of large dimensional random matrices</u> by Zhidong Bai & Jack W. Silverstein.

<!--more-->

## Multiple Matrix

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

## Graph-Associated Multiple Matrix

### 有向图 Directed  Graph

Let $G = (V, E, f \times g)$ be a **directed graph** with $t$ vertices and $k$ edges, that is,

+ $V = [t] = \{ 1, \cdots, t \}$.
+ $E = \big \{ e_j : j \in [k] \big \} = \{ e_1, \cdots, e_k \}$.
+ $f \times g$ is a mapping from $[k]$ to $V \times V$, with the property that, for each $j \in [k]$, the $j$-th edge $e_j = \big( f(j), g(j) \big )$ goes from the vertex $f(j)$ to the vertex $g(j)$.

### 维度一致性约束 Consistent Dimension Restriction

Let $\big \{ \mathbf{T}^{(j)} : j \in [k] \big \}$ be a collection of matrices corresponding to the $k$ edges. We say that $\big \{ \mathbf{T}^{(j)} \big \}$ is subject to the **consistent dimension restriction** given by $G$ if

+ for each $a \in V$, there exists a positive integers $m_a$ associated with the vertex $a$, such that
+ for each $j \in [k]$, the dimension of matrix $\mathbf{T}^{(j)}$ is $m_{f(j)} \times m_{g(j)}$.

### 图关联多重矩阵 Graph-Associated Multiple Matrix

Let $U, W \subset V$ be two disjoint sets of vertices. Here $U$ and $W$ can be empty sets.

Define the multiple indices
$$
\mathbf{u} = (i_a)_{a \in U},
\quad
\mathbf{w} = (i_a)_{a \in W},
\quad \text{ and } \quad
\mathbf{v} = (i_a)_{a \in V \backslash (U \cup W)},
$$
where $i_a$ takes values in $[m_a]$.

Then the **graph-associated multiple matrix** $\mathbf{T}(G)$ with left index $\mathbf{u}$ and right index $\mathbf{w}$ is define by
$$
\mathbf{T}(G)_{\mathbf{u}, \mathbf{w}} = 
\sum_{\mathbf{v}} \prod_{j=1}^{k} t^{(j)}_{i_{f(j)}, i_{g(j)}}.
$$

### 边向逆转 Reverse of Edges 

Assume that $J \subset [k]$. 

**[graph]** We can define a new graph $\widetilde{G}= \big ( V, \widetilde{E}, \phi \times \varphi \big )$ by reversing the edges in $\{ e_j: j \in J \}$. In other words,

+ $\phi(j) = g(j)$ and $\varphi(j) = f(j)$ for $j \in J$.
+ $\phi(j) = f(j)$ and $\varphi(j) = g(j)$ for $j \in [k] \backslash J$.

![](graph-1.svg)<!-- -->

**[matrices]** Now define $\widetilde{\mathbf{T}}^{(j)} = \big ( \mathbf{T}^{(j)} \big ) ^ \top$ for $j \in J$ and $\widetilde{\mathbf{T}}^{(j)} = \mathbf{T}^{(j)}$ for $j \in [k] \backslash J$.

Then $\big \{ \widetilde{\mathbf{T}}^{(j)} : j \in [k] \big \}$ satisfies the consistent dimension restriction given by $\widetilde{G}$.

**[multiple matrix]** Let $\widetilde{\mathbf{T}}(\widetilde{G})$ be the multiple matrix associated with the graph $\widetilde{G}$ with left index $\mathbf{u}$ and right index $\mathbf{w}$,
$$
\widetilde{\mathbf{T}}(\widetilde{G})_{\mathbf{u}, \mathbf{w}} 
= \sum_{\mathbf{v}} \prod_{j=1}^{k} \widetilde{t}^{(j)}_{i_{\phi(j)}, i_{\varphi(j)}}.
$$
Note that for any $\mathbf{u}$ and $\mathbf{w}$,
$$
\widetilde{\mathbf{T}}(\widetilde{G})_{\mathbf{u}, \mathbf{w}}  
= \sum_{\mathbf{v}} \left ( \prod_{j \in J} \widetilde{t}^{(j)}_{i_{\phi(j)}, i_{\varphi(j)}} \prod_{j \in [k] \backslash J} \widetilde{t}^{(j)}_{i_{\phi(j)}, i_{\varphi(j)}} \right )
= \sum_{\mathbf{v}} \left ( \prod_{j \in J} {t}^{(j)}_{i_{\varphi(j)}, i_{\phi(j)}} \prod_{j \in [k] \backslash J} {t}^{(j)}_{i_{\phi(j)}, i_{\varphi(j)}} \right )
= \mathbf{T}({G})_{\mathbf{u}, \mathbf{w}}.
$$
Thus $\mathbf{T}(\widetilde{G}) = \mathbf{T}(G)$.

### 顶点分裂 Splitting of Vertex 

Assume that $1 \in V \backslash (U \cup W)$. 

Let $J_0, J_1 \subset [k]$ such that $\{ e_j: j \in J_0\}$ and $\{ e_j: j \in J_1\}$ form a partition of the set of edges adjacent with the vertex $1$.

**[graph]** Now define a new graph $\widetilde{G}= \big ( \{ 0 \} \cup V, \widetilde{E}, \phi \times \varphi \big)$ by splitting the vertex $1$ into two vertices.

+ Add an edge $e_0$ from vertex $0$ to $1$, that is, $\phi(0) = 0$ and $\varphi(0) = 1$.

+ Attach all the edges indexed by $J_0$ to the new vertex $0$. In other words, for all $j \in J_0$, 
    $$
    f(j) = 1 \ \Leftrightarrow \ \phi(j) = 0,
    \quad \text{ and } \quad
    g(j) = 1 \ \Leftrightarrow \ \varphi(j) = 0.
    $$

+ All other edges remain the same, that is, $\phi(j) = f(j)$ and $\varphi(j) = g(j)$ for $j \in [k] \backslash J_0$.

**[matrices]** Now define $\widetilde{\mathbf{T}}^{(0)} = \mathbf{I}_{m_1}$ and $\widetilde{\mathbf{T}}^{(j)} = \mathbf{T}^{(j)}$ for $j \in [k]$. Recall that $m_1$ is the dimension associated with the vertex $1$ in graph $G$.

Then $\big \{ \widetilde{\mathbf{T}}^{(j)} : j = 0 \text{ or } j \in [k] \big \}$ satisfies the consistent dimension restriction given by $\widetilde{G}$.

**[multiple matrix]** Define the multiple index $\widetilde{\mathbf{v}} = (i_0, \mathbf{v})$, where $i_0$ takes values in $[m_0] = [m_1]$.

Let $\widetilde{\mathbf{T}}(\widetilde{G})$ be the multiple matrix associated with the graph $\widetilde{G}$ with left index $\mathbf{u}$ and right index $\mathbf{w}$,
$$
\widetilde{\mathbf{T}}(\widetilde{G})_{\mathbf{u}, \mathbf{w}} 
= \sum_{\widetilde{\mathbf{v}}} \prod_{j=0}^{k} \widetilde{t}^{(j)}_{i_{\phi(j)}, i_{\varphi(j)}}.
$$
Note that for any $\mathbf{u}$ and $\mathbf{w}$,
$$
\widetilde{\mathbf{T}}(\widetilde{G})_{\mathbf{u}, \mathbf{w}}  
= \sum_{i_0, \mathbf{v}} \left ( \delta_{i_0, i_1} \prod_{j \in J_0} \widetilde{t}^{(j)}_{i_{\phi(j)}, i_{\varphi(j)}} \prod_{j \in [k] \backslash J_0} \widetilde{t}^{(j)}_{i_{\phi(j)}, i_{\varphi(j)}} \right )
= \sum_{\mathbf{v}} \left ( \prod_{j \in J_0} {t}^{(j)}_{i_{\phi(j)}, i_{\varphi(j)}} \prod_{j \in [k] \backslash J_0} {t}^{(j)}_{i_{\phi(j)}, i_{\varphi(j)}} \right )
= \mathbf{T}({G})_{\mathbf{u}, \mathbf{w}}.
$$
Thus $\mathbf{T}(\widetilde{G}) = \mathbf{T}(G)$.
