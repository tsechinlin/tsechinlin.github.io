---
title: 概率与测度 -1- 测度空间
date: 2020-06-16 22:04:24
tags: 
  - measure
categories: Probability and Measure
mathjax: true
---

Durrett 概率论，Billingsley 概率与测度笔记。

<!--more-->

## 半代数、代数、$\sigma$-代数

### 定义

**半代数 (semialgebra)**：集合 $\Omega$ 的一个子集族 $\mathcal{S} \subset 2^{\Omega}$ 称为 $\Omega$ 上的一个**半代数**，如果：

+ $\varnothing, \Omega \in \mathcal{S}$；
+ 对任意 $S, T \in \mathcal{S}$，有 $S \cap T \in \mathcal{S}$；
+ 对任意 $S \in \mathcal{S}$，存在不交的有限集合列 $\{T_i\}_{i=1}^{n} \subset \mathcal{S}$，使得 $S^c = \bigcup_{i=1}^n T_i$。

**代数 (algebra)**：集合 $\Omega$ 的一个子集族 $\mathcal{A} \subset 2^{\Omega}$ 称为 $\Omega$ 上的一个**代数**，如果：

+ $\Omega \in \mathcal{A}$；
+ 对任意 $A \in \mathcal{A}$，有 $A^c \in \mathcal{A}$；
+ 对任意 $A, B \in \mathcal{A}$，有 $A \cup B \in \mathcal{A}$。

**$\sigma$-代数 ($\sigma$-algebra)**：集合 $\Omega$ 的一个子集族 $\mathcal{F} \subset 2^{\Omega}$ 称为 $\Omega$ 上的一个 **$\sigma$-代数**，如果：

+ $\Omega \in \mathcal{F}$；
+ 对任意 $A \in \mathcal{A}$，有 $A^c \in \mathcal{F}$；
+ 对任意可数集合列 $\{A_i\}_{i=1}^{\infty} \subset \mathcal{F}$，有 $\bigcup_{i=1}^{\infty} A_i \in \mathcal{F}$。

**性质**

+ 假设 $\{\mathcal{A}_i\}_{i \in I}$ 为同一个集合 $\Omega$ 上的一族代数 (或 $\sigma$-代数)，那么 $\bigcap_{i \in I} \mathcal{A}_i$ 也为代数 (或 $\sigma$-代数)。

+ 如果 $\mathcal{F}$ 是集合 $\Omega$ 上的 $\sigma$-代数，那么对任意 $\Omega_0 \subset \Omega$，集族
  $$
  \mathcal{F} \cap \Omega_0 = \left \{ A \cap \Omega_0 \ | \ A \in \mathcal{F} \right \}
  $$
  是 $\Omega_0$ 上的 $\sigma$-代数。

### 半代数生成的代数

对任意 $\Omega$ 上的子集族 $\mathcal{S}$，存在包含 $\mathcal{S}$ 的最小代数：
$$
\bigcap \left \{ \mathcal{A} \ | \ \mathcal{S} \subset \mathcal{A} \text{ and } \mathcal{A} \text{ is an algebra on } \Omega \right \}.
$$
特别地，当 $\mathcal{S}$ 为半代数时，
$$
\bar{\mathcal{S}} := \left \{ \left. \bigcup_{i=1}^n S_i \ \right | \ n \in \mathbb{Z}_+, S_i \in \mathcal{S} \text{ are disjoint} \right \}
$$
为包含 $\mathcal{S}$ 的最小代数，称为由 $\mathcal{S}$ **生成的代数**。

### 子集族生成的 $\sigma$-代数

对任意 $\Omega$ 上的子集族 $\mathcal{A}$，存在包含 $\mathcal{A}$ 的最小 $\sigma$-代数
$$
\sigma(\mathcal{A}) := \bigcap \left \{ \mathcal{F} \ | \ \mathcal{A} \subset \mathcal{F} \text{ and } \mathcal{F} \text{ is a } \sigma \text{-algebra on } \Omega \right \},
$$
称为由 $\mathcal{A}$ **生成的 $\sigma$-代数**。

+ 如果 $\sigma(\mathcal{A}) = \mathcal{F}$，那么对任意 $\Omega_0 \subset \Omega$，集族 $\mathcal{A} \cap \Omega_0$ 生成了 $\sigma$-代数 $\mathcal{F} \cap \Omega_0$，即
  $$
  \sigma(\mathcal{A} \cap \Omega_0) = \mathcal{F} \cap \Omega_0.
  $$

## 测度

### 定义

给定集合 $\Omega$ 以及 $\Omega$ 上的一个代数 $\mathcal{F}$ (或 $\sigma$-代数)，称非负集函数 $\mu: \mathcal{F} \to [0, \infty]$ 为 $\mathcal{A}$ 上的一个**测度**，如果：

+ $\mu(\varnothing) = 0$；

+ **可数可加性**：对任意不交的可数集合列 $\{A_i\}_{i=1}^{\infty} \subset \mathcal{F}$，如果 $\bigcup_{i=1}^{\infty} A_i \in \mathcal{F}$，则有
  $$
  \mu \left( \bigcup_{i=1}^{\infty} A_i \right) = \sum_{i=1}^{\infty} \mu(A_i).
  $$

特别地，如果 $\mu(\Omega) = 1$，称 $\mu$ 为**概率测度**。

### 基本性质

下述集合都假定为 $\mathcal{A}$ 中的集合。

+ **单调性**：如果 $A \subset B$，那么 $\mu(A) \leq \mu(B)$；
+ **次可加性**：如果 $A \subset \bigcup_{i=1}^{\infty} A_i$，那么 $\mu \left( A \right) \leq \sum_{i=1}^{\infty} \mu(A_i)$；
+ **下连续性**：如果 $A_i \uparrow A$，即 $A_1 \subset A_2 \subset \cdots$ 且 $\bigcup_{i=1}^{\infty} A_i = A$，那么 $\mu(A_i) \uparrow \mu(A)$；
+ **上连续性**：如果 $A_i \downarrow A$，即 $A_1 \supset A_2 \supset \cdots$ 且 $\bigcap_{i=1}^{\infty} A_i = A$，那么当 $\mu(A_1) < \infty$ 时 $\mu(A_i) \downarrow \mu(A)$。

### 可测空间、测度空间、概率空间

+ 假定 $\mathcal{F}$ 为集合 $\Omega$ 上的 $\sigma$-代数，称二元组 $(\Omega, \mathcal{F})$ 为**可测空间 (measurable space)**，
+ 如果 $\mu$ 为 $\mathcal{F}$ 上的测度，称三元组 $(\Omega, \mathcal{F}, \mu)$ 为**测度空间 (measure space)**，
+ 特别地，如果 $\mu$ 为概率测度，称三元组 $(\Omega, \mathcal{F}, \mu)$ 为**概率空间 (probability space)**。

### 测度的 $\sigma$-有限性

假设测度 $\mu$ 定义在代数 $\mathcal{F}$ (或 $\sigma$-代数) 上，称其在子族 $\mathcal{A} \subset \mathcal{F}$ 上为 **$\sigma$-有限 ($\sigma$-finite)** 的，如果存在 $\{A_i\}_{i=1}^{\infty} \subset \mathcal{A}$，使得 $\mu(A_i) < \infty$ 以及 $\bigcup_{i=1}^{\infty} A_i = \Omega$ 成立。

+ 由于可以令
  $$
  A_n^\prime = \bigcup_{i=1}^{n} A_i \quad \text{or} \quad A_n^\prime = A_n \cap \left( \bigcap_{i=1}^{n-1} A_i^c \right) \in \mathcal{A},
  $$
  因此不失一般性，可以假设 $A_i \uparrow \Omega$ 或者 $\{A_i\}$ 不交。
+ 如果 $\mu$ 是 $\sigma$-代数 $\mathcal{F}$ 上的 $\sigma$-有限测度，那么在 $\mathcal{F}$ 中不存在不交的不可数正测度集合列，即如果 $\{A_\alpha \} \subset \mathcal{F}$ 两两不交，并且对任意 $\alpha$ 有 $\mu(A_\alpha) > 0$，那么 $\{A_\alpha \}$ 至多可数。

## 测度扩张与实空间上的测度

### 半代数 $\Rightarrow$ 代数

假设 $\mathcal{S}$ 为集合 $\Omega$ 上的一个半代数，并且 $\mu: \mathcal{S} \to [0, \infty]$ 为定义在 $\mathcal{S}$ 上的集函数，如果：

+ $\mu(\varnothing) = 0$，
+ 对任意不交的有限集合列 $\{S_i\}_{i=1}^{n} \subset \mathcal{S}$，当 $\bigcup_{i=1}^{n} S_i \in \mathcal{S}$ 时，有
  $$
  \mu \left( \bigcup_{i=1}^{n} S_i \right) = \sum_{i=1}^{n} \mu(S_i),
  $$
+ 对任意不交的可数集合列 $\{S_i\}_{i=1}^{\infty} \subset \mathcal{S}$，当 $\bigcup_{i=1}^{\infty} S_i \in \mathcal{S}$ 时，有
  $$
  \mu \left( \bigcup_{i=1}^{\infty} S_i \right) \leq \sum_{i=1}^{\infty} \mu(S_i).
  $$

那么，在由 $\mathcal{S}$ 生成的代数 $\bar{\mathcal{S}}$ 上，存在唯一的测度 $\bar{\mu}$，使其为 $\mu$ 的扩张。

> **构造**：如果 $A \in \bar{\mathcal{S}}$ 可以被表示为 $A = \bigcup_{i=1}^n S_i$，其中 $S_i \in \mathcal{S}$，令
> $$
> \bar{\mu} (A) = \sum_{i=1}^n \mu(S_i).
> $$

### 代数 $\Rightarrow \sigma$-代数 (Caratheodory's Extension Theorem)

> **构造**：对任意 $A \subset \Omega$，定义**外测度**
> $$
> \mu^{*}(A)=\inf \left\{ \left. \sum_{n=1}^{\infty} \mu\left(A_{i}\right) \ \right| \ A_{i} \in \mathcal{A} \text{ and } A \subset \bigcup_{i=1}^{\infty} A_{i}\right\},
> $$
> 将 $\mu^\*$ 限制到 $\sigma({\mathcal{A}})$ 上即为所需扩张。

