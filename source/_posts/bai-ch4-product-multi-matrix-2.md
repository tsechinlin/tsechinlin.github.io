---
title: Enumerative Combinatorics with Multiple Matrices - Hierarchical Graphs
tags: 
  - Graph Theory
  - Enumerative Combinatorics
categories: Random Matrix
mathjax: true
---

[Notes] <u>Spectral analysis of large dimensional random matrices</u> by Zhidong Bai & Jack W. Silverstein.

<!--more-->

## $V_1$-based Graphs

### 图结构 Graph Structure

Consider a directed graph $G = (V, E; f \times g)$ with the following structures.

+ The vertex set of $G$ can be partitioned into $V = V_1 + V_2 + V_3$, where $V_1$ and $V_3$ is nonempty.
+ The end vertex of each edge is in $V_3$, i.e., for each $j \in [k]$, we have $g(j) \in V_3$.
+ The edges initiated from $V_1$, $V_2$, or $V_3$ are called the first, second, or third type edges, respectively. Let
    $$
    J_p = \big \{ j \in [k]: f(j) \in V_p \big \}, \quad \text{ for } p = 1, 2, 3.
    $$
+ The graph $G$ is **$V_1$-based**, in the sense that
    + For any $a \in V_1$, there exists some vertex $b \in V_3$ such that $(a,b) \in E$.
    + For any $b \in V_3$, there exists some vertex $a \in V_1$ such that $(a,b) \in E$.

Below we assume that $\{ \mathbf{T}^{(j)} \}_{j \in [k]}$ is a collection of matrices satisfying the consistent dimension restriction given by $G$.

### 图关联多重矩阵 Graph-Associated Multiple Matrix

Define the multiple indices
$$
\mathbf{v}_p = (i_a)_{a \in V_p} \quad \text{ for } \quad p = 1, 2, 3.
$$
Then the multiple matrix associated with the graph $G$ with left index $\mathbf{v}_1$ and right index $(\mathbf{v}_2, \mathbf{v}_3)$ is given by
$$
\mathbf{T}(G)_{\mathbf{v}_1, (\mathbf{v}_2, \mathbf{v}_3)} 
= \prod_{j \in [k]} t^{(j)}_{i_{f(j)} \ , i_{g(j)}}
= \prod_{j \in J_1} t^{(j)}_{i_{f(j)} \ , i_{g(j)}} \prod_{j \in J_2 \cup J_3} t^{(j)}_{i_{f(j)} \ , i_{g(j)}}.
$$
### Lemma [GM-1]

Assume that $\mathbf{A} = ( a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} )$ is a multiple matrix where the left index $\mathbf{i}$ is independent of $\mathbf{v}_1, \mathbf{v}_2$ and $\mathbf{v}_3$. 

Define the product of $\mathbf{A}$ and $\mathbf{T} (G)$ by a multiple matrix with left index $\mathbf{i}$ and right index $(\mathbf{v}_2, \mathbf{v}_3)$,
$$
\big ( \mathbf{A} \cdot \mathbf{T} (G) \big )_{\mathbf{i}, (\mathbf{v}_2, \mathbf{v}_3)}
= \sum_{\mathbf{v}_1} a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} \mathbf{T}(G)_{\mathbf{v}_1, (\mathbf{v}_2, \mathbf{v}_3)}.
$$

Then, we have
$$
\big \| \mathbf{A} \cdot \mathbf{T} (G) \big \|
\leq \| \mathbf{A} \| \cdot \prod_{j \in [k]} \big \| \mathbf{T}^{(j)} \big \|_{\mathrm{op}}.
$$

> **证明**：
>
> 首先注意到，对任意的 $u \in \left [ m_{f(j)} \right ]$ 及 $v \in \left [ m_{g(j)} \right ]$，有
> $$
> \big \| \mathbf{T}^{(j)} \big \|_{\mathrm{op}} = \max_{\| \mathbf{x} \|_2 = 1, \ \| 
> \mathbf{y} \|_2 = 1} \left | \big \langle \mathbf{T}^{(j)} \mathbf{x}, \mathbf{y} \big \rangle \right |
> \geq \big | t^{(j)}_{u, v} \big |.
> $$
> 结合多重矩阵范数的定义，可以推出
> $$
> \begin{align*}
> \big \| \mathbf{A} \cdot \mathbf{T} (G) \big \|^2
> & = \sup_{\| \mathbf{g} \| = 1} \sum_{\mathbf{v}_2, \mathbf{v}_3} 
> \left|\sum_{\mathbf{i}} \big ( \mathbf{A} \cdot \mathbf{T} (G) \big )_{\mathbf{i}, (\mathbf{v}_2, \mathbf{v}_3)} g_{\mathbf{i}} \right|^2 \\
> & = \sup_{\| \mathbf{g} \| = 1} \sum_{\mathbf{v}_2, \mathbf{v}_3} 
> \left|\sum_{\mathbf{i}} g_{\mathbf{i}} \sum_{\mathbf{v}_1} a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} \mathbf{T}(G)_{\mathbf{v}_1, (\mathbf{v}_2, \mathbf{v}_3)} \right|^2 \\
> & \leq \sup_{\| \mathbf{g} \| = 1} \sum_{\mathbf{v}_2, \mathbf{v}_3} 
> \left|\sum_{\mathbf{i}} g_{\mathbf{i}} \sum_{\mathbf{v}_1} a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} \prod_{j \in J_1} t^{(j)}_{i_{f(j)} \ , i_{g(j)}} \right|^2 \cdot \prod_{j \in J_2 \cup J_3} \big \| \mathbf{T}^{(j)} \big \|_{\mathrm{op}}^2.
> \end{align*}
> $$
> 对于 $j \in J_1$，假定矩阵 $\mathbf{T}^{(j)}$ 的奇异值分解为 $\mathbf{T}^{(j)} = \mathbf{H}^{(j)} \boldsymbol{\Sigma}^{(j)} ( \boldsymbol{\Xi}^{(j)} )^*$，此处 $\mathbf{H}^{(j)}$ 以及 $\boldsymbol{\Xi}^{(j)}$ 分别为 $m_{f(j)}$ 阶和 $m_{g(j)}$ 阶的酉矩阵。此时
> $$
> t_{u,v}^{(j)}=\sum_{\ell=1}^{r_{j}} \sigma_{\ell}^{(j)} \eta_{u,\ell}^{(j)} \overline{\xi}_{v,\ell}^{(j)},
> \quad \text{ for } u \in \left [ m_{f(j)} \right ] \text{ and } v \in \left [ m_{g(j)} \right ],
> $$
> 其中 $r_j = m_{f(j)} \wedge m_{g(j)}$。
>
> 用 $w_j$ 替换 $i_{g(j)}$ 并令 $\mathbf{w} = (w_j)_{j \in J_1}$。考虑到任意的 $a \in V_3$，都存在 $j \in J_1$ 使得 $g(j) = a$，因此对 $\mathbf{v}_3 \in \prod_{a \in V_3} [m_a]$ 求和就相当于对 $\mathbf{w} \in \prod_{j \in J_1} \big [ m_{g(j)} \big ]$ 求和，但附加约束
> $$
> w_j = w_{j^\prime},
> \quad \text{ for any } j, j^\prime \in J_1 \text{ with }
> g(j) = g(j^\prime).
> $$
> 当待求和项非负时，去除上述约束不会使总和减小，因此
> $$
> \begin{align*}
> \sum_{\mathbf{v}_2} \sum_{\mathbf{v}_3} 
> \left| \sum_{\mathbf{i}, \mathbf{v}_1} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} \prod_{j \in J_1} t^{(j)}_{i_{f(j)} \ , w_j} \right|^2
> & \leq \sum_{\mathbf{v}_2} \sum_{\mathbf{w}} 
> \left| \sum_{\mathbf{i}, \mathbf{v}_1} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} \prod_{j \in J_1} t^{(j)}_{i_{f(j)} \ , w_j} \right|^2 \\
> & \triangleq \sum_{\mathbf{v}_2} \sum_{\mathbf{w}} 
> \left| \sum_{\mathbf{i}, \mathbf{v}_1} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} \sum_{\boldsymbol{\ell}} \sigma_{\boldsymbol{\ell}} \eta_{\mathbf{v}_1, \boldsymbol{\ell}} \overline{\xi}_{\mathbf{w}, \boldsymbol{\ell}} \right|^2,
> \end{align*}
> $$
>
> 此处多重指标 $\boldsymbol{\ell} = (\ell_j)_{j \in J_1}$，取值范围为 $\prod_{j \in J_1} [ r_{j} ]$，
> $$
> \sigma_{\boldsymbol{\ell}} 
> : = \prod_{j \in J_1} \sigma_{\ell_j}^{(j)} 
> , \quad
> \eta_{\mathbf{v}_1, \boldsymbol{\ell}} 
> : = \prod_{j \in J_1} \eta_{i_{f(j)} \ , \ell_j}^{(j)}, 
> \quad \text{ and } \quad 
> \xi_{\mathbf{w}, \boldsymbol{\ell}} 
> : = \prod_{j \in J_1} \xi_{w_j, \ell_j}^{(j)}.
> $$
> 注意到 $\boldsymbol{\Xi}^{(j)}$ 为酉矩阵，因此对任意的 $\boldsymbol{\ell}, \boldsymbol{\ell}^\prime \in \prod_{j \in J_1} [ r_{j} ]$，有
> $$
> \sum_{\mathbf{w}} \overline{\xi}_{\mathbf{w}, \boldsymbol{\ell}} \xi_{\mathbf{w}, \boldsymbol{\ell}^\prime}
> = \sum_{\mathbf{w}} \prod_{j \in J_1} \overline{\xi}_{w_j, \ell_j}^{(j)} \xi_{w_j, \ell_j^\prime}^{(j)}
> = \prod_{j \in J_1} \sum_{w_j} \overline{\xi}_{w_j, \ell_j}^{(j)} \xi_{w_j, \ell_j^\prime}^{(j)}
> = \prod_{j \in J_1} \delta_{\ell_j, \ell_j^\prime}
> = \delta_{\boldsymbol{\ell}, \boldsymbol{\ell}^\prime}.
> $$
> 再注意到 $\sigma_{\boldsymbol{\ell}} \leq \prod_{j \in J_1} \big \| \mathbf{T}^{(j)} \big \|_{\mathrm{op}}$，可以推得
> $$
> \begin{align*}
> \sum_{\mathbf{v}_2} \sum_{\mathbf{w}}
> \left| \sum_{\boldsymbol{\ell}} \overline{\xi}_{\mathbf{w}, \boldsymbol{\ell}} \left ( \sigma_{\boldsymbol{\ell}} \sum_{\mathbf{i}, \mathbf{v}_1} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} \eta_{\mathbf{v}_1, \boldsymbol{\ell}} \right ) \right|^2
> & = \sum_{\mathbf{v}_2} \sum_{\boldsymbol{\ell}} \sigma_{\boldsymbol{\ell}}^2 \left | \sum_{\mathbf{i}, \mathbf{v}_1} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} \eta_{\mathbf{v}_1, \boldsymbol{\ell}} \right |^2 \\
> & \leq \prod_{j \in J_1} \big \| \mathbf{T}^{(j)} \big \|_{\mathrm{op}}^2 \sum_{\mathbf{v}_2} \sum_{\boldsymbol{\ell}} \left | \sum_{\mathbf{i}, \mathbf{v}_1} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} \eta_{\mathbf{v}_1, \boldsymbol{\ell}} \right |^2 
> \end{align*}
> $$
> 注意此处对于求和指标 $\boldsymbol{\ell}$ 的取值范围是 $\prod_{j \in J_1} [ r_{j} ] \triangleq [ \mathbf{r} ]$。考虑到待求和项非负，因此将 $\boldsymbol{\ell}$ 的取值范围扩大为 $\prod_{j \in J_1} \big [ m_{f(j)} \big ] \triangleq [ \mathbf{m}_f ]$ 不会使总和减小。
>
> 另外，由于 $\mathbf{H}^{(j)}$ 也是酉矩阵，因此对任意的 $\mathbf{v}_1, \mathbf{v}_1^\prime \in \prod_{a \in V_1} [ m_{a} ]$，有
> $$
> \sum_{\boldsymbol{\ell} \in \left [ \mathbf{m}_f \right ]} \eta_{\mathbf{v}_1, \boldsymbol{\ell}} \overline{\eta}_{\mathbf{v}_1^\prime, \boldsymbol{\ell}}
> = \sum_{\boldsymbol{\ell} \in \left [ \mathbf{m}_f \right ]} \prod_{j \in J_1} \eta_{i_{f(j)} \ , \ell_j}^{(j)} \overline{\eta}_{i_{f(j)}^\prime \ , \ell_j}^{(j)} 
> = \prod_{j \in J_1} \sum_{\ell_j \in \left [ m_{f(j)} \right ]} \eta_{i_{f(j)} \ , \ell_j}^{(j)} \overline{\eta}_{i_{f(j)}^\prime \ , \ell_j}^{(j)}
> = \prod_{j \in J_1} \delta_{i_{f(j)} \ , i_{f(j)}^\prime}
> = \delta_{\mathbf{v}_1, \mathbf{v}_1^\prime}.
> $$
> 这里最后一个等号成立是因为根据假设，$\big \{ f(j) \big \}_{j \in J_1} = V_1$。因此，
>
> $$
> \begin{align*}
> \sum_{\mathbf{v}_2} \sum_{\boldsymbol{\ell} \in [\mathbf{r}]} \left | \sum_{\mathbf{v}_1} \eta_{\mathbf{v}_1, \boldsymbol{\ell}} \left ( \sum_{\mathbf{i}} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} \right ) \right |^2
> & \leq \sum_{\mathbf{v}_2} \sum_{\boldsymbol{\ell} \in \left [ \mathbf{m}_f \right ]} \left | \sum_{\mathbf{v}_1} \eta_{\mathbf{v}_1, \boldsymbol{\ell}} \left ( \sum_{\mathbf{i}} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} \right ) \right |^2 \\
> & = \sum_{\mathbf{v}_2} \sum_{\mathbf{v}_1} \left | \sum_{\mathbf{i}} g_{\mathbf{i}} a_{\mathbf{i}, (\mathbf{v}_1, \mathbf{v}_2)} \right |^2
> \leq \| \mathbf{A} \|^2.
> \end{align*}
> $$
> 综上所述，引理 [GM-1] 得证。

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
