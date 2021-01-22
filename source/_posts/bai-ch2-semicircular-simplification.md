---
title: Semicircular Law for Wigner Matrices - Matrix Simplification
date: 2020-11-10 16:01:56
tags: 
  - Eigenvalue
  - Wigner Matrix
  - Semicircle Law
categories: Random Matrix
mathjax: true
---

[Notes] <u>Spectral analysis of large dimensional random matrices</u> by Zhidong Bai & Jack W. Silverstein.

<!--more-->

## Step 0 - Truncation

$\mathbf{W}_n = \mathbf{X}_n / \sqrt{n}$.

根据条件，对任意 $\eta > 0$, 有
$$
\lim_{n \rightarrow \infty} \frac{1}{\eta^{2} n^{2}} \sum_{j, k = 1}^n \mathbb{E} \left [ \left|x_{j k}^{(n)}\right|^{2} \cdot \mathbb{I}\left(\left|x_{j k}^{(n)}\right| \geq \eta \sqrt{n}\right) \right ]=0.
$$
因此存在非增序列 $\{ \eta_n: n \geq 1 \}$ 使得
$$
\lim_{n \rightarrow \infty} \frac{1}{\eta_n^{2} n^{2}} \sum_{j, k = 1}^n \mathbb{E} \left [ \left|x_{j k}^{(n)}\right|^{2} \cdot \mathbb{I}\left(\left|x_{j k}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ]=0.
$$

## Step 1 - Truncation

定义 $\widetilde{\mathbf{W}}_n = \left [ \widetilde{w}_{jk}^{(n)} \right]_{j,k = 1}^n$，其中
$$
\widetilde{w}_{jk}^{(n)} = \frac{1}{\sqrt{n}} x_{j k}^{(n)} \cdot \mathbb{I}\left(\left|x_{j k}^{(n)}\right| < \eta_n \sqrt{n}\right).
$$
注意到对任意随机矩阵 $\mathbf{A} = (\mathbf{a}_1, \cdots, \mathbf{a}_n) \in \mathbb{C}^{n \times n}$，其秩满足
$$
\operatorname{rank} (\mathbf{A}) \leq \operatorname{card} \{ 1 \leq j \leq n: \mathbf{a}_j \not= \mathbf{0} \},
$$
其中
$$
\begin{align*}
& \mathbf{a}_j = \mathbf{0} 
\quad \Leftrightarrow \quad
\mathbb{I} (\mathbf{a}_j \not= \mathbf{0}) = 0
\quad \Leftrightarrow \quad
\sum_{k=1}^n \mathbb{I} ({a}_{jk} \not= {0}) = 0, \\
& \mathbf{a}_j \not= \mathbf{0} 
\quad \Leftrightarrow \quad
\mathbb{I} (\mathbf{a}_j \not= \mathbf{0}) = 1
\quad \Leftrightarrow \quad
\sum_{k=1}^n \mathbb{I} ({a}_{jk} \not= {0}) \geq 1.
\end{align*}
$$
因此
$$
\operatorname{rank} (\mathbf{A}) 
\leq \sum_{j=1}^n \mathbb{I} (\mathbf{a}_{j} \not= \mathbf{0})
\leq \sum_{j,k=1}^n \mathbb{I} ({a}_{jk} \not= {0}).
$$

$$
\begin{align*}
\left \| F^{\mathbf{W}_n} - F^{\widetilde{\mathbf{W}}_n} \right \| 
& \leq \frac{1}{n} \operatorname{rank} \left ( \mathbf{W}_n - \widetilde{\mathbf{W}}_n \right )
\leq \frac{1}{n} \sum_{j,k=1}^n \mathbb{I} \left( \tilde{w}_{j k}^{(n)} \not= {w}_{j k}^{(n)} \right)
\\
& \leq \frac{1}{n} \sum_{j,k=1}^n \mathbb{I}\left(\left|x_{j k}^{(n)}\right| \geq \eta_n \sqrt{n}\right)
\leq \frac{2}{n} \sum_{1 \leq j \leq k \leq n} \mathbb{I}\left(\left|x_{j k}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \triangleq 2S_n.
\end{align*}
$$

此处 $S_n$ 是 $n(n+1)/2$ 个独立随机变量的和，其中每个随机变量都以 $1/n$ 为一致的界。注意到
$$
\begin{align*}
\mu_n 
& := \mathbb{E} S_n
= \frac{1}{n} \sum_{1 \leq j \leq k \leq n} \mathbb{E} \left [ \mathbb{I}\left(\left|x_{j k}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ] \\
& \leq \frac{1}{\eta_n^2 n^2} \sum_{1 \leq j \leq k \leq n} \mathbb{E} \left [ \left|x_{j k}^{(n)}\right|^{2} \cdot \mathbb{I}\left(\left|x_{j k}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ],
\end{align*}
$$
于是 $\mu_n = o(1)$。以及
$$
\begin{align*}
\sigma_n^2 
& := \operatorname{Var} \left [ S_n \right ] 
= \frac{1}{n^2} \sum_{1 \leq j \leq k \leq n} \mathbb{E} \left [ \mathbb{I}\left(\left|x_{j k}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ] \\ 
& \leq \frac{1}{\eta_n^2 n^3} \sum_{1 \leq j \leq k \leq n} \mathbb{E} \left [ \left|x_{j k}^{(n)}\right|^{2} \cdot \mathbb{I}\left(\left|x_{j k}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ].
\end{align*}
$$
于是 $\sigma_n^2 = o(1/n)$。因此对任意 $\varepsilon > 0$，存在 $N_0 \in \mathbb{Z}_+$ 使得
$$
\mu_n < \varepsilon/2 \quad \text{ and } \quad \sigma_n^2 < \varepsilon/(2n), \quad \forall n \geq N_0.
$$
另一方面，根据 Bernstein 不等式，有
$$
\mathbb{P} \left ( S_n - \mu_n \geq \frac{\varepsilon}{2} \right ) 
\leq 2 \exp \left ( - \frac{\varepsilon^2/8}{\sigma_n^2 + \varepsilon/(2n)} \right ).
$$
综合上述两式，对 $n \geq N_0$，有
$$
\begin{align*}
\mathbb{P} \left ( S_n > \varepsilon \right ) 
& \leq \mathbb{P} \left ( S_n - \mu_n \geq \frac{\varepsilon}{2} \right ) 
\leq 2 \exp \left ( - \frac{\varepsilon^2/8}{\sigma_n^2 + \varepsilon/(2n)} \right ) \\
& \leq 2 \exp \left ( - \frac{\varepsilon^2/8}{\varepsilon/(2n) + \varepsilon/(2n)} \right )
= 2 \mathrm{e}^{- {n\varepsilon}/{8}}.
\end{align*}
$$
由于 $\sum_{n = N_0}^{\infty} \mathrm{e}^{- {n\varepsilon}/{8}} < \infty$，根据引理 知几乎必然有
$$
S_n \to 0
\quad \Rightarrow \quad
\left \| F^{\mathbf{W}_n} - F^{\widetilde{\mathbf{W}}_n} \right \| \to 0.
$$

## Step 2 - Removing Diagonal Elements

令 $\widehat{\mathbf{W}}_n$ 为 $\widetilde{\mathbf{W}}_n$ 对角线元素置 $0$ 之后得到的矩阵，即
$$
\widehat{w}_{jk}^{(n)} := 
\begin{cases}
\widetilde{w}_{jk}^{(n)}, & \text{ if } j \not= k, \\
0, & \text{ if } j = k.
\end{cases}
$$
那么
$$
L^3 \left ( F^{\widetilde{\mathbf{W}}_n}, F^{\widehat{\mathbf{W}}_n} \right )
\leq \frac{1}{n} \left \| \widetilde{\mathbf{W}}_n - \widehat{\mathbf{W}}_n \right \|_F^2
= \frac{1}{n^2} \sum_{k = 1}^n \left | x_{kk}^{(n)} \right |^2 \cdot \mathbb{I}\left(\left|x_{k k}^{(n)}\right| < \eta_n \sqrt{n}\right) \triangleq Y_n.
$$
注意到 $Y_n$ 为非负随机变量，并且
$$
\mathbb{E} Y_n^2 = 
\frac{1}{n^4} \sum_{k = 1}^n \mathbb{E} \left [ \left | x_{kk}^{(n)} \right |^4 \cdot \mathbb{I}\left(\left|x_{k k}^{(n)}\right| < \eta_n \sqrt{n}\right) \right ]
\leq \frac{1}{n^4} \sum_{k = 1}^n \eta_n^2 n = \frac{\eta_n^2}{n^2},
$$
因此对于任意的 $\varepsilon > 0$，
$$
\mathbb{P} (Y_n > \varepsilon) \leq \frac{1}{\varepsilon^2} \mathbb{E} |Y_n|^2 \leq \frac{\eta_n^2}{n^2 \varepsilon^2}.
$$
由于 $\sum_{n = 1}^{\infty} \eta_n^2 / (n^2 \varepsilon^2) < \infty$，根据引理 知几乎必然有
$$
Y_n \to 0
\quad \Rightarrow \quad
L \left ( F^{\widetilde{\mathbf{W}}_n}, F^{\widehat{\mathbf{W}}_n} \right ) \to 0.
$$

## Step 3 - Centralization

对任意的 $n$ 以及 $1 \leq j,k \leq n$，注意到 $\mathbb{E} x_{jk}^{(n)} = 0$，因此
$$
\mathbb{E} \left [ x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| < \eta_n \sqrt{n}\right) \right ] = \mathbb{E} x_{jk}^{(n)} - \mathbb{E} \left [ x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ] \\
= - \mathbb{E} \left [ x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ].
$$
再利用 $\mathbb{E}^2[Y] \leq \mathbb{E}[Y^2]$，可以推出
$$
\begin{align*}
L^3 \left ( F^{\widehat{\mathbf{W}}_n}， F^{\widehat{\mathbf{W}}_n - \mathbb{E} \widehat{\mathbf{W}}_n} \right )
& \leq \frac{1}{n} \left \| \mathbb{E} \widehat{\mathbf{W}}_n \right \|_F^2 
= \frac{1}{n^2} \sum_{1 \leq j \not= k \leq n} \left ( \mathbb{E} \left [ x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| < \eta_n \sqrt{n}\right) \right ] \right )^2 \\
& = \frac{1}{n^2} \sum_{1 \leq j \not= k \leq n} \mathbb{E}^2 \left [ x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ] \\
& \leq \frac{1}{\eta_n^2 n^2} \sum_{j, k = 1}^n \mathbb{E} \left [ \left|x_{jk}^{(n)}\right|^2 \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ] \to 0, 
\quad n \to \infty.
\end{align*}
$$

## Step 4 - Replacing Elements with Small Variance

对 $1 \leq j \not= k \leq n$，定义
$$
\left ( \sigma_{jk}^{(n)} \right )^{2}
:=  n \operatorname{Var} \left [ \widehat{w}_{jk}^{(n)} \right ] 
= \operatorname{Var} \left [ x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| < \eta_n \sqrt{n}\right) \right ].
$$
注意到
$$
\operatorname{Var} \left [ x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| < \eta_n \sqrt{n}\right) \right ]
\leq \mathbb{E} \left [ \left|x_{j k}^{(n)}\right|^{2} \cdot \mathbb{I}\left(\left|x_{j k}^{(n)}\right| < \eta_n \sqrt{n}\right) \right ]
\leq \mathbb{E} \left|x_{j k}^{(n)}\right|^{2}
= 1,
$$
因此 $\sigma_{jk}^{(n)} \leq 1$。现考察指标集
$$
\begin{align*}
D_n & := \left \{ (j,k): 1 \leq j < k \leq n \ \text{ and } \ \left ( \sigma_{jk}^{(n)} \right )^{2} \leq \frac{1}{2} \right \}, \\
E_n & := \left \{ (j,k): 1 \leq j < k \leq n \ \text{ and } \ \left ( \sigma_{jk}^{(n)} \right )^{2} > \frac{1}{2} \right \},
\end{align*}
$$
及基数 $K: = K(n) = \operatorname{card}(D_n)$。首先，
$$
\begin{align*}
1 - \left ( \sigma_{jk}^{(n)} \right )^2 
& = \mathbb{E} \left | x_{jk} ^{(n)} \right |^2 - \mathbb{E} \left [ \left|x_{jk}^{(n)}\right|^2 \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| < \eta_n \sqrt{n}\right) \right ] + \mathbb{E}^2 \left [ x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| < \eta_n \sqrt{n}\right) \right ] \\
& = \mathbb{E} \left [ \left|x_{jk}^{(n)}\right|^2 \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ] + \mathbb{E}^2 \left [ x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ] \\
& \leq 2 \mathbb{E} \left [ \left|x_{jk}^{(n)}\right|^2 \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ].
\end{align*}
$$
由此可以推出
$$
\begin{align*}
\frac{1}{n^2} \sum_{1 \leq j < k \leq n} \left [ 1 - \left ( \sigma_{jk}^{(n)} \right )^2 \right ]
\leq \frac{2}{n^2} \sum_{1 \leq j \not= k \leq n} \mathbb{E} \left [ \left|x_{jk}^{(n)}\right|^2 \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ].
\end{align*}
$$
对定理条件取 $\eta = 1$，可知上式右端在 $n \to \infty$ 时趋于 $0$。因此，
$$
\frac{1}{n^2} \sum_{(j, k) \in D_n} \left ( \sigma_{jk}^{(n)} \right )^2
= \frac{n(n-1)}{2n^2} - \frac{1}{n^2} \sum_{1 \leq j < k \leq n} \left [ 1 - \left ( \sigma_{jk}^{(n)} \right )^2 \right ] \to \frac{1}{2}.
$$
利用 $1 \leq j < k \leq n$ 时 $\sigma_{jk}^{(n)} \leq 1$ 以及 $(j,k) \in D_n$ 时 $\sigma_{jk}^{(n)} \leq 1/2$，可以得到
$$
\begin{align*}
\sum_{1 \leq j < k \leq n} \left ( \sigma_{jk}^{(n)} \right )^2
\leq \frac{1}{2} K(n) + \left ( \frac{n(n-1)}{2} - K(n) \right ),
\end{align*}
$$
于是
$$
\frac{1}{n^2} K(n) \leq \frac{n-1}{n} - \frac{2}{n^2} \sum_{(j, k) \in D_n} \left ( \sigma_{jk}^{(n)} \right )^2 \to 0.
$$
现定义 $n$ 维 Hermite 矩阵 $\overline{\mathbf{W}}_n$，其对角线元素为零。至于对角线以上的元素，则定义
$$
\overline{w}_{jk}^{(n)} := \begin{cases}
y_{jk}^{(n)} / \sqrt{n}, & \text{ if } (j, k) \in D_n, \\
\widehat{w}_{jk}^{(n)} - \mathbb{E} \widehat{w}_{jk}^{(n)}, & \text{ if } (j, k) \in E_n,
\end{cases}
$$
这里 $y_{jk}^{(n)}$ 为新构造的随机变量，使得

+ $\mathbb{P} \left ( y_{jk}^{(n)} = 1 \right ) = \mathbb{P} \left ( y_{jk}^{(n)} = -1 \right ) = 1/2$，这意味着 $\mathbb{E} y_{jk}^{(n)} = 0$ 以及  $\operatorname{Var} \left [ y_{jk}^{(n)} \right ] = 1$。
+ 矩阵 $\overline{\mathbf{W}}_n$ 对角线之上的元素之间相互独立。

那么
$$
\begin{align*}
L^3 \left ( F^{\overline{\mathbf{W}}_n}， F^{\widehat{\mathbf{W}}_n - \mathbb{E} \widehat{\mathbf{W}}_n} \right ) 
& \leq \frac{1}{n} \left \| \overline{\mathbf{W}}_n - \widehat{\mathbf{W}}_n + \mathbb{E} \widehat{\mathbf{W}}_n \right \|_F^2 
\triangleq \frac{2}{n^2} \sum_{(j,k) \in D_n} z_{jk}^{(n)},
\end{align*}
$$
其中	
$$
z_{jk}^{(n)} : = \left | y_{jk}^{(n)} - x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| < \eta_n \sqrt{n}\right) + \mathbb{E} \left [ x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| < \eta_n \sqrt{n}\right) \right ] \right |^2.
$$
由于 $\left | y_{jk}^{(n)} \right | \leq 1 \leq \eta_n \sqrt{n}$，可以断定 $z_{jk}^{(n)} \leq 9 \eta_n^2 n$ 。另一方面，
$$
\mathbb{E} z_{jk}^{(n)} 
= \operatorname{Var} \left [ y_{jk}^{(n)} \right ] + \operatorname{Var} \left [ x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| < \eta_n \sqrt{n}\right) \right ] 
= 1 + \left ( \sigma_{jk}^{(n)} \right )^{2}
\leq 2.
$$
对固定的 $n$，考虑 $m := \lceil \ln n \rceil$，并将 $\sum_{(j,k) \in D_n} z_{jk}^{(n)}$ 重写为 $\sum_{k=1}^{K} u_{k}$，
$$
\begin{align*}
\mathbb{E} \left ( \frac{2}{n^2} \sum_{k=1}^{K} u_{k} \right )^m 
& = \frac{2^{m}}{n^{2 m}} \sum_{m_{1} + \cdots + m_{K} = m} \frac{m !}{m_{1} ! \cdots m_{K} !} \mathbb{E} u_{1}^{m_{1}} \cdots \mathbb{E} u_{K}^{m_{K}} \\
& = \frac{2^{m}}{n^{2 m}} \sum_{l=1}^m \sum_{\substack{m_{1} + \cdots + m_{l} = m \\ m_t \geq 1}} \frac{m !}{m_{1} ! \cdots m_{l} !} \sum_{1 \leq k_1 < \cdots < k_l \leq K} \mathbb{E} u_{k_1}^{m_{1}} \cdots \mathbb{E} u_{k_l}^{m_{l}}.
\end{align*}
$$

此处
$$
\mathbb{E} u_{k_1}^{m_{1}} \cdots \mathbb{E} u_{k_l}^{m_{l}} 
\leq \left ( 9 \eta_n^2 n \right )^{m - l} \mathbb{E} u_{k_1} \cdots \mathbb{E} u_{k_l}
\leq \left ( 9 \eta_n^2 n \right )^{m - l} 2^l.
$$
因此
$$
\begin{align*}
\mathbb{E} \left ( \frac{2}{n^2} \sum_{k=1}^{K} u_{k} \right )^m 
& \leq \frac{2^{m}}{n^{2 m}} \sum_{l=1}^m \left ( 9 \eta_n^2 n \right )^{m - l} 2^l {K \choose l} \sum_{m_{1} + \cdots + m_{l} = m} \frac{m !}{m_{1} ! \cdots m_{l} !} \\
& \leq \frac{2^{m}}{n^{2 m}} \sum_{l=1}^m \left ( 9 \eta_n^2 n \right )^{m - l} \frac{(2K)^l}{l!} l^m \\
& \leq \sum_{l=1}^m \left ( \frac{18 \eta_n^2 l}{n} \right )^{m-l} \left ( \frac{4 \mathrm{e} K}{n^2} \right )^{l} \leq \left ( \frac{18 \eta_n^2 m}{n} + \frac{4 \mathrm{e} K}{n^2} \right )^{m}
\end{align*}
$$
这意味着对任意的 $\varepsilon > 0$，有
$$
\mathbb{P} \left (\frac{2}{n^2} \sum_{(j,k) \in D_n} z_{jk}^{(n)} > \varepsilon \right ) \leq \left ( \frac{18 \eta_n^2 m}{\varepsilon n} + \frac{4 \mathrm{e} K}{\varepsilon n^2} \right )^{m}.
$$
按照设定，有 $m = O(\ln n)$ 以及 $K = o(n^2)$，因此上式右端括号中的项在 $n \to \infty$ 时趋于 $0$，这意味着对任意的 $t > 0$，当 $n$ 足够大时都有
$$
m \ln \left ( \frac{18 \eta_n^2 m}{\varepsilon n} + \frac{4 \mathrm{e} K}{\varepsilon n^2} \right ) \leq -tm \leq -t \ln n.
$$
特别地，取 $t = 2$，那么 $\mathbb{P} \left (\sum_{(j,k) \in D_n} 2 z_{jk}^{(n)} /n^2 > \varepsilon \right ) = o(n^{-2})$ 为可求和的。根据引理，几乎必然有
$$
\frac{2}{n^2} \sum_{(j,k) \in D_n} z_{jk}^{(n)} \to 0
\quad \Rightarrow \quad
L \left ( F^{\overline{\mathbf{W}}_n}， F^{\widehat{\mathbf{W}}_n - \mathbb{E} \widehat{\mathbf{W}}_n} \right )  \to 0.
$$

## Step 5 - Rescaling

定义 $n$ 维 Hermite 矩阵 $\mathbf{W}^\sharp_n$，其对角线元素为零。至于对角线以上的元素，则进行方差归一化，即
$$
{w}_{jk}^{\sharp (n)} :=\begin{cases}
\overline{w}_{jk}^{(n)}, & \text{ if } (j,k) \in D_n, \\
\overline{w}_{jk}^{(n)} / \sigma_{jk}^{(n)}, & \text{ if } (j,k) \in E_n,
\end{cases}
$$

注意根据 $E_n$ 的定义，对于 $(j,k) \in E_n$，有
$$
\overline{x}_{jk}^{(n)} 
: = \sqrt{n} \cdot \overline{w}_{jk}^{(n)} 
= x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| \geq \eta_n \sqrt{n}\right) -\mathbb{E} \left [ x_{jk}^{(n)} \cdot \mathbb{I}\left(\left|x_{jk}^{(n)}\right| \geq \eta_n \sqrt{n}\right) \right ].
$$
以及 $\sigma_{jk}^{(n)} = \mathbb{E} \left | \overline{x}_{jk}^{(n)} \right |^2 \in [1 / 2, 1]$。

$$
L^3 \left (F^{\mathbf{W}^{\sharp}_n} , F^{\overline{\mathbf{W}}_n} \right )
\leq \frac{1}{n} \left \| {\mathbf{W}}^{\sharp}_n - \overline{\mathbf{W}}_n \right \|_F^2 
= \frac{2}{n^2} \sum_{(j,k) \in E_n} \left ( 1 / \sigma_{jk}^{(n)} - 1 \right )^2 \left | \overline{x}_{jk}^{(n)} \right |^2 \triangleq S_n.
$$

一方面，

$$
\begin{align*}
\mathbb{E} S_n
& = \frac{2}{n^2} \sum_{(j,k) \in E_n} \left ( 1 - \sigma_{jk}^{(n)} \right )^2
\leq \frac{2}{n^2} \sum_{1 \leq j < k \leq n} \left ( 1 - \left | \sigma_{jk}^{(n)} \right |^2 \right )
\end{align*}
$$
注意 step 4 中已经证明了上式右端在 $n \to \infty$ 时趋于 $0$。另一方面，对 $(j,k) \in E_n$，记
$$
y_{jk}^{(n)} 
:= \left | \overline{x}_{jk}^{(n)} \right |^2 - \left | \sigma_{jk}^{(n)} \right |^2.
$$
那么根据引理，对任意的 $r \in \mathbb{Z}_+$，存在仅与 $r$ 有关的常数 $C_r$ 以及 $C_{2r}$ 使得
$$
\begin{align*}
\mathbb{E} \left | y_{jk}^{(n)} \right |^r 
& \leq C_r \mathbb{E} \left | \overline{x}_{jk}^{(n)} \right |^{2r} 
\leq C_r C_{2r} \mathbb{E} \left [ \left | x_{jk}^{(n)} \right |^{2r} \cdot \mathbb{I} \left( \left|x_{jk}^{(n)} \right| < \eta_n \sqrt{n} \right) \right ] \\
& \leq C_r C_{2r} \eta_n^{2r-2} n^{n-1} \mathbb{E} \left | x_{jk}^{(n)} \right |^2 = C_r C_{2r} \eta_n^{2r-2} n^{r-1}.
\end{align*}
$$
于是利用 Rosenthal 不等式，可以推出
$$
\begin{align*}
\mathbb{E} \left | S_n - \mathbb{E} S_n \right |^4
& = \mathbb{E} \left | \frac{2}{n^2} \sum_{(j,k) \in E_n} \left ( 1 / \sigma_{jk}^{(n)} - 1 \right )^2 {y}_{jk}^{(n)} \right |^4 \\
& \leq \frac{C}{n^8} \mathbb{E} \left | \sum_{(j,k) \in E_n} y_{jk}^{(n)} \right |^4
\leq \frac{C}{n^8} \left [ \sum_{(j,k) \in E_n} \mathbb{E} \left | y_{jk}^{(n)} \right |^4 + \left ( \sum_{(j,k) \in E_n} \mathbb{E} \left | y_{jk}^{(n)} \right |^2  \right )^2 \right ] \\
& \leq \frac{C}{n^8} \left  [ n^2 \cdot \eta_n^{6} n^{3} + \left ( n^2 \cdot \eta_n^{2} n \right )^2 \right ] = o(n^{-2}).
\end{align*}
$$
由此可知，对于任意 $\varepsilon > 0$，可以选取 $N_0 \in \mathbb{Z}_+$ 使得 $\mathbb{E} S_n < \varepsilon / 2$，从而当 $n \geq N_0$ 时，有
$$
\begin{align*}
\mathbb{P} \left ( S_n > \varepsilon \right ) 
& \leq \mathbb{P} \left ( S_n - \mathbb{E} S_n \geq \frac{\varepsilon}{2} \right ) 
\leq \frac{\mathbb{E} \left | S_n - \mathbb{E} S_n \right |^4}{(\varepsilon / 2)^4} 
= o(n^{-2}).
\end{align*}
$$
根据引理，这蕴含这几乎必然有
$$
S_n \to 0
\quad \Rightarrow \quad
L \left ( F^{\mathbf{W}^{\sharp}_n}, F^{\overline{\mathbf{W}}_n} \right ) \to 0.
$$

