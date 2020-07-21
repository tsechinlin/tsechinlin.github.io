---
title: 概率与测度 -2- $\pi$-$\lambda$ 系统，单调类与测度的唯一性
date: 2020-06-17 23:17:13
tags: 
  - measure
categories: Probability and Measure
mathjax: true
---

Durrett 概率论，Billingsley 概率与测度笔记。

<!--more-->

## $\pi$-$\lambda$ 系统

### 定义

**$\pi$-系 ($\pi$-system)**：集合 $\Omega$ 的一个子集族 $\mathcal{P} \subset 2^{\Omega}$ 称为 $\Omega$ 上的一个 **$\pi$-系**，如果：

+ 对任意 $A, B \in \mathcal{P}$，有 $A \cap B \in \mathcal{P}$。

**$\lambda$-系 ($\lambda$-system)**：集合 $\Omega$ 的一个子集族 $\mathcal{L} \subset 2^{\Omega}$ 称为 $\Omega$ 上的一个 **$\lambda$-系**，如果：

+ $\Omega \in \mathcal{L}$；
+ 对任意的 $A,B \in \mathcal{L}$，当 $A \subset B$ 时有 $B\backslash A \in \mathcal{L}$；
+ 对任意不交的可数集合列 $\{A_i\}_{i=1}^{\infty} \subset \mathcal{L}$，有 $\bigcup_{i=1}^{\infty} A_i \in \mathcal{L}$。

在 $\lambda$-系的定义中，由于条件一和三的存在，条件二可以被等价替换为：

+ 对任意的 $A \in \mathcal{L}$，有 $A^c \in \mathcal{L}$。

### $\pi$-$\lambda$ 定理

+ 一个子集族如果同时是 $\pi$-系和 $\lambda$-系，那么其也是 $\sigma$-代数。
+ 如果 $\mathcal{P}$ 是 $\Omega$ 上的一个 $\pi$-系，那么
  $$
  \lambda(\mathcal{P}) = \sigma(\mathcal{P}),
  $$
  这里 $\lambda(\mathcal{P})$ 表示包含 $\mathcal{P}$ 的最小 $\lambda$-系。

> **证明**：
>
> $\lambda(\mathcal{P}) \subset \sigma(\mathcal{P})$ 显然，现证 $\sigma(\mathcal{P}) \subset \lambda(\mathcal{P})$。令 $\mathcal{L} = \lambda(\mathcal{P})$，这里只需证明 $\mathcal{L}$ 同时也为 $\pi$-系：因为此时 $\mathcal{L}$ 为 $\sigma$-代数并且包含 $\mathcal{P}$，所需结论成立。首先，对任意 $A \subset \Omega$，令
> $$
> \mathcal{L}_A = \left \{ B \subset \Omega \ | \ A \cap B \in \mathcal{L} \right \},
> $$
> 不难验证当 $A \in \mathcal{L}$ 时，$\mathcal{L}_A$ 为 $\lambda$-系。
>
> 对任意 $A, B \in \mathcal{P}$，由于 $\mathcal{P}$ 为 $\pi$-系，因此有 $A \cap B \in \mathcal{P} \subset \mathcal{L}$ 以及 $B \in \mathcal{L}_A$ 成立，进而 $\mathcal{P} \subset \mathcal{L}_A$。由 $\mathcal{L}$ 的极小性，知 $\mathcal{L} \subset \mathcal{L}_A$。
>
> 因此，对任意的 $A \in \mathcal{P}$ 以及 $B \in \mathcal{L}$，有 $B \in \mathcal{L}_A$ 即 $A \cap B \in \mathcal{L}$ 成立。换言之，$A \in \mathcal{L}_B$。这表明 $\mathcal{P} \subset \mathcal{L}_B$，再次由 $\mathcal{L}$ 的极小性，得 $\mathcal{L} \subset \mathcal{L}_B$。
>
> 最后，对任意的 $A, B \in \mathcal{L}$，有 $A \in \mathcal{L}_B$ 即 $A \cap B \in \mathcal{L}$ 成立，从而 $\mathcal{L}$ 为 $\pi$-系，证毕。

+ **(Dynkin's $\pi$-$\lambda$ theorem)** 假设 $\mathcal{P}$ 是 $\Omega$ 上的一个 $\pi$-系，$\mathcal{L}$ 是 $\Omega$ 上的一个 $\lambda$-系，那么当 $\mathcal{P} \subset \mathcal{L}$ 时，有 $\sigma(\mathcal{P}) \subset \mathcal{L}$。

### 测度的唯一性

假设 $\mu_1$ 和 $\mu_2$ 是定义在 $\sigma(\mathcal{P})$ 上的测度，这里 $\mathcal{P}$ 是 $\Omega$ 上的一个 $\pi$-系，此外，假设 $\mu_1$ 和 $\mu_2$ 都在 $\mathcal{P}$ 上 $\sigma$-有限。那么，当  $\mu_1$ 和 $\mu_2$ 在 $\mathcal{P}$ 上相等时，他们在 $\sigma(\mathcal{P})$ 上也相等。

## 单调类

### 定义

**单调类 (monotone class)**：集合 $\Omega$ 的一个子集族 $\mathcal{M} \subset 2^{\Omega}$ 称为 $\Omega$ 上的一个**单调类**，如果：

+ 对任意 $A_1, A_2, \ldots \in \mathcal{M}$，当 $A_i \uparrow A$ 时，有 $A \in \mathcal{M}$；
+ 对任意 $A_1, A_2, \ldots \in \mathcal{M}$，当 $A_i \downarrow A$ 时，有 $A \in \mathcal{M}$。

### 单调类定理

+ 一个子集族如果同时是单调类和代数，那么其也是 $\sigma$-代数。
+ 如果 $\mathcal{A}$ 是 $\Omega$ 上的一个代数，那么
  $$
  m(\mathcal{A}) = \sigma(\mathcal{A}),
  $$
  这里 $m(\mathcal{A})$ 表示包含 $\mathcal{A}$ 的单调类。

> **证明**：
>
> $m(\mathcal{A}) \subset \sigma(\mathcal{A})$ 显然，现证 $\sigma(\mathcal{A}) \subset m(\mathcal{A})$。令 $\mathcal{M} = m(\mathcal{A})$，这里只需证明 $\mathcal{M}$ 同时也为代数：因为此时 $\mathcal{M}$ 为 $\sigma$-代数并且包含 $\mathcal{A}$，所需结论成立。首先，对任意 $A \in \mathcal{M}$，令
> $$
> \mathcal{M}_A = \left \{ B \subset \Omega \ | \ A \cap B \in \mathcal{M} \text{ and } B^c \in \mathcal{M} \right \},
> $$
> 不难验证当 $A \in \mathcal{M}$ 时，$\mathcal{M}_A$ 为单调类。
>
> 对任意 $A, B \in \mathcal{A}$，由于 $\mathcal{A}$ 为代数，因此有 $A \cap B \in \mathcal{A} \subset \mathcal{M}$ 以及 $B^c \in \mathcal{A} \subset \mathcal{M}$ 成立，于是乎 $B \in \mathcal{M}_A$，进而 $\mathcal{A} \subset \mathcal{M}_A$。由 $\mathcal{M}$ 的极小性，知 $\mathcal{M} \subset \mathcal{M}_A$。
>
> 因此，对任意的 $A \in \mathcal{A}$ 以及 $B \in \mathcal{M}$，有 $B \in \mathcal{M}_A$ 即 $A \cap B \in \mathcal{M}$ 成立。此外，由于 $\mathcal{A}$ 为代数，$A^c \in \mathcal{A} \subset \mathcal{M}$。因此，$A \in \mathcal{M}_B$。这表明 $\mathcal{A} \subset \mathcal{M}_B$，再次由 $\mathcal{M}$ 的极小性，得 $\mathcal{M} \subset \mathcal{M}_B$。
>
> 最后，对任意的 $A, B \in \mathcal{M}$，有 $A \in \mathcal{M}_B$ 即 $A \cap B \in \mathcal{L}$ 以及 $A^c \in \mathcal{M}$ 成立，此外显然有 $\Omega \in \mathcal{A} \subset \mathcal{M}$，因此 $\mathcal{M}$ 为代数，证毕。

+ **(Halmos's monotone class theorem)** 假设 $\mathcal{A}$ 是 $\Omega$ 上的一个代数，$\mathcal{M}$ 是 $\Omega$ 上的一个单调类，那么当 $\mathcal{A} \subset \mathcal{M}$ 时，有 $\sigma(\mathcal{A}) \subset \mathcal{M}$。

### 测度的唯一性

假设 $\mu_1$ 和 $\mu_2$ 是定义在 $\sigma(\mathcal{A})$ 上的测度，这里 $\mathcal{A}$ 是 $\Omega$ 上的一个代数，此外，假设 $\mu_1$ 和 $\mu_2$ 都在 $\mathcal{A}$ 上 $\sigma$-有限。那么，当  $\mu_1$ 和 $\mu_2$ 在 $\mathcal{A}$ 上相等时，他们在 $\sigma(\mathcal{A})$ 上也相等。

