---
title: "Compressed Sensing with Redundant Dictionaries - CoSaMP"
date: 2020-03-24 16:10:44
tags: 
  - Compressed Sensing
categories: Computational Mathematics
mathjax: true
---

参考文献

+ **[DNW13]** Davenport, M. A., Needell, D., & Wakin, M. B. (2013). Signal space CoSaMP for sparse recovery with redundant dictionaries. IEEE Transactions on Information Theory, 59(10), 6820-6829.
+ **[GN15]** Giryes, R., & Needell, D. (2015). Greedy signal space methods for incoherence and beyond. Applied and Computational Harmonic Analysis, 39(1), 1-20.

<!--more-->

## 投影算子与最优指标集

+ **正交投影算子** (the orthogonal projection operator)：对指标集 $S \subset [N]$，用 $\mathcal{R}(\mathbf{D}_S)$ 表示 $\mathbf{D}_S$ 的值域，也就是
  $$
  \mathcal{R}(\mathbf{D}_S) = \operatorname{span} \left \{ \mathbf{d}_j: j \in S \right\},
  $$
  令 $\mathcal{P}_S: \mathbb{C}^n \to \mathbb{C}^n$ 表示到子空间 $\mathcal{R}(\mathbf{D}_S)$ 的投影算子，具体来说，对 $\mathbf{g} \in \mathbb{R}^n$，定义
  $$
  \mathcal{P}_{S} \mathbf{g} = \underset{\mathbf{h} \in \mathbb{C}^n}{\arg \min} \ { \| \mathbf{g} - \mathbf{h} \|_2} \quad \text{ s.t. } \quad \mathbf{h} \in \mathcal{R}(\mathbf{D}_S),
  $$
等价地，
  $$
  \mathcal{P}_{S} \mathbf{g} = \mathbf{D} \cdot \underset{\operatorname{supp(\mathbf{z})}  \subset S}{\arg \min} \ {\| \mathbf{g} - \mathbf{D} \mathbf{z} \|_2}.
  $$
  另外令 $\mathcal{Q}_S: \mathbb{C}^n \to \mathbb{C}^n$  表示 $\mathcal{R}(\mathbf{D}_S)$ 正交补的投影算子，即
  $$
  \mathcal{Q}_S \mathbf{g} = \mathbf{g} - \mathcal{P}_S \mathbf{g} = \left ( \mathbf{Id} - \mathcal{P}_S \right) \mathbf{g}.
  $$
  
+ **最优投影指标集** (optimal index set for orthogonal projection)：对正整数 $s \in [N]$ 以及 $\mathbf{g} \in \mathbb{C}^n$，令 $\mathcal{O}_s(\mathbf{g})$ 表示大小为 $s$ 的投影效果最好的指标集，即
  $$
  \mathcal{O}_{s}(\mathbf{g}) = \underset{S \subset [N]}{\arg \min} \ { \| \mathbf{g} - \mathcal{P}_S \mathbf{g} \|_2} \quad \text{ s.t. } \quad \operatorname{card}(S) = s.
  $$

### 引理 1

对任意指标集 $S \subset T \subset [N]$，有

+ $\mathcal{P}_S \mathcal{P}_T = \mathcal{P}_S$，
+ 对任意 $\mathbf{g} \in \mathbb{C}^n$，有 $\lVert \mathcal{P}_S \mathbf{g} \rVert_2 = \rVert \mathcal{P}_S \mathcal{P}_T \mathbf{g} \rVert_2 \leq \|\mathcal{P}_T \mathbf{g} \|_2$。

### 引理 2

对任意 $\mathbf{g}, \mathbf{h} \in \mathbb{C}^n$ 以及 $S \subset [N]$，有
$$
\left \| \mathbf{g} - \mathcal{P}_{S} \mathbf{g} \right \|_2 \leq \left \| \mathbf{g} - \mathcal{P}_{S} \mathbf{h} \right \|_2.
$$
### 引理 3

对任意 $\mathbf{g} \in \mathbb{C}^n$，以及正整数 $s \in [N]$，如果令 $\Omega = \mathcal{O}_{s}(\mathbf{g})$，那么对任意大小为 $s$ 的指标集 $\Pi \subset [N]$，有
$$
\left \| \mathcal{P}_{\Omega \cup \Pi} \mathbf{g} - \mathcal{P}_{\Omega} \mathbf{g} \right \|_2 \leq \left \| \mathcal{P}_{\Omega \cup \Pi} \mathbf{g} - \mathcal{P}_{\Pi} \mathbf{g} \right \|_2.
$$

> **证明**：
>
> 对任意指标集 $\Gamma \subset \Omega \cup \Pi$，由于
> $$
> \mathbf{g} -\mathcal{P}_{\Omega \cup \Pi} \mathbf{g} \perp \mathcal{R}(\mathbf{D}_{\Omega \cup \Pi}),
> $$
> 以及
> $$
> \mathcal{P}_{\Omega \cup \Pi} \mathbf{g} - \mathcal{P}_{\Gamma} \mathbf{g} \in \mathcal{R}(\mathbf{D}_{\Omega \cup \Pi}),
> $$
> 从而根据勾股定理，
> $$
> \left \| \mathbf{g} -\mathcal{P}_{\Gamma} \mathbf{g} \right \|_2^2 = \left \| \mathbf{g} -\mathcal{P}_{\Omega \cup \Pi} \mathbf{g} \right \|_2^2 + \left \| \mathcal{P}_{\Omega \cup \Pi} \mathbf{g} - \mathcal{P}_{\Gamma} \mathbf{g} \right \|_2^2.
> $$
> 对满足 $\operatorname{card}(\Gamma) = s$ 的指标集 $\Gamma$，上式左端在 $\Gamma = \mathcal{O}_{s}(\mathbf{g}) = \Omega$ 时取得最小值，因此右端第二项也在 $\Gamma = \Omega$ 时取得最小值，特别地，
> $$
> \left \| \mathcal{P}_{\Omega \cup \Pi} \mathbf{g} - \mathcal{P}_{\Omega} \mathbf{g} \right \|_2 \leq \left \| \mathcal{P}_{\Omega \cup \Pi} \mathbf{g} - \mathcal{P}_{\Pi}\mathbf{g} \right \|_2.
> $$

### 引理 4

对任意大小不超过 $s$ 的指标集 $S \subset [N]$，有
$$
\begin{align*}\left \| \mathcal{P}_{S} \mathbf{A}^* \right \|_{2 \to 2} & = \left \| \mathbf{A} \mathcal{P}_{S} \right \|_{2 \to 2} = \sup_{\| \mathbf{g} \|_2 = 1} \left \| \mathbf{A} \mathcal{P}_{S} \mathbf{g} \right \|_{2} \\& \leq \sqrt{1 + \delta_{s}} \sup_{\| \mathbf{g} \|_2 = 1} \left \| \mathcal{P}_{S} \mathbf{g} \right \|_{2} \leq \sqrt{1 + \delta_{s}}.\end{align*}
$$

### 引理 5

对任意大小不超过 $s$ 的指标集 $S \subset [N]$，有
$$
\left\| \mathcal{P}_S (\mathbf{A}^* \mathbf{A} - \mathbf{Id}) \mathcal{P}_S \right\|_{2 \to 2} \leq \delta_{s}.
$$

此外，对指标集 $S, T \subset [N]$，如果 $\operatorname{card}(S \cup T) \leq s$，那么
$$
\left\| \mathcal{P}_S (\mathbf{A}^* \mathbf{A} - \mathbf{Id}) \mathcal{P}_T \right\|_{2 \to 2} \leq \delta_{s}.
$$

> **证明：**
>
> 对任意 $\mathbf{g} \in \mathbb{C}^n$，由于 $\mathcal{P}_S(\mathbf{g})$ 是 $s$-synthesis sparse 的，因此
> $$
> \left\| \mathbf{A} \mathcal{P}_S \mathbf{g}  \right\|_2^2 \leq \left(1 + \delta_{s}\right) \left \| \mathcal{P}_S \mathbf{g} \right\|_2^2.
> $$
> 注意到 $\mathcal{P}_S (\mathbf{A}^* \mathbf{A} - \mathbf{Id}) \mathcal{P}_S$ 是自伴算子，于是
> $$
> \begin{align*}\left\| \mathcal{P}_S (\mathbf{A}^* \mathbf{A} - \mathbf{Id}) \mathcal{P}_S \right\|_{2 \to 2} & = \sup_{\| \mathbf{g} \|_2 = 1} \left | \left \langle \mathcal{P}_S (\mathbf{A}^* \mathbf{A} - \mathbf{Id}) \mathcal{P}_S \mathbf{g}, \mathbf{g} \right \rangle \right| \\& = \sup_{\| \mathbf{g} \|_2 = 1} \left | \left \langle \mathcal{P}_S \mathbf{A}^* \mathbf{A} \mathcal{P}_S \mathbf{g}, \mathbf{g} \right \rangle - \left \langle \mathcal{P}_S \mathcal{P}_S\mathbf{g}, \mathbf{g} \right \rangle \right| \\& = \sup_{\| \mathbf{g} \|_2 = 1} \left | \left \| \mathbf{A} \mathcal{P}_S \mathbf{g} \right \|_2^2 - \left \| \mathcal{P}_S \mathbf{g} \right \|_2^2 \right| \\& \leq \delta_{s} \cdot \sup_{\| \mathbf{g} \|_2 = 1} \left \| \mathcal{P}_S \mathbf{g} \right \|_2^2 \\& \leq \delta_{s} \cdot \sup_{\| \mathbf{g} \|_2 = 1} \left \| \mathbf{g} \right \|_2^2 = \delta_{s}.\end{align*}
> $$
> 对于第二个结论，只需注意到
> $$
> \left\| \mathcal{P}_S (\mathbf{A}^* \mathbf{A} - \mathbf{Id}) \mathcal{P}_T \right\|_{2 \to 2} 
> = \left\| \mathcal{P}_{S \cup T} \mathcal{P}_S (\mathbf{A}^* \mathbf{A} - \mathbf{Id}) \mathcal{P}_T \mathcal{P}_{S \cup T} \right\|_{2 \to 2}
> \leq \left\| \mathcal{P}_{S \cup T} (\mathbf{A}^* \mathbf{A} - \mathbf{Id}) \mathcal{P}_{S \cup T} \right\|_{2 \to 2}
> $$
> 即可。

## $\mathbf{D}$-CoSaMP 算法与近似最优指标集

### $\mathbf{D}$-CoSaMP 算法

+ **输入**：字典 $\mathbf{D} \in \mathbb{C}^{n \times N}$，测量矩阵 $\mathbf{A} \in \mathbb{C}^{m \times n}$，观测结果 $\mathbf{y} \in \mathbb{C}^m$，稀疏度 $s \in [N]$
+ **初始化**：$\mathbf{f}^0 = \mathbf{0}$，$S^0 = \varnothing$
+ **迭代**：
  $$
  \begin{align*}
  T^{k+1} & = S^{k} \cup \mathcal{O}_{2s}\left( \mathbf{A}^* (\mathbf{y} - \mathbf{A} \mathbf{f}^{k}) \right), \\
  \mathbf{g}^{k+1} & = \mathbf{D} \cdot \underset{\operatorname{supp(\mathbf{z})}  \subset T^{k+1}}{\arg \min} \ {\| \mathbf{y} - \mathbf{A} \mathbf{D} \mathbf{z} \|_2}, \\
  S^{k+1} & = \mathcal{O}_{s}\left( \mathbf{g}^{k + 1} \right), \\
  \mathbf{f}^{k+1} &= \mathcal{P}_{S^{k+1}} \mathbf{g}^{k+1}.
  \end{align*}
  $$

### 近似最优投影指标集

一般来说，最优的用于投影的指标集 $\mathcal{O}_{s}(\mathbf{g})$ 计算难度较大，实际计算中会倾向于计算其近似，也就是近似最优投影指标集 (near-optimal index set for orthogonal projection)。这里关于 "近似最优" 可以有不同定义，由此得到的 ($\mathbf{D}$-CoSaMP) 算法也有不同的收敛性结果。

+ **[DNW13]** 对任意 $\mathbf{g} \in \mathbb{C}^n$ 以及正整数 $s$，定义近似最优投影指标集 $\mathcal{N}_s(\mathbf{g})$。此近似指标集满足 $\operatorname{card}(\mathcal{N}_s(\mathbf{g})) \leq s$ 以及
  $$
  \left\| \mathcal{P}_{\mathcal{O}_s(\mathbf{g})} \mathbf{g} - 
  \mathcal{P}_{\mathcal{N}_s(\mathbf{g})} \mathbf{g} \right\|_{2} \leq \min \left(\epsilon_{1} \left\| \mathcal{P}_{\mathcal{O}_s(\mathbf{g})} \mathbf{g} \right\|_{2}, \ \epsilon_{2}\left\| \mathbf{g} - \mathcal{P}_{\mathcal{O}_s(\mathbf{g})} \mathbf{g}  \right\|_{2}\right),
  $$
  其中 $\epsilon_1, \epsilon_2 \geq 0$ 是与 $s$ 和 $\mathbf{g}$ 无关的固定参数。

+ **[GN15]** 对固定的正整数 $s$，称 $\mathcal{N}_s$ 和 $\widehat{\mathcal{N}_{2s}}$ 诱导出一对近似最优投影，如果对任意 $\mathbf{g} \in \mathbb{C}^n$，有 $\operatorname{card}(\mathcal{N}_s(\mathbf{g})) \leq s$ 和 $\operatorname{card}(\widehat{\mathcal{N}_{2s}}(\mathbf{g})) \leq 2s$ 成立，并且
  $$
  \begin{align*}
  \left\| \mathbf{g} - \mathcal{P}_{\mathcal{N}_{s}(\mathbf{g})} \mathbf{g} \right\|_{2} & \leq \ \tau_{1}\left\| \mathbf{g} - \mathcal{P}_{\mathcal{O}_s(\mathbf{g})} \mathbf{g}  \right\|_{2}, \\
  \left\| \mathcal{P}_{\widehat{\mathcal{N}_{2 s}}(\mathbf{g})} \mathbf{g} \right\|_{2} & \geq \ \tau_{2}\left\| \mathcal{P}_{\mathcal{O}_{2s}(\mathbf{g})} \mathbf{g} \right\|_{2},
  \end{align*}
  $$
  其中 $\tau_1, \tau_2 \geq 0$ 是与 $\mathbf{g}$ 无关的固定参数。

## [DNW13] 收敛性分析

($\mathbf{D}$-CoSaMP) 迭代过程：
$$
\begin{align*}
T^{k+1} & = S^{k} \cup \mathcal{N}_{2s}\left( \mathbf{A}^* (\mathbf{y} - \mathbf{A} \mathbf{f}^{k}) \right), \\
\mathbf{g}^{k+1} & = \mathbf{D} \cdot \underset{\operatorname{supp(\mathbf{z})}  \subset T^{k+1}}{\arg \min} \ {\| \mathbf{y} - \mathbf{A} \mathbf{D} \mathbf{z} \|_2}, \\
S^{k+1} & = \mathcal{N}_{s}\left( \mathbf{g}^{k + 1} \right), \\
\mathbf{f}^{k+1} &= \mathcal{P}_{S^{k+1}} \mathbf{g}^{k+1}.
\end{align*}
$$

### 命题 1：重建误差的迭代不等式

对固定的字典 $\mathbf{D} \in \mathbb{C}^{n \times N}$，假设测量矩阵 $\mathbf{A} \in \mathbb{C}^{m \times n}$ 以常数 $\delta_{4s}$ 满足 $\mathbf{D}$-RIP 条件，那么对任意的 $s$-synthesis sparse 待回复信号 $\mathbf{f} \in \mathbb{C}^m$ 以及观测误差 $\mathbf{e} \in \mathbb{C}^n$，将观测结果 $\mathbf{y} = \mathbf{A} \mathbf{f} + \mathbf{e}$ 作为输入运行 ($\mathbf{D}$-CoSaMP) 算法时，有如下关于重建误差的迭代不等式：$\forall k \geq 0$，
$$
\left\| \mathbf{f} - {\mathbf{f}}^{k + 1} \right\|_2 \leq c_1 \left\| \mathbf{f} - {\mathbf{f}}^{k} \right\|_2 + d_1 \left\| \mathbf{e} \right\|_2,
$$
其中 $c_1, d_1 > 0$ 是仅依赖于 $\mathbf{D}$-RIP 常数 $\delta_{4s}$ 以及近似参数 $\epsilon_1, \epsilon_2$ 的常数，
$$
\begin{align*}
c_1 & = \left(\left(2+\epsilon_{1}\right) \delta_{4 s}+\epsilon_{1}\right)(2 + \epsilon_2) \sqrt{\frac{1 + \delta_{4s}}{1 - \delta_{4s}}}, \\
d_1 & = \frac{2 + \left(2+\epsilon_{1}\right) \left({1 + \delta_{4 s}} \right)}{\sqrt{1 - \delta_{4s}}} (2 + \epsilon_2).
\end{align*}
$$

> **证明：**
>
> 以下分四部分证明上述误差迭代不等式。

### Part 1

$$
\left\| {\mathbf{f}} - {\mathbf{f}}^{k+1} \right\|_2 \leq (2 + \epsilon_2) \left\| \mathbf{f} - \mathbf{g}^{k + 1} \right\|_2.
$$

> 根据三角不等式，
> $$
> \left\| \mathbf{f} - \mathbf{f}^{k + 1} \right\|_2 \leq \left\| \mathbf{f} - \mathbf{g}^{k + 1} \right\|_2 + \left\| \mathbf{g}^{k+1} - \mathbf{f}^{k + 1} \right\|_2.
> $$
> 对于上式右端中的第二项，注意到 $\mathbf{f}^{k + 1} = \mathcal{P}_{\mathcal{N}_s(\mathbf{g}^{k+1})} \mathbf{g}^{k + 1}$，因此根据近似最优投影指标集的性质，有
> $$
> \begin{align*}
> \left\| \mathbf{g}^{k+1} - \mathbf{f}^{k + 1} \right\|_2 
> & \leq \left\| \mathbf{g}^{k+1} - \mathcal{P}_{\mathcal{O}_s(\mathbf{g}^{k+1})} \mathbf{g}^{k + 1} \right\|_2 + \left\| \mathcal{P}_{\mathcal{O}_s(\mathbf{g}^{k+1})} \mathbf{g}^{k + 1} - \mathbf{f}^{k+1}\right\|_2 \\
> & = \left\| \mathbf{g}^{k+1} - \mathcal{P}_{\mathcal{O}_s(\mathbf{g}^{k+1})} \mathbf{g}^{k + 1} \right\|_2 + \left\| \mathcal{P}_{\mathcal{O}_s(\mathbf{g}^{k+1})} \mathbf{g}^{k + 1} - \mathcal{P}_{\mathcal{N}_s(\mathbf{g}^{k+1})} \mathbf{g}^{k + 1} \right\|_2 \\
> & \leq (1 + \epsilon_2) \left\| \mathbf{g}^{k+1} - \mathcal{P}_{\mathcal{O}_s(\mathbf{g}^{k+1})} \mathbf{g}^{k + 1} \right\|_2.
> \end{align*}
> $$
> 因为 $\mathbf{f}$ 为 $s$-synthesis sparse信号，因此存在大小为 $s$ 的指标集 $S \subset [N]$ 使得 $\mathbf{f} \in \mathcal{R}(\mathbf{D}_S)$。根据 $\mathcal{O}_s(\mathbf{g}^{k+1})$ 以及投影算子的定义，
> $$
> \left\| \mathbf{g}^{k+1} - \mathcal{P}_{\mathcal{O}_s(\mathbf{g}^{k+1})} \mathbf{g}^{k + 1} \right\|_2 \leq \left\| \mathbf{g}^{k+1} - \mathcal{P}_{S} \mathbf{g}^{k + 1} \right\|_2 \leq \left\| \mathbf{g}^{k+1} - \mathbf{f} \right\|_2.
> $$
> 综上所述，可以得到
> $$
> \left\| {\mathbf{f}} - {\mathbf{f}}^{k+1} \right\|_2 \leq (2 + \epsilon_2) \left\| \mathbf{f} - \mathbf{g}^{k + 1} \right\|_2,
> $$
> 所需不等式成立。

### Part 2

$$
\left\| \mathbf{f} - \mathbf{g}^{k+1} \right\|_2 
\leq \sqrt{\frac{1 + \delta_{4s}}{1 - \delta_{4s}}} \left\| \mathcal{Q}_{T^{k+1}} \mathbf{f} \right\|_2 + \frac{2}{\sqrt{1 - \delta_{4s}}} \| \mathbf{e} \|_2.
$$

> 首先，由于 $\mathbf{g}^{k+1}$ 是 $3s$-synthesis sparse 的，并且 $\mathbf{f}$ 是 $s$-synthesis sparse 的，因此根据 $\mathbf{A}$ 的 $\mathbf{D}$-RIP 性质以及三角不等式，有
> $$
> \left\| \mathbf{f} - \mathbf{g}^{k+1} \right\|_2 
> \leq \frac{\left\| \mathbf{A} \mathbf{f} - \mathbf{A} \mathbf{g}^{k+1} \right\|_2}{\sqrt{1 - \delta_{4s}}}
> \leq \frac{\left\| \mathbf{y} - \mathbf{A} \mathbf{g}^{k+1} \right\|_2 + \| \mathbf{e} \|_2}{\sqrt{1 - \delta_{4s}}}.
> $$
> 对于分子中的第一项，注意到 $\mathbf{g}^{k+1}$ 的迭代公式为
> $$
> \mathbf{g}^{k+1} = \underset{\mathbf{g} \in \mathbb{C}^n}{\arg \min} \ {\| \mathbf{y} - \mathbf{A} \mathbf{g} \|_2} \quad \text{ s.t. } \quad \mathbf{g} \in \mathcal{R}\left( \mathbf{D}_{T^{k+1}} \right),
> $$
> 特别地，由于 $\mathcal{P}_{T^{k+1}} \mathbf{f} \in \mathcal{R}\left( \mathbf{D}_{T^{k+1}} \right)$，根据上式可以得到
> $$
> \begin{align*}
> \left\| \mathbf{y} - \mathbf{A} \mathbf{g}^{k+1} \right\|_2 
> & \leq \left\| \mathbf{y} - \mathbf{A} \mathcal{P}_{T^{k+1}} \mathbf{f} \right\|_2 \\
> & = \left\| \mathbf{A} \mathbf{f} - \mathbf{A} \mathcal{P}_{T^{k+1}} \mathbf{f} \right\|_2 + \| \mathbf{e} \|_2 \\
> & \leq \sqrt{1 + \delta_{4s}} \left\| \mathbf{f} - \mathcal{P}_{T^{k+1}} \mathbf{f} \right\|_2 + \| \mathbf{e} \|_2 .
> \end{align*}
> $$
> 其中最后一步利用了 $\operatorname{card}(T^{k+1}) \leq 3s$ 以及 $\mathbf{A}$ 的 $\mathbf{D}$-RIP 性质。综合上述式子，有
> $$
> \left\| \mathbf{f} - \mathbf{g}^{k+1} \right\|_2 
> \leq \sqrt{\frac{1 + \delta_{4s}}{1 - \delta_{4s}}} \left\| \mathbf{f} - \mathcal{P}_{T^{k+1}} \mathbf{f} \right\|_2 + \frac{2}{\sqrt{1 - \delta_{4s}}} \| \mathbf{e} \|_2,
> $$
> 所需不等式成立。

### Part 3

记第 $k$ 次迭代的残差为 $\mathbf{r}^k = \mathbf{y} - \mathbf{A} \mathbf{f}^{k}$，另外记 $\mathbf{A}^\* \mathbf{r}^k$ 的近似最优投影指标集为 $\Lambda^k = \mathcal{N}_{2s}(\mathbf{A}^\*\mathbf{r}^{k})$，那么
$$
\left \| \mathcal{Q}_{T^{k+1}} \mathbf{f} \right \|_2 \leq \left\| \mathcal{Q}_{\Lambda^k} \left( \mathbf{f} - \mathbf{f}^k \right ) \right\|_{2}.
$$

> **证明：**
>
> 根据定义，$T^{k+1} = S^k \cup \Lambda^k$。由于 ${\mathbf{f}}^k \in \mathcal{R}\left( \mathbf{D}_{S^k} \right) \subset \mathcal{R}\left( \mathbf{D}_{T^{k+1}} \right)$，因此 $\mathcal{P}_{T^{k+1}} \mathbf{f}^k = \mathbf{f}^k$，从而
> $$
> \left\| \mathcal{Q}_{T^{k+1}} \mathbf{f} \right\|_2^2 =
> \left \| \mathcal{Q}_{T^{k+1}} \mathbf{f} - \mathcal{Q}_{T^{k+1}} \mathbf{f}^k \right \|_2^2 = \left \| \mathcal{Q}_{T^{k+1}} \left({\mathbf{f}} - {\mathbf{f}}^k \right) \right \|_2^2.
> $$
> 对于右端项，注意到
> $$
> \| {\mathbf{f}} - {\mathbf{f}}^k \|_2^2 = \left \| \mathcal{P}_{T^{k+1}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right \|_2^2 + \left \| \mathcal{Q}_{T^{k+1}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right \|_2^2,
> $$
> 以及
> $$
> \| {\mathbf{f}} - {\mathbf{f}}^k \|_2^2 = \left \| \mathcal{P}_{\Lambda^{k}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right \|_2^2 + \left \| \mathcal{Q}_{\Lambda^{k}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right \|_2^2,
> $$
> 由于 $\Lambda^k \subset T^{k+1}$，利用引理 1 可知，
> $$
> \left \| \mathcal{P}_{\Lambda^{k}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right \|_2^2 \leq \left \| \mathcal{P}_{T^{k+1}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right \|_2^2.
> $$
> 因此综合上述式子得到，
> $$
> \left\| \mathcal{Q}_{T^{k+1}} \mathbf{f} \right\|_2^2 = \left \| \mathcal{Q}_{T^{k+1}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right \|_2^2 \leq \left \| \mathcal{Q}_{\Lambda^{k}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right \|_2^2,
> $$
> 开方即得所需结论。

### Part 4

$$
\left \| \mathcal{Q}_{\Lambda^{k}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right \|_2 \leq\left(\left(2+\epsilon_{1}\right) \delta_{4 s}+\epsilon_{1}\right)\| {\mathbf{f}} - {\mathbf{f}}^k \|_{2}+\left(2+\epsilon_{1}\right) \sqrt{1+\delta_{4 s}} \| \mathbf{e} \|_2.
$$

> 记 $\mathbf{A}^\*\mathbf{r}^{k}$ 的最优投影指标集为 $\Omega^k = \mathcal{O}_{2s}(\mathbf{A}^\*\mathbf{r}^{k})$，并记 ${\mathbf{f}} - {\mathbf{f}}^k$ 的最优投影指标集为 $\Pi^k = \mathcal{O}_{2s}({\mathbf{f}} - {\mathbf{f}}^k)$。根据引理 2 以及三角不等式，可以得到
> $$
> \begin{align*}
> \left\| \mathcal{Q}_{\Lambda^{k}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2}
> = & \  \left\| \left( {\mathbf{f}} - {\mathbf{f}}^k \right) - \mathcal{P}_{\Lambda^{k}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2} \\
> \leq & \ \left\| \left( {\mathbf{f}} - {\mathbf{f}}^k \right) - \mathcal{P}_{\Lambda^k} \mathbf{A}^* {\mathbf{r}}^k \right \|_{2} \\
> \leq & \ \left\| \left( {\mathbf{f}} - {\mathbf{f}}^k \right) - \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{r}}^k \right \|_{2} 
> + \left\| \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{r}}^k - \mathcal{P}_{\Omega^k} \mathbf{A}^* {\mathbf{r}}^k \right \|_{2} \\
> & + \left\| \mathcal{P}_{\Omega^k} \mathbf{A}^* {\mathbf{r}}^k - \mathcal{P}_{\Lambda^k} \mathbf{A}^* {\mathbf{r}}^k \right \|_{2} \\
> \leq & \ \left\| \left( {\mathbf{f}} - {\mathbf{f}}^k \right) - \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{A}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right)\right \|_{2}
> + \left\| \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{e}} \right \|_{2} \\
> & + \left\| \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{r}}^k - \mathcal{P}_{\Omega^k} \mathbf{A}^* {\mathbf{r}}^k \right \|_{2}
> + \left\| \mathcal{P}_{\Omega^k} \mathbf{A}^* {\mathbf{r}}^k - \mathcal{P}_{\Lambda^k} \mathbf{A}^* {\mathbf{r}}^k \right \|_{2}.
> \end{align*}
> $$
> 其中最后一个不等号利用了 $\mathbf{r}^k = \mathbf{y} - \mathbf{A} \mathbf{f}^{k} = \mathbf{A} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) + \mathbf{e}$。上述不等式右端有四项，这里先将第三项以及第四项处理成前面两项的形式。
>
> **(1)** 对于第三项，首先利用引理 3 可以得到下面的第一个不等式，第二步的等式则是利用引理 1，接下来的第三步则是再次利用了引理 2。在第四步中，只需注意到 $\mathbf{f} - \mathbf{f}^k$ 是 $2s$-synthesis sparse 的，因此有
> $$
> \mathcal{P}_{\Pi^k} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) = \mathbf{f} - \mathbf{f}^k.
> $$
> 第五步利用了三角不等式以及引理 1，最后一步则是由于 $\left\lVert \mathcal{Q}_{\Pi^k} \right\rVert_{2 \to 2} \leq 1$，
> $$
> \begin{align*}
> \left\| \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{r}}^k - \mathcal{P}_{\Omega^k} \mathbf{A}^* {\mathbf{r}}^k \right \|_{2} 
> & \leq \left\| \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{r}}^k - \mathcal{P}_{\Pi^k} \mathbf{A}^* {\mathbf{r}}^k \right \|_{2} \\
> & = \left\| \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{r}}^k - \mathcal{P}_{\Pi^k} \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{r}}^k \right \|_{2} \\
> & \leq \left\| \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{r}}^k - \mathcal{P}_{\Pi^k} \left( {\mathbf{f}} - {\mathbf{f}}^k + \mathbf{A}^* {\mathbf{e}}\right) \right \|_{2} \\
> & \leq \left\| \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* \mathbf{A} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) + \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{e}} - \left( {\mathbf{f}} - {\mathbf{f}}^k \right) - \mathcal{P}_{\Pi^k} \mathbf{A}^* {\mathbf{e}} \right \|_{2} \\
> & \leq \left\| \left( {\mathbf{f}} - {\mathbf{f}}^k \right) - \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{A}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right)\right \|_{2} 
> + \left\| \left(\mathbf{Id} - \mathcal{P}_{\Pi^k} \right) \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{e}} \right \|_{2} \\
> & \leq  \left\| \left( {\mathbf{f}} - {\mathbf{f}}^k \right) - \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{A}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right)\right \|_{2}
> + \left\| \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{e}} \right \|_{2}.
> \end{align*}
> $$
> **(2)** 对于最后一项，利用近似最优投影指标集的性质，再利用引理 1 以及三角不等式，可以得到
> $$
> \begin{align*}
> \left\| \mathcal{P}_{\Omega^k} \mathbf{A}^* {\mathbf{r}}^k - \mathcal{P}_{\Lambda^k} \mathbf{A}^* {\mathbf{r}}^k \right \|_{2} 
> \leq & \ \epsilon_1 \left\| \mathcal{P}_{\Omega^k} \mathbf{A}^* {\mathbf{r}}^k \right \|_{2} \\
> \leq & \ \epsilon_1 \left\| \mathcal{P}_{\Omega^k \cup \Pi^k} \mathbf{A}^* {\mathbf{r}}^k\right \|_{2} \\
> \leq & \ \epsilon_1 \left\| \mathcal{P}_{\Omega^k \cup \Pi^k} \mathbf{A}^* \mathbf{A} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right \|_{2} + \epsilon_1 \left\| \mathcal{P}_{\Omega^k \cup \Pi^k} \mathbf{A}^* \mathbf{e} \right \|_{2} \\
> \leq & \ \epsilon_1 \left\| {\mathbf{f}} - {\mathbf{f}}^k \right\|_2 + \epsilon_1  \left\| \left( {\mathbf{f}} - {\mathbf{f}}^k \right) - \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{A}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right)\right \|_{2} \\
> & + \epsilon_1 \left\| \mathcal{P}_{\Omega^k \cup \Pi^k} \mathbf{A}^* \mathbf{e} \right \|_{2}.
> \end{align*}
> $$
> 综上所述，
> $$
> \begin{align*}
> \left\| \mathcal{Q}_{\Lambda^{k}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2} 
> \leq & \ (2 + \epsilon_1) \left\| \left( {\mathbf{f}} - {\mathbf{f}}^k \right) - \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{A}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right)\right \|_{2} \\
> & + (2 + \epsilon_1) \left\| \mathcal{P}_{\Omega^k \cup \Pi^k} \mathbf{A}^* \mathbf{e} \right \|_{2} 
> + \epsilon_1 \left\| {\mathbf{f}} - {\mathbf{f}}^k \right\|_2.
> \end{align*}
> $$
> **(1)** 对上式的第一项，由于 ${\mathbf{f}} - {\mathbf{f}}^k \in \mathcal{R}\left(\mathbf{D}_{\Pi^k}\right) \subset \mathcal{R}\left(\mathbf{D}_{\Pi^k \cup \Omega^k} \right)$，于是
> $$
> {\mathbf{f}} - {\mathbf{f}}^k = \mathcal{P}_{\Omega^k \cup \Pi^k} \left( {\mathbf{f}} - {\mathbf{f}}^k \right).
> $$
> 再注意到 $\operatorname{card}(\Omega^k \cup \Pi^k) \leq 4s$，因此根据引理 5，可以得到
> $$
> \begin{align*}
> & \ \left\| \left( {\mathbf{f}} - {\mathbf{f}}^k \right) - \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{A}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right)\right \|_{2} \\
> = & \ \left\| \mathcal{P}_{\Omega^k \cup \Pi^k}\mathcal{P}_{\Omega^k \cup \Pi^k} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) - \mathcal{P}_{\Pi^k \cup \Omega^k} \mathbf{A}^* {\mathbf{A}} \mathcal{P}_{\Omega^k \cup \Pi^k} \left( {\mathbf{f}} - {\mathbf{f}}^k \right)\right \|_{2} \\
> = & \ \left\| \mathcal{P}_{\Omega^k \cup \Pi^k} (\mathbf{Id} - \mathbf{A}^* \mathbf{A}) \mathcal{P}_{\Omega^k \cup \Pi^k} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right \|_{2} \\
> \leq  & \ \delta_{4s} \| {\mathbf{f}} - {\mathbf{f}}^k \|_2.
> \end{align*}
> $$
> **(2)** 对第二项，由于 $\operatorname{card}(\Omega^k \cup \Pi^k) \leq 4s$，根据引理 4 可知，
> $$
> \left\| \mathcal{P}_{\Omega^k \cup \Pi^k} \mathbf{A}^* \mathbf{e} \right \|_{2} \leq \left \| \mathcal{P}_{\Omega^k \cup \Pi^k} \mathbf{A}^* \right \|_{2 \to 2} \| \mathbf{e} \|_2 \leq \sqrt{1 + \delta_{4s}} \| \mathbf{e} \|_2.
> $$
> 综上所述，有
> $$
> \left\| \mathcal{Q}_{\Lambda^{k}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2} \leq\left(\left(2+\epsilon_{1}\right) \delta_{4 s}+\epsilon_{1}\right)\| {\mathbf{f}} - {\mathbf{f}}^k \|_{2}+\left(2+\epsilon_{1}\right) \sqrt{1+\delta_{4 s}} \| \mathbf{e} \|_2
> $$
> 成立。

### Conclusion

> 为了得到原命题中的结论，将上述四个不等式依次代入即可：
> $$
> \begin{align*}
> \left\| \mathbf{f} - {\mathbf{f}}^{k + 1} \right\|_2
> \leq & \ (2 + \epsilon_2) \left\| \mathbf{f} - \mathbf{g}^{k + 1} \right\|_2 \\
> \leq & \ (2 + \epsilon_2) \sqrt{\frac{1 + \delta_{4s}}{1 - \delta_{4s}}} \left\| \mathcal{Q}_{T^{k+1}} \mathbf{f} \right\|_2 + \frac{4 + 2\epsilon_2}{\sqrt{1 - \delta_{4s}}} \| \mathbf{e} \|_2 \\
> \leq & \ (2 + \epsilon_2) \sqrt{\frac{1 + \delta_{4s}}{1 - \delta_{4s}}} \left\| \mathcal{Q}_{\Lambda^k} \left( \mathbf{f} - \mathbf{f}^k \right ) \right\|_{2} + \frac{4 + 2\epsilon_2}{\sqrt{1 - \delta_{4s}}} \| \mathbf{e} \|_2 \\
> \leq & \ \left(\left(2+\epsilon_{1}\right) \delta_{4 s}+\epsilon_{1}\right)(2 + \epsilon_2) \sqrt{\frac{1 + \delta_{4s}}{1 - \delta_{4s}}} \| {\mathbf{f}} - {\mathbf{f}}^k \|_{2} \\
> & + \frac{2 + \left(2+\epsilon_{1}\right) \left({1 + \delta_{4 s}} \right)}{\sqrt{1 - \delta_{4s}}} (2 + \epsilon_2) \| \mathbf{e} \|_2.
> \end{align*}
> $$
> 综上所述，命题 1 证毕。

## [GN15] 收敛性分析

($\mathbf{D}$-CoSaMP) 算法迭代过程：
$$
\begin{align*}
T^{k+1} & = S^{k} \cup \widehat{\mathcal{N}_{2s}}\left( \mathbf{A}^* (\mathbf{y} - \mathbf{A} \mathbf{f}^{k}) \right), \\
\mathbf{g}^{k+1} & = \mathbf{D} \cdot \underset{\operatorname{supp(\mathbf{z})}  \subset T^{k+1}}{\arg \min} \ {\| \mathbf{y} - \mathbf{A} \mathbf{D} \mathbf{z} \|_2}, \\
S^{k+1} & = \mathcal{N}_{s}\left( \mathbf{g}^{k + 1} \right), \\
\mathbf{f}^{k+1} &= \mathcal{P}_{S^{k+1}} \mathbf{g}^{k+1}.
\end{align*}
$$



### Part 1

$$
\left\| \mathbf{f} - {\mathbf{f}}^{k+1} \right\|_{2} \leq \left( 1 + {\tau_1} \right) \left \| \mathbf{f} - \mathbf{g}^{k+1} \right \|_2.
$$

> 首先注意到 $\mathbf{f}^{k + 1} = \mathcal{P}_{\mathcal{N}_{s}(\mathbf{g}^{k+1})} \mathbf{g}^{k + 1}$，因此根据 $\mathcal{N}_{s}$ 的性质，有
> $$
> \left \| \mathbf{g}^{k+1} - \mathbf{f}^{k+1} \right \|_2 \leq \tau_{1}\left\| \mathbf{g}^{k+1} - \mathcal{P}_{\mathcal{O}_s(\mathbf{g}^{k+1})} \mathbf{g}^{k+1} \right\|_{2} \leq \tau_{1}\left\| \mathbf{g}^{k+1} - \mathcal{P}_{S} \mathbf{g}^{k+1} \right\|_{2} \leq \tau_{1}\left\| \mathbf{g}^{k+1} - \mathbf{f}\right\|_{2}.
> $$
> 从而有
> $$
> \left\| \mathbf{f} - {\mathbf{f}}^{k+1} \right\|_{2} \leq \left \| \mathbf{f} - \mathbf{g}^{k+1} \right \|_2 + \left \| \mathbf{g}^{k+1} - \mathbf{f}^{k+1} \right \|_2 \leq \left( 1 + {\tau_1} \right) \left \| \mathbf{f} - \mathbf{g}^{k+1} \right \|_2.
> $$

### Part 2

$$
\left \| \mathbf{f} - \mathbf{g}^{k+1} \right \|_2 \leq \frac{1}{\sqrt{ 1- \delta_{4 s}^2 }} \left\| \mathcal{Q}_{T^{k+1}} \left(\mathbf{f} - \mathbf{g}^{k+1}\right)\right\|_{2}+ \frac{\sqrt{1+\delta_{4 s}}}{1-\delta_{4 s}} \|\mathbf{e}\|_{2}.
$$

> 根据 $\mathbf{g}^{k+1}$ 的定义，$\forall \mathbf{h} \in \mathcal{R}\left( \mathbf{D}_{T^{k+1}} \right)$，有
> $$
> \left \langle \mathbf{y} - \mathbf{A} \mathbf{g}^{k+1}, \mathbf{A} \mathbf{h} \right \rangle = 0,
> $$
> 将 $\mathbf{y} = \mathbf{A} \mathbf{f} + \mathbf{e}$ 代入，得到
> $$
> \left \langle \mathbf{f} - \mathbf{g}^{k+1}, \mathbf{A}^* \mathbf{A} \mathbf{h} \right \rangle = \left \langle \mathbf{e}, \mathbf{A} \mathbf{h} \right \rangle.
> $$
> 特别地，令 $\mathbf{h} = \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right)$，可以得到
> $$
> \begin{align*}
> \left \| \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \|_2^2
> & = \left \langle \mathbf{f} - \mathbf{g}^{k+1}, \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \rangle \\
> & = \left \langle \mathbf{f} - \mathbf{g}^{k+1}, (\mathbf{Id} - \mathbf{A}^* \mathbf{A})\mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \rangle + \left \langle \mathbf{f} - \mathbf{g}^{k+1}, \mathbf{A}^* \mathbf{A} \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \rangle \\
> & = \left \langle \mathbf{f} - \mathbf{g}^{k+1}, (\mathbf{Id} - \mathbf{A}^* \mathbf{A})\mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \rangle + \left \langle \mathbf{e}, \mathbf{A} \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \rangle.
> \end{align*}
> $$
> **(1)** 先处理这里出现的第一项。因为 $\mathbf{f}$ 为 $s$-synthesis sparse信号，因此存在大小为 $s$ 的指标集 $S \subset [N]$ 使得 $\mathbf{f} \in \mathcal{R}(\mathbf{D}_S)$。另外注意到 $\mathbf{g} \in \mathcal{R}\left( \mathbf{D}_{T^{k+1}} \right)$，因此有
> $$
> \begin{align*}
> & \ \left \langle \mathbf{f} - \mathbf{g}^{k+1}, (\mathbf{Id} - \mathbf{A}^* \mathbf{A})\mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \rangle \\
> = & \ \left \langle \mathcal{P}_{S \cup T^{k+1}}(\mathbf{f} - \mathbf{g}^{k+1}), (\mathbf{Id} - \mathbf{A}^* \mathbf{A})\mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \rangle \\
> = & \ \left \langle \mathbf{f} - \mathbf{g}^{k+1}, \mathcal{P}_{S \cup T^{k+1}}(\mathbf{Id} - \mathbf{A}^* \mathbf{A})\mathcal{P}_{S \cup T^{k+1}} \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \rangle \\
> \leq & \ \left\| \mathbf{f} - \mathbf{g}^{k+1} \right\|_2 \left\| \mathcal{P}_{S \cup T^{k+1}}(\mathbf{Id} - \mathbf{A}^* \mathbf{A})\mathcal{P}_{S \cup T^{k+1}} \right\|_{2 \to 2} \left\| \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right\|_2 \\
> \leq & \ \delta_{4 s} \left\| \mathbf{f} - \mathbf{g}^{k+1} \right\|_2 \left\| \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right\|_2,
> \end{align*}
> $$
> 这里最后一步利用了引理 5。
>
> **(2)** 对于第二项，可以利用 Cauchy–Schwarz 不等式以及引理 4 推出：
> $$
> \begin{align*}
> \left \langle \mathbf{e}, \mathbf{A} \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \rangle 
> & \leq \left \| \mathbf{e} \right\|_2  \left\| \mathbf{A} \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \|_2 \\
> & \leq \sqrt{1 +\delta_{4 s}} \left\| \mathbf{e} \right\|_2 \left\| \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right\|_2.
> \end{align*}
> $$
> 将这两条不等式代回原式，约去 $\left\| \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right\|_2$，可以得到
> $$
> \left \| \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \|_2 \leq \delta_{4 s} \left\| \mathbf{f} - \mathbf{g}^{k+1} \right\|_2 + \sqrt{1 +\delta_{4 s}} \left\| \mathbf{e} \right\|_2
> $$
> 从而有
> $$
> \begin{align*}
> \left \| \mathbf{f} - \mathbf{g}^{k+1} \right \|_2^2 
> & = \left \| \mathcal{P}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \|_2^2 + \left\| \mathcal{Q}_{T^{k+1}} \left(\mathbf{f} - \mathbf{g}^{k+1}\right)\right\|_{2}^2 \\
> & \leq \left( \delta_{4 s} \left\| \mathbf{f} - \mathbf{g}^{k+1} \right\|_2 + \sqrt{1 +\delta_{4 s} } \left\| \mathbf{e} \right\|_2 \right)^2 + \left\| \mathcal{Q}_{T^{k+1}} \left(\mathbf{f} - \mathbf{g}^{k+1}\right)\right\|_{2}^2
> \end{align*}
> $$
> 注意到上式其实是关于 $\left \| \mathbf{f} - \mathbf{g}^{k+1} \right \|_2$ 二次多项式的不等式，因此可以用此多项式的较大的零点作为 $\left \| \mathbf{f} - \mathbf{g}^{k+1} \right \|_2$ 的上界，利用求根公式：
> $$
> \begin{align*}
> \left \| \mathbf{f} - \mathbf{g}^{k+1} \right \|_2
> & \leq \frac{\delta_{4 s} \sqrt{1 + \delta_{4 s}} \| \mathbf{e} \|_2 + \sqrt{\left( 1 + \delta_{4 s} \right) \| \mathbf{e} \|_2^2 + \left( 1- \delta_{4 s}^2 \right) \left\| \mathcal{Q}_{T^{k+1}} \left(\mathbf{f} - \mathbf{g}^{k+1}\right)\right\|_{2}^2} }{1- \delta_{4 s}^2} \\
> & \leq \frac{\left( 1 + \delta_{4 s} \right) \sqrt{1 + \delta_{4 s}} \| \mathbf{e} \|_2 + \sqrt{ 1- \delta_{4 s}^2 } \left\| \mathcal{Q}_{T^{k+1}} \left(\mathbf{f} - \mathbf{g}^{k+1}\right)\right\|_{2} } {1- \delta_{4 s}^2} \\
> & = \frac{1}{\sqrt{ 1- \delta_{4 s}^2 }} \left\| \mathcal{Q}_{T^{k+1}} \left(\mathbf{f} - \mathbf{g}^{k+1}\right)\right\|_{2} +\frac{\sqrt{1+\delta_{4 s}}}{1-\delta_{4 s}} \|\mathbf{e}\|_{2}
> \end{align*}
> $$
> 其中第二个不等号利用了 $\forall a, b \geq 0$，有 $\sqrt{a^2 + b^2} \leq a + b$ 成立。

### Part 3

$$
\left \| \mathcal{Q}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \|_2 \leq \left\| \mathcal{Q}_{T^{k+1}} \left( \mathbf{f} - \mathbf{f}^{k} \right) \right\|_{2}.
$$

> 根据三角不等式，
> $$
> \left \| \mathcal{Q}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \|_2 \leq \left\| \mathcal{Q}_{T^{k+1}} \left( \mathbf{f} - \mathbf{f}^{k} \right) \right\|_{2} 
> + \left \| \mathcal{Q}_{T^{k+1}} \left( \mathbf{f}^{k} - \mathbf{g}^{k+1} \right) \right \|_2.
> $$
> 由于 $\mathbf{g}^{k+1} \in \mathcal{R}(\mathbf{D}_{T^{k+1}})$ 以及 $\mathbf{f}^{k} \in \mathcal{R}(\mathbf{D}_{S^{k}}) \subset \mathcal{R}(\mathbf{D}_{T^{k+1}})$，因此
> $$
> \mathcal{Q}_{T^{k+1}} \left( \mathbf{f}^{k} - \mathbf{g}^{k+1} \right) = \mathbf{0},
> $$
> 进而有
> $$
> \left \| \mathcal{Q}_{T^{k+1}} \left( \mathbf{f} - \mathbf{g}^{k+1} \right) \right \|_2 \leq \left\| \mathcal{Q}_{T^{k+1}} \left( \mathbf{f} - \mathbf{f}^{k} \right) \right\|_{2}.
> $$

### Part 4

存在仅依赖于 $\mathbf{D}$-RIP 常数 $\delta_{4s}$ 以及近似参数 $\tau_2$ 的常数 $\rho_1, \kappa_1 > 0$ 使得
$$
\left\| \mathcal{Q}_{T^{k+1}} \left( \mathbf{f} - \mathbf{f}^{k} \right) \right\|_{2} \leq \rho_1 \left\| \mathbf{f} - {\mathbf{f}}^{k} \right\|_{2} + \kappa_1 \left\| \mathbf{e} \right\|_{2}.
$$


> 根据 $\widehat{\mathcal{N}_{2s}}$ 的性质，对任意 $\mathbf{h} \in \mathbb{C}^n$ 以及大小不超过 $2s$ 的指标集 $\Pi \subset [N]$，有
> $$
> \begin{align*}
> \left\| \mathcal{P}_{\widehat{\mathcal{N}_{2 s}}(\mathbf{h})} \mathbf{h} \right\|_{2}^2 & \geq \tau_{2}^2\left\| \mathcal{P}_{\mathcal{O}_{2s}(\mathbf{h})} \mathbf{h} \right\|_{2}^2
> = \tau_{2}^2 \left( \left\| \mathbf{h} \right\|_{2}^2 - \left\| \mathbf{h} - \mathcal{P}_{\mathcal{O}_{2s}(\mathbf{h})} \mathbf{h} \right\|_{2}^2 \right) \\
> & \geq \tau_{2}^2 \left( \left\| \mathbf{h} \right\|_{2}^2 - \left\| \mathbf{h} - \mathcal{P}_{\Pi} \mathbf{h} \right\|_{2}^2 \right) = \tau_{2}^2\left\| \mathcal{P}_{\Pi} \mathbf{h} \right\|_{2}^2.
> \end{align*}
> $$
> 特别地，可以令 $\mathbf{h} = \mathbf{A}^\* \mathbf{r}^k$ 以及 $\Pi = S \cup S^k$，其中 $\mathbf{r}^k$ 为第 $k$ 次迭代的残差，即 $\mathbf{r}^k = \mathbf{y} - \mathbf{A} \mathbf{f}^{k}$。另外注意到 $T^{k+1} = S^k \cup \widehat{\mathcal{N}_{2 s}}(\mathbf{A}^* \mathbf{r}^k)$，因此
> $$
> \left\| \mathcal{P}_{T^{k+1}} \mathbf{A}^* \mathbf{r}^k \right\|_{2}^2 
> \geq \left\| \mathcal{P}_{\widehat{\mathcal{N}_{2 s}}(\mathbf{A}^* \mathbf{r}^k)} \mathbf{A}^* \mathbf{r}^k \right\|_{2}^2 \geq \tau_2^2 \left\| \mathcal{P}_{S \cup S^k} \mathbf{A}^* \mathbf{r}^k \right\|_{2}^2.
> $$
> 接下来分别给出上式左端的上限、右端的下限，推导过程中需要利用到一个结论是：对任意 $\mathbf{h}_1, \mathbf{h}_2 \in \mathbb{C}^n$ 以及 $\alpha > 0$，根据 Cauchy–Schwarz 不等式以及基本不等式，可以推出
> $$
> \begin{align*}
> \left\| \mathbf{h}_1 + \mathbf{h}_2 \right\|_2^2 
> & = \left\| \mathbf{h}_1 \right\|_2^2 + \left\| \mathbf{h}_2 \right\|_2^2 + 2 \operatorname{Re} \left \langle \mathbf{h}_1, \mathbf{h}_2 \right \rangle \\
> & \leq \left\| \mathbf{h}_1 \right\|_2^2 + \left\| \mathbf{h}_2 \right\|_2^2 + 2 \left\| \mathbf{h}_1 \right\|_2\left\| \mathbf{h}_2 \right\|_2  \\
> & \leq \left(1 + \frac{1}{\alpha} \right) \left\| \mathbf{h}_1 \right\|_2^2 + \left(1 + {\alpha} \right) \left\| \mathbf{h}_2 \right\|_2^2.
> \end{align*}
> $$
>
> 假设 $\gamma, \xi_1, \xi_2 > 0$ 都是待定常数。
>
> **(1)** 对于左端，利用 $\mathbf{r}^k = \mathbf{A} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) + \mathbf{e}$，有
> $$
> \begin{align*}
> \left\| \mathcal{P}_{T^{k+1}} \mathbf{A}^* \mathbf{r}^k \right\|_{2}^2
> \leq & \ \left( 1 + \frac{1}{\gamma} \right) \left\| \mathcal{P}_{T^{k+1}} \mathbf{A}^* \mathbf{e} \right\|_{2}^2 
> + (1 + \gamma) \left\| \mathcal{P}_{T^{k+1}} \mathbf{A}^* \mathbf{A} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2}^2 \\
> \leq & \ \left( 1 + \frac{1}{\gamma} \right) \left\| \mathcal{P}_{T^{k+1}} \mathbf{A}^* \mathbf{e} \right\|_{2}^2 
> + (1 + \gamma)(1 + \xi_1) \left\| \mathcal{P}_{T^{k+1}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2}^2 \\
> & \ + (1 + \gamma) \left( 1 + \frac{1}{\xi_1} \right) \left\| \mathcal{P}_{T^{k+1}} (\mathbf{A}^* \mathbf{A} - \mathbf{Id}) \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2}^2 \\
> = & \ \left( 1 + \frac{1}{\gamma} \right) \left\| \mathcal{P}_{T^{k+1}} \mathbf{A}^* \mathbf{e} \right\|_{2}^2 
> + (1 + \gamma)(1 + \xi_1) \left[ \left \| {\mathbf{f}} - {\mathbf{f}}^k \right \| -  \left\| \mathcal{Q}_{T^{k+1}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2}^2 \right] \\	
> & \ + (1 + \gamma) \left( 1 + \frac{1}{\xi_1} \right) \left\| \mathcal{P}_{T^{k+1}} (\mathbf{A}^* \mathbf{A} - \mathbf{Id}) \mathcal{P}_{S \cup S^{k}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2}^2 \\
> \leq & \ \left( 1 + \frac{1}{\gamma} \right) (1 + \delta_{4 s}) \left\| \mathbf{e} \right\|_{2}^2 
> - (1 + \gamma)(1 + \xi_1) \left\| \mathcal{Q}_{T^{k+1}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2}^2 \\	
> & \ + (1 + \gamma) \left[ 1 + \xi_1 + \left( 1 + \frac{1}{\xi_1} \right) \delta_{4s}^2 \right] \left\| {\mathbf{f}} - {\mathbf{f}}^k \right \|_{2}^2.
> \end{align*}
> $$
> 其中第三步利用了 ${\mathbf{f}} - {\mathbf{f}}^k \in \mathcal{R}(\mathbf{D}_{S \cup S^k} )$，最后一步则是利用引理 4 与引理 5。
>
> **(2)** 对于右端，再次利用引理 4 与引理 5，可以得到
> $$
> \begin{align*}
> \left\| \mathcal{P}_{S \cup S^k} \mathbf{A}^* \mathbf{r}^k \right\|_{2}^2
> \geq & \ \frac{1}{1 + \gamma} \left\| \mathcal{P}_{S \cup S^k} \mathbf{A}^* \mathbf{A} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2}^2 
> - \frac{1}{\gamma} \left\| \mathcal{P}_{S \cup S^k} \mathbf{A}^* \mathbf{e} \right\|_{2}^2 \\
> \geq & \ \frac{1}{1 + \gamma} \frac{1}{1 + \xi_2} \left\| \mathcal{P}_{S \cup S^k} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2}^2 
> - \frac{1}{1 + \gamma} \frac{1}{\xi_2} \left\| \mathcal{P}_{S \cup S^k} (\mathbf{A}^* \mathbf{A} - \mathbf{Id}) \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2}^2 \\
> & \ - \frac{1}{\gamma} \left\| \mathcal{P}_{S \cup S^k} \mathbf{A}^* \mathbf{e} \right\|_{2}^2 \\
> \geq & \ \frac{1}{1 + \gamma} \left( \frac{1}{1 + \xi_2} - \frac{1}{\xi_2} \delta_{4 s}^2 \right) \left\| {\mathbf{f}} - {\mathbf{f}}^k \right \|_{2}^2
> - \frac{1 + \delta_{4s}}{\gamma} \left\| \mathbf{e} \right\|_{2}^2.
> \end{align*}
> $$
> 将上述上限、下限代回原式并进行整理，可以推出
> $$
> \left\| \mathcal{Q}_{T^{k+1}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2}^2 \leq \rho_1^2 \left\| {\mathbf{f}} - {\mathbf{f}}^k \right\|_{2}^2 + \kappa_1^2 \left\| \mathbf{e} \right\|_{2}^2,
> $$
> 其中
> $$
> \begin{align*}
> \rho_1^2 & = 1 + \frac{1}{\xi_1} \delta_{4s}^2 - \frac{\tau_2^2}{(1 + \gamma)^2(1 + \xi_1)} \left( \frac{1}{1 + \xi_2} - \frac{1}{\xi_2} \delta_{4s}^2 \right), \\
> \kappa_1^2 & = \frac{1 + \delta_{4s}}{\gamma(1 + \xi_1)} + \frac{\tau_2^2(1 + \delta_{4s})}{\gamma(1 + \gamma)(1 + \xi_1)}.
> \end{align*}
> $$
> 要得到所要求的结论，只需注意到
> $$
> \left\| \mathcal{Q}_{T^{k+1}} \left( {\mathbf{f}} - {\mathbf{f}}^k \right) \right\|_{2} \leq \left[ \rho_1^2 \left\| {\mathbf{f}} - {\mathbf{f}}^k \right\|_{2}^2 + \kappa_1^2 \left\| \mathbf{e} \right\|_{2}^2 \right]^{\frac{1}{2}} \leq \rho_1 \left\| {\mathbf{f}} - {\mathbf{f}}^k \right\|_{2} + \kappa_1 \left\| \mathbf{e} \right\|_{2}
> $$
> 即可。接下来确定待定常数 $\xi_1$ 与 $\xi_2$ 的值。先对 $\rho_1$ 关于 $\xi_2$ 求最小值，得 $\xi_2 = \delta_{4s} / (1-\delta_{4s})$ 时，有
> $$
> \rho_1^2 = 1 + \frac{1}{\xi_1} \delta_{4s}^2 - \frac{\tau_2^2 \left(1 - \delta_{4 s}\right)^2 }{(1 + \gamma)^2(1 + \xi_1)}.
> $$
> 接下来对 $\rho_1$ 关于 $\xi_2$ 求最小值，得
> $$
> \xi_1 =  \left[ \frac{\tau_2 (1 - \delta_{4s})}{ \left( 1 + \gamma \right) \delta_{4s}} - 1 \right]^{-1}
> $$
> 时，有
> $$
> \rho_1^2 = 1 - \left[ \delta_{4s} -  \frac{\tau_2 (1 - \delta_{4s})}{1 + \gamma} \right]^2 = 1 - \left[ \left( 1 + \frac{\tau_2}{1 + \gamma} \right) \delta_{4s} -  \frac{\tau_2}{1 + \gamma} \right]^2.
> $$
>

### Conclusion

> 综合上述结论，可以得到
> $$
> \begin{align*}
> \left\| \mathbf{f} - {\mathbf{f}}^{k + 1} \right\|_2
> \leq & \ \left( 1 + {\tau_1} \right) \left \| \mathbf{f} - \mathbf{g}^{k+1} \right \|_2 \\
> \leq & \ \frac{1 + {\tau_1}}{\sqrt{ 1- \delta_{4 s}^2 }} \left\| \mathcal{Q}_{T^{k+1}} \left(\mathbf{f} - \mathbf{g}^{k+1}\right)\right\|_{2}
> + \frac{\left( 1 + {\tau_1} \right)\sqrt{1+\delta_{4 s}}}{1-\delta_{4 s}} \|\mathbf{e}\|_{2} \\
> \leq & \ \frac{1 + {\tau_1}}{\sqrt{ 1- \delta_{4 s}^2 }}  \left\| \mathcal{Q}_{T^{k+1}} \left( \mathbf{f} - \mathbf{f}^{k} \right) \right\|_{2}
> + \frac{\left( 1 + {\tau_1} \right)\sqrt{1+\delta_{4 s}}}{1-\delta_{4 s}} \|\mathbf{e}\|_{2} \\
> \leq & \ \frac{ \rho_1\left( 1 + {\tau_1} \right)}{\sqrt{ 1- \delta_{4 s}^2 }}  \left\| \mathbf{f} - {\mathbf{f}}^{k} \right\|_{2} 
> + \left( 1 + {\tau_1} \right) \left( \frac{ \rho_1}{\sqrt{ 1- \delta_{4 s}^2 }} + \frac{\sqrt{1+\delta_{4 s}}}{1-\delta_{4 s}} \right) \|\mathbf{e}\|_{2} \\
> \triangleq & \ \rho_2 \left\| \mathbf{f} - {\mathbf{f}}^{k} \right\|_{2} + \kappa_2 \|\mathbf{e}\|_{2}.
> \end{align*}
> $$
> 注意到
> $$
> \rho_2^2 = \frac{\rho_1^2(1 + {\tau_1})^2}{ 1- \delta_{4 s}^2 } = \frac{(1 + {\tau_1})^2}{ 1- \delta_{4 s}^2 } \left \{ 1 - \left[ \left( 1 + \frac{\tau_2}{1 + \gamma} \right) \delta_{4s} -  \frac{\tau_2}{1 + \gamma} \right]^2 \right \},
> $$
>
> 将上式代入不等式 $\rho_2^2 < 1$ 并进行整理，可以得到
> $$
> \left[ \frac{1}{(1 + \tau_1)^2} - \left( 1 + \frac{\tau_2}{1 + \gamma} \right)^2 \right] \delta_{4s}^2 + \frac{2\tau_2}{1 + \gamma}\left( 1 + \frac{\tau_2}{1 + \gamma} \right) \delta_{4s} + \left[ 1 - \frac{1}{(1 + \tau_1)^2} - \frac{\tau_2^2}{(1 + \gamma)^2} \right] < 0.
> $$
> 上述方程的二次项系数小于 0，一次项系数大于 0。另外，如果记 $u = 1/ \left( 1 +\tau_1 \right)$ 以及 $v = \tau_2 / (1 + \gamma)$，那么方程的判别式大于 0：
> $$
> \begin{align*}
> \Delta 
> & = 4 v^2 (1 + u)^2 - 4 (1 - u^2 - v^2) \left[ u^2 - ( 1 + v )^2 \right] \\
> & = \left( 1 - u^2 \right) u^2 \left[ \frac{v^2}{1 - u^2} + \frac{(1 + v)^2}{u^2} - 1\right] > 0,
> \end{align*}
> $$
> 这是由于从 $1 + v > 1$ 以及 $u < 1$ 可以推出 ${(1 + v)^2}/{u^2} > 1$。因此，当且仅当常数项小于 0 时，上述不等式方程的解区间包含 0 的某个邻域。综上，如果上述二次多项式的常数项小于 0 也就是
> $$
> (1 + \tau_1)^2 \left[1  - \frac{\tau_2^2}{(1 + \gamma)^2}\right] < 1,
> $$
> 记 $\delta^\*$ 为方程较小的零点，那么当 $\mathbf{A}$ 的 $\mathbf{D}$-RIP 常数满足 $\delta_{4s} < \delta^\*$ 时，常数 $\rho_2$ 满足 $\rho_2 < 1$。命题 证毕。

