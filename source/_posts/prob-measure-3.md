---
title: 测度扩张
date: 2020-06-19 20:57:46
tags: 
  - measure
categories: Probability and Measure
mathjax: true
---

Durrett 概率论，Billingsley 概率与测度笔记。

<!--more-->

## 测度扩张：半代数 $\Rightarrow$ 代数

假设 $\mathcal{S}$ 为集合 $\Omega$ 上的一个半代数，并且 $\mu: \mathcal{S} \to [0, \infty]$ 为定义在 $\mathcal{S}$ 上的集函数，如果：

+ $\mu(\varnothing) = 0$，

+ **有限可加性**：对任意不交的有限集合列 $\{S_i\}_{i=1}^{n} \subset \mathcal{S}$，当 $\bigcup_{i=1}^{n} S_i \in \mathcal{S}$ 时，有
  $$
  \mu \left( \bigcup_{i=1}^{n} S_i \right) = \sum_{i=1}^{n} \mu(S_i),
  $$

+ **次可加性**：对任意不交的可数集合列 $\{S_i\}_{i=1}^{\infty} \subset \mathcal{S}$，当 $\bigcup_{i=1}^{\infty} S_i \in \mathcal{S}$ 时，有
  $$
  \mu \left( \bigcup_{i=1}^{\infty} S_i \right) \leq \sum_{i=1}^{\infty} \mu(S_i).
  $$

那么，在由 $\mathcal{S}$ 生成的代数 $\bar{\mathcal{S}}$ 上，存在唯一的测度 $\bar{\mu}$，使其为 $\mu$ 的扩张。

**构造方法**：如果 $A \in \bar{\mathcal{S}}$ 可以被表示为 $A = \bigcup_{i=1}^n S_i$，其中 $S_i \in \mathcal{S}$，那么令
$$
\bar{\mu} (A) = \sum_{i=1}^n \mu(S_i).
$$

## Carathéodory 外测度

### 外测度定义

称集函数 $\mu^\*: 2^\Omega \to [0, \infty]$ 为**外测度**，如果：

+ $\mu^\*(\varnothing)=0$；

+ **单调性**：对任意 $A \subset B$，有 $\mu^\*(A) \leq \mu^\*(B)$ 成立；

+ **次可加性**：对任意可数子集列 $\{A_i \}_{i=1}^{\infty} \subset 2^\Omega$，有
  $$
  \mu^*\left(\bigcup_{i=1}^{\infty} A_{i}\right) \leq \sum_{i=1}^{\infty} \mu^*\left(A_{i}\right).
  $$

### 可测集

对 $\Omega$ 上的一个外测度 $\mu^\*$，称集合 $A \subset \Omega$ 为 $\mu^\*$-可测的，如果对任意 $E \subset \Omega$，有
$$
\mu^*(E \cap A) + \mu^*(E \cap A^c) = \mu^*(E).
$$
记 $\Omega$ 中 $\mu^\*$-可测集全体为 $\mathcal{M}(\mu^\*)$。

### 性质

如果 $\mu^\*$ 是 $\Omega$ 上的一个外测度，那么

+ $\mathcal{M}(\mu^\*)$ 为 $\sigma$-代数；
+ $\mu^\*$ 在 $\mathcal{M}(\mu^\*)$ 为可数可加的，即 $\mu^\*$ 限制在 $\mathcal{M}(\mu^\*)$ 上时为测度；
+ 作为 $\mathcal{M}(\mu^\*)$ 上的测度，$\mu^\*$ 是完备的。

### 正则外测度

**定义**：称 $\Omega$ 上的一个外测度 $\mu^\*$ 为正则的，如果对于任意的 $A \subset \Omega$，存在 $\mu^\*$-可测集 $B \in \mathcal{M}(\mu^\*)$ 使得 $A \subset B$ 以及 $\mu^\*(A) = \mu^\*(B)$。

**有限正则外测度下的 $\mu^\*$-可测性**：假设 $\mu^\*$ 是 $\Omega$ 上的一个正则外测度，如果 $\mu^\*$ 是有限的，即 $\mu(\Omega) < \infty$，那么集合 $A \in \Omega$ 的 $\mu^\*$-可测性可以由
$$
\mu^*(A) + \mu^*(A^c) = \mu^*(\Omega)
$$
等价描述。

> **证明**：
>
> 假设 $A \subset \Omega$ 满足 $\mu^\*(A) + \mu^\*(A^c) = \mu^\*(\Omega)$，现证 $A \in \mathcal{M}(\mu^\*)$。对任意 $E \subset \Omega$，有 $\mu^\*$ 的正则性，存在 $F \in \mathcal{M}(\mu^\*)$ 使得 $E \subset F$ 以及 $\mu^\*(E) = \mu^\*(F)$。
>
> + $\mu^\*$ 次可加性 $\Rightarrow$
>   $$
>   \mu^*(F^c \cap A) + \mu^*(F^c \cap A^c) \geq \mu^*(F^c),
>   $$
>
> + $F$ 可测性 $\Rightarrow$
>   $$
>   \begin{align*}
>   \mu^*(A) & = \mu^*(A \cap F) + \mu^*(A \cap F^c), \\
>   \mu^*(A^c) & = \mu^*(A^c \cap F) + \mu^*(A^c \cap F^c),
>   \end{align*}
>   $$
>
> + 给定条件 $\Rightarrow$
>   $$
>   \mu^*(A) + \mu^*(A^c) = \mu^*(\Omega),
>   $$
>
> 联立上述式子，得到
> $$
> \mu^*(A \cap F)  + \mu^*(A^c \cap F)  \leq \mu^* (\Omega) - \mu^*(F^c).
> $$
> 此外，由于 $\mu^\*$ 在 $\mathcal{M}(\mu^\*)$ 上的可加性，
> $$
> \mu^*(F) + \mu^*(F^c) = \mu^*(\Omega),
> $$
> 从而最后有：
> $$
> \begin{align*}
> \mu^*(A \cap E)  + \mu^*(A^c \cap E) & \leq \mu^*(A \cap F)  + \mu^*(A^c \cap F) \\ 
> & \leq \mu^* (\Omega) - \mu^*(F^c) = \mu^*(F) = \mu^*(E).
> \end{align*}
> $$
> 证毕。

## 测度扩张：半代数 $\Rightarrow \sigma$-代数

### 诱导外测度

假设 $\mathcal{A} \subset 2^{\Omega}$ 是 $\Omega$ 的一个子集族并且 $\varnothing \in \mathcal{A}$，而 $\mu: \mathcal{A} \to [0, \infty]$ 是 $\mathcal{A}$ 上的集函数并且 $\mu(\varnothing)=0$。对任意 $A \subset \Omega$，令
$$
\mu^{*}(A) = \inf \left\{ \left. \sum_{n=1}^{\infty} \mu\left(A_{n}\right) \ \right| \ A_{n} \in \mathcal{A} \text{ and } A \subset \bigcup_{n=1}^{\infty} A_{n}\right\},
$$
其中当不存在 $\{ A_n \} \subset \mathcal{A}$ 使 $A \subset \bigcup_{n=1}^{\infty} A_{n}$ 时，规定 $\mu^*(A) = \infty$。此时，$\mu^\*$ 为外测度，称为 $\mu$ **诱导的外测度**。

### Carathéodory 扩张定理

假设 $\mu$ 为定义在代数 $\mathcal{A} \subset 2^\Omega$ 上的测度，那么其所诱导的外测度 $\mu^\*$ 满足

+ $\mu^\*$ 为正则外测度；
+ $\mathcal{A} \subset \mathcal{M}(\mu^\*)$；
+ 对 $A \in \mathcal{A}$，有 $\mu^\*(A) = \mu(A)$，

因此，$\mu$ 可以被扩张为 $\sigma({\mathcal{A}})$ 上的测度。此外，如果 $\mu$ 在 $\mathcal{A}$  上 $\sigma$-有限，那么此扩张唯一。

### 诱导外测度下的可测集

假设 $\mu$ 为定义在代数 $\mathcal{A} \subset 2^\Omega$ 上的有限测度，其所诱导的外测度为 $\mu^\*$，那么下述关于集合 $A \subset \Omega$ 可测性的描述等价：

+ 对任意 $E \subset \Omega$，有 $\mu^\*(E \cap A) + \mu^\*(E \backslash A) = \mu^\*(E)$；
+ $\mu^*(A) + \mu^*(A^c) = \mu^*(\Omega)$；
+ 对任意 $\varepsilon > 0$，存在 $A_{\varepsilon} \in \mathcal{A}$ 使得 $\mu^\* (A \triangle A_{\varepsilon}) < \varepsilon$；
+ 存在 $A_1, A_2 \in \mathcal{A}$ 使得 $A_1 \subset A \subset A_2$ 并且 $\mu^\* (A_2 \backslash A_1) = 0$。

