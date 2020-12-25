---
title: Stieltjes Transform
date: 2020-12-26 00:14:22
tags: 
  - Semicircle Law
  - M-P Law
  - Stieltjes Transform
categories: Random Matrix
mathjax: true
---

[Notes] <u>Spectral analysis of large dimensional random matrices</u> by Zhidong Bai & Jack W. Silverstein.

<!--more-->

以下约定出现的复数平方根均取复部为正的分支，即
$$
\sqrt{z}=\operatorname{sgn}(\Im z) \frac{|z|+z}{\sqrt{2(|z|+\Re z)}}
$$
此时有
$$
\begin{align*}
\Re\sqrt{z} & = \frac{1}{\sqrt{2}} \operatorname{sgn}(\Im z) \sqrt{|z|+\Re z}=\frac{\Im z}{\sqrt{2(|z|-\Re z)}}, \\
\Im\sqrt{z} & = \frac{1}{\sqrt{2}} \sqrt{|z|-\Re z}=\frac{|\Im z|}{\sqrt{2(|z|+\Re z)}}.
\end{align*}
$$

## Semicircular Law

**Semicircular Law** with scale parameter $\sigma > 0$:
$$
\mu( \mathrm{d} x ) := \frac{1}{2\pi \sigma^2} \sqrt{4 \sigma^2 - x^2} \cdot \mathbb{I}_{[-2\sigma, 2\sigma]}(x) \mathrm{d} x.
$$
The Stieltjes transform for the semicircular law is given by
$$
s(z)
= - \frac{z - \sqrt{z^2 - 4 \sigma^2}}{2 \sigma^2}.
$$

### Stieltjes Transform of the Semicircular Law

> 对任意固定的 $z = u+\mathrm{i} v \in \mathbb{C}_+$，利用变换 $x = \sigma^2 \left( 1 + y + 2 \sqrt{y} \cos w \right )$ 以及 $\zeta = \mathrm{e}^{\mathrm{i} w}$，可以推出
> $$
> \begin{align*}
> s(z) 
> & = \int_{\mathbb{R}} \frac{1}{x-z} \mu(\mathrm{d} x)
> = \frac{1}{2\pi \sigma^2} \int_{-2 \sigma}^{2 \sigma} \frac{1}{x-z} \sqrt{ 4\sigma^2- x^2} \mathrm{d} x \\
> & = \frac{2}{\pi} \int_{0}^{\pi} \frac{\sin^2 w}{2\sigma \cos w -z} \mathrm{d} w
> = \frac{1}{\pi} \int_{0}^{2\pi} \frac{\left [\left ( \mathrm{e}^{ \mathrm{i} w} - \mathrm{e}^{- \mathrm{i} w} \right ) / 2 \mathrm{i} \right ]^2}{ \sigma \left ( \mathrm{e}^{ \mathrm{i} w} + \mathrm{e}^{- \mathrm{i} w} \right ) -z} \mathrm{d} w \\
> & = - \frac{1}{4 \pi \mathrm{i}} \int_{| \zeta | = 1} \frac{\left ( \zeta^2 - 1 \right )^2}{\zeta^2 \left [ \sigma \left ( \zeta^2 + 1 \right ) - z \zeta \right ]} \mathrm{d} \zeta
> \triangleq - \frac{1}{4 \pi \mathrm{i}} \int_{| \zeta | = 1} f(\zeta) \mathrm{d} \zeta.
> \end{align*}
> $$
> 考察 $f$ 的 $3$ 个极点：
>
> + $\zeta_0 = 0$，阶数为 $2$。计算可得 $f$ 在 $\zeta_0$ 处的留数为
>     $$
>     \begin{align*}
>     \operatorname{Res}_{\zeta_0} f 
>     & = \lim_{\zeta \to \zeta_0} \frac{\mathrm{d}}{\mathrm{d} \zeta} \left [ (\zeta - \zeta_0)^2 f(\zeta) \right ] \\
>     & = \lim_{\zeta \to \zeta_0} \frac{\left ( \zeta^2 - 1 \right ) \left ( 2 \sigma \zeta^3 - 3z \zeta^2 + 2 \sigma \zeta -z \right )}{\left [ \sigma \left ( \zeta^2 + 1 \right ) - z \zeta \right ]^2}
>     = \frac{z}{\sigma^2} .
>     \end{align*}
>     $$
> + 求解方程
>     $$
>     \sigma \left ( \zeta^2 + 1 \right ) - z \zeta = 0
>     $$
>     得到 $f$ 的另外两个阶数均为 $1$ 的极点
>     $$
>     \zeta_1 = \frac{z + \sqrt{z^2 - 4 \sigma^2}}{2 \sigma}
>     \quad \text{ and } \quad
>     \zeta_2 = \frac{z - \sqrt{z^2 - 4 \sigma^2}}{2 \sigma}.
>     $$
>     注意到 $\zeta_1 \zeta_2 = 1$，可计算出 $f$ 在这两个极点处的留数为
>     $$
>     \begin{align*}
>     \operatorname{Res}_{\zeta_1} f 
>     & = \lim_{\zeta \to \zeta_1} (\zeta - \zeta_1) f(\zeta) 
>     = \frac{\left ( \zeta_1^2 - 1 \right )^2}{\zeta_1^2 \cdot \sigma \left (\zeta_1 - \zeta_2 \right)} 
>     = \frac{\sqrt{z^2 - 4 \sigma^2}}{\sigma^2}, \\
>     \operatorname{Res}_{\zeta_2} f 
>     & = \lim_{\zeta \to \zeta_2} (\zeta - \zeta_2) f(\zeta) 
>     = \frac{\left ( \zeta_2^2 - 1 \right )^2}{\zeta_2^2 \cdot \sigma \left (\zeta_2 - \zeta_1 \right)} 
>     = - \frac{\sqrt{z^2 - 4 \sigma^2}}{\sigma^2}.
>     \end{align*}
>     $$
>
> 考察判定式 $\Delta = z^2 - 4 \sigma^2$。首先 $\Im \sqrt{\Delta}$ 与 $\Im z = v$ 都是非负的，另一方面，
> $$
> \Re \sqrt{\Delta} = \frac{\Im \Delta}{\sqrt{2 \left ( |\Delta| - \Re \Delta \right )}} 
> = \frac{2uv}{\sqrt{2 \left ( |\Delta| - \Re \Delta \right )}} 
> = \frac{2v \cdot \Re z}{\sqrt{2 \left ( |\Delta| - \Re \Delta \right )}},
> $$
> 因此 $\Re \sqrt{\Delta}$ 也与 $\Re z$ 符号一致。由于 $|\zeta_1| \cdot |\zeta_2| = 1$，这意味着 $|\zeta_1| > 1$ 而 $| \zeta_2 | < 1$。综上，有
> $$
> s(z)
> = - \frac{1}{4 \pi \mathrm{i}} \int_{| \zeta | = 1} f(\zeta) \mathrm{d} \zeta 
> = - \frac{1}{2} \left ( \operatorname{Res}_{\zeta_0} f + \operatorname{Res}_{\zeta_2} f \right )
> = - \frac{z - \sqrt{z^2 - 4 \sigma^2}}{2 \sigma^2}.
> $$

## Marčenko–Pastur Law

**M-P Law** with scale parameter $\sigma > 0$ and ratio parameter $y > 0$:
$$
\mu( \mathrm{d} x ) := \frac{1}{2\pi xy \sigma^2} \sqrt{(b-x)(x-a)} \cdot \mathbb{I}_{[a, b]}(x) \mathrm{d} x + \left( 1 - \frac{1}{y} \right)^+ \delta_0.
$$
where $a = \sigma^2 \left (1 - \sqrt{y} \right)^2$ and $b = \sigma^2 \left (1 + \sqrt{y} \right)^2$.

The Stieltjes transform for the M-P law is given by
$$
s(z) = \frac{\sigma^2(1-y) - z +  \sqrt{\sigma^{4}(1-y)^{2}-2 \sigma^{2}(1+y) z+z^{2}}}{2 \sigma^{2} yz}.
$$

### Verification of M-P law as a Distribution

> 如果 $y = 1$，那么 $a = 0$ 以及 $b = 4 \sigma^2$。利用变换 $x = 4 \sigma^2 \sin^2 w$，可以推出
> $$
> \int_{\mathbb{R}} \mu(\mathrm{d} x)
> = \int_{0}^{4\sigma^2} \frac{1}{2\pi x \sigma^2} \sqrt{ x\left (4\sigma^2-x \right)} \mathrm{d} x
> = \frac{4}{\pi} \int_{0}^{\pi/2} \cos^2 w \mathrm{d} w 
> = 1.
> $$
> 现考虑 $y \not = 1$ 的情形。利用变换 $x = \sigma^2 \left( 1 + y + 2 \sqrt{y} \cos w \right )$ 以及 $\zeta = \mathrm{e}^{\mathrm{i} w}$，可以推出
> $$
> \begin{align*}
> \int_{\mathbb{R}} \mu(\mathrm{d} x)
> & = \int_{a}^{b} \frac{1}{2\pi xy \sigma^2} \sqrt{(b-x)(x-a)} \mathrm{d} x \\
> & = \frac{2}{\pi} \int_{0}^{\pi} \frac{\sin^2 w}{1 + y + 2\sqrt{y} \cos w} \mathrm{d} w 
> = \frac{1}{\pi} \int_{0}^{2 \pi} \frac{\left [\left ( \mathrm{e}^{ \mathrm{i} w} - \mathrm{e}^{- \mathrm{i} w} \right ) / 2 \mathrm{i} \right ]^2}{1 + y + \sqrt{y} \left ( \mathrm{e}^{ \mathrm{i} w} + \mathrm{e}^{- \mathrm{i} w} \right )} \mathrm{d} w \\
> & = - \frac{1}{4 \pi \mathrm{i}} \int_{| \zeta | = 1} \frac{\left ( \zeta^2 - 1 \right )^2}{\zeta^2 \left [ (1+ y) \zeta + \sqrt{y} \left ( \zeta^2 + 1 \right ) \right ]} \mathrm{d} \zeta \triangleq - \frac{1}{4 \pi \mathrm{i}} \int_{| \zeta | = 1} f(\zeta) \mathrm{d} \zeta.
> \end{align*}
> $$
> 考察 $f$ 的 $3$ 个极点：
>
> + $\zeta_0 = 0$，阶数为 $2$。计算可得 $f$ 在 $\zeta_0$ 处的留数为
>     $$
>     \begin{align*}
>     \operatorname{Res}_{\zeta_0} f 
>     & = \lim_{\zeta \to \zeta_0} \frac{\mathrm{d}}{\mathrm{d} \zeta} \left [ (\zeta - \zeta_0)^2 f(\zeta) \right ] \\
>     & = \lim_{\zeta \to \zeta_0} \frac{\left ( \zeta^2 - 1 \right ) \left [ 2 \sqrt{y} \zeta^3 + 3(1+y) \zeta^2 + 6\sqrt{y} \zeta + (1+y) \right ]}{\left [ (1+ y) \zeta + \sqrt{y} \left ( \zeta^2 + 1 \right ) \right ]^2}
>     = - 1 - \frac{1}{y} .
>     \end{align*}
>     $$
> + 求解方程
>     $$
>     (1+ y) \zeta + \sqrt{y} \left ( \zeta^2 + 1 \right )  = 0,
>     $$
>     即得 $f$ 的另外两个极点 $\zeta_1 = - \sqrt{y}$ 及 $\zeta_2 = - 1/ \sqrt{y}$，其阶数均为 $1$。计算可得 $f$ 在这两个极点处的留数为
>     $$
>     \begin{align*}
>     \operatorname{Res}_{\zeta_1} f 
>     & = \lim_{\zeta \to \zeta_1} (\zeta - \zeta_1) f(\zeta) 
>     = \frac{\left ( \zeta_1^2 - 1 \right )^2}{\sqrt{y} \zeta_1^2 \left (\zeta_1 - \zeta_2 \right)} 
>     = \frac{1}{y} - 1, \\
>     \operatorname{Res}_{\zeta_2} f 
>     & = \lim_{\zeta \to \zeta_2} (\zeta - \zeta_2) f(\zeta) 
>     = \frac{\left ( \zeta_2^2 - 1 \right )^2}{\sqrt{y} \zeta_2^2 \left (\zeta_2 - \zeta_1 \right)} 
>     = 1 - \frac{1}{y}.
>     \end{align*}
>     $$
>
> 对于 $y \in (0, 1)$ 的情形，有 $|\zeta_1| < 1$ 而 $|\zeta_2| > 1$，因此由留数公式
> $$
> \int_{\mathbb{R}} \mu(\mathrm{d} x) = - \frac{1}{4 \pi \mathrm{i}} \int_{| \zeta | = 1} f(\zeta) \mathrm{d} \zeta = - \frac{1}{2} \left ( \operatorname{Res}_{\zeta_0} f + \operatorname{Res}_{\zeta_1} f  \right ) 
> = 1.
> $$
> 最后，如果 $y \in (1, \infty)$，那么 $|\zeta_1| > 1$ 而 $|\zeta_2| < 1$，因此
> $$
> \int_{\mathbb{R}} \mu(\mathrm{d} x)
> = - \frac{1}{4 \pi \mathrm{i}} \int_{| \zeta | = 1} f(\zeta) \mathrm{d} \zeta + \left( 1 - \frac{1}{y} \right)
> = - \frac{1}{2} \left ( \operatorname{Res}_{\zeta_0} f + \operatorname{Res}_{\zeta_2} f  \right )  + \left( 1 - \frac{1}{y} \right) = 1.
> $$

### Stieltjes Transform of the M-P Law

> 先考虑 $y \not = 1$ 的情形。对任意固定的 $z = u+\mathrm{i} v \in \mathbb{C}_+$，利用变换 $x = \sigma^2 \left( 1 + y + 2 \sqrt{y} \cos w \right )$ 以及 $\zeta = \mathrm{e}^{\mathrm{i} w}$，可以推出
> $$
> \begin{align*}
> s(z) 
> & = \int_{\mathbb{R}} \frac{1}{x-z} \mu(\mathrm{d} x)
> = \int_{a}^{b} \frac{1}{x-z} \frac{1}{2\pi xy \sigma^2} \sqrt{(b-x)(x-a)} \mathrm{d} x \\
> & = \frac{2}{\pi} \int_{0}^{\pi} \frac{\sin^2 w}{\left (1 + y + 2\sqrt{y} \cos w \right ) \left [ \sigma^2 \left (1 + y + 2\sqrt{y} \cos w \right ) - z \right ]} \mathrm{d} w \\
> & = \frac{1}{\pi} \int_{0}^{2 \pi} \frac{\left [\left ( \mathrm{e}^{ \mathrm{i} w} - \mathrm{e}^{- \mathrm{i} w} \right ) / 2 \mathrm{i} \right ]^2}{\left (1 + y + 2\sqrt{y} \left ( \mathrm{e}^{ \mathrm{i} w} - \mathrm{e}^{- \mathrm{i} w} \right ) \right ) \left [ \sigma^2 \left (1 + y + 2\sqrt{y} \left ( \mathrm{e}^{ \mathrm{i} w} - \mathrm{e}^{- \mathrm{i} w} \right ) \right ) - z \right ]} \mathrm{d} w \\
> & = - \frac{1}{4 \pi \mathrm{i}} \int_{| \zeta | = 1} \frac{\left ( \zeta^2 - 1 \right )^2}{\zeta \left [ (1+ y) \zeta + \sqrt{y} \left ( \zeta^2 + 1 \right ) \right ] \left [ \sigma^2 (1+ y) \zeta + \sigma^2 \sqrt{y} \left ( \zeta^2 + 1 \right ) - z\zeta \right ]} \mathrm{d} \zeta \\ 
> & \triangleq - \frac{1}{4 \pi \mathrm{i}} \int_{| \zeta | = 1} f(\zeta) \mathrm{d} \zeta.
> \end{align*}
> $$
> 易知 $f$ 具有 $5$ 个极点：
>
> + $\zeta_0 = 0$，阶数为 $1$。计算可得 $f$ 在 $\zeta_0$ 处的留数为
>     $$
>     \operatorname{Res}_{\zeta_0} f 
>     = \lim_{\zeta \to \zeta_0} (\zeta - \zeta_0) f(\zeta) 
>     = \frac{1}{\sigma^2 y}.
>     $$
> + 求解方程
>     $$
>     (1+ y) \zeta + \sqrt{y} \left ( \zeta^2 + 1 \right )  = 0,
>     $$
>     得到 $f$ 的另外两个阶数均为 $1$ 的极点 $\zeta_1 = - \sqrt{y}$ 及 $\zeta_2 = - 1/ \sqrt{y}$。利用上述方程以及 $\zeta_1 \zeta_2 = 1$，可得出 $f$ 在这两个极点处的留数为
>     $$
>     \begin{align*}
>     \operatorname{Res}_{\zeta_1} f 
>     & = \lim_{\zeta \to \zeta_1} (\zeta - \zeta_1) f(\zeta) 
>     = \frac{\left ( \zeta_1^2 - 1 \right )^2}{\zeta_1 \cdot \sqrt{y} \left (\zeta_1 - \zeta_2 \right) \cdot (- z \zeta_1)} 
>     = \frac{y-1}{yz}, \\
>     \operatorname{Res}_{\zeta_2} f 
>     & = \lim_{\zeta \to \zeta_2} (\zeta - \zeta_2) f(\zeta) 
>     = \frac{\left ( \zeta_2^2 - 1 \right )^2}{\zeta_2 \cdot \sqrt{y} \left (\zeta_2 - \zeta_1 \right) \cdot (-z \zeta_2)} 
>     = \frac{1-y}{yz}.
>     \end{align*}
>     $$
> + 求解方程
>     $$
>     \sigma^2 \left [(1+ y) \zeta + \sqrt{y} \left ( \zeta^2 + 1 \right ) \right ] - z\zeta  = 0,
>     $$
>     即得 $f$ 的另外两个阶数均为 $1$ 的极点
>     $$
>     \begin{align*}
>     \zeta_{3} & = \frac{-\sigma^{2}(1+y)+z+\sqrt{\sigma^{4}(1-y)^{2}-2 \sigma^{2}(1+y) z+z^{2}}}{2 \sigma^{2} \sqrt{y}}, \\
>     \zeta_{4} & = \frac{-\sigma^{2}(1+y)+z-\sqrt{\sigma^{4}(1-y)^{2}-2 \sigma^{2}(1+y) z+z^{2}}}{2 \sigma^{2} \sqrt{y}} .
>     \end{align*}
>     $$
>     利用上述方程以及 $\zeta_3 \zeta_4 = 1$，可得出 $f$ 在这两个极点处的留数为
>     $$
>     \begin{align*}
>     \operatorname{Res}_{\zeta_3} f 
>     & = \lim_{\zeta \to \zeta_3} (\zeta - \zeta_3) f(\zeta) 
>     = \frac{\left ( \zeta_3^2 - 1 \right )^2}{\zeta_3 \cdot (z \zeta_3 / \sigma^{2}) \cdot \sigma^2 \sqrt{y} \left (\zeta_3 - \zeta_4 \right)} \\
>     & = \frac{\zeta_3 - \zeta_4}{\sqrt{y} z} = \frac{\sqrt{\sigma^{4}(1-y)^{2}-2 \sigma^{2}(1+y) z+z^{2}}}{\sigma^{2} yz}, \\
>     \operatorname{Res}_{\zeta_4} f 
>     & = \lim_{\zeta \to \zeta_4} (\zeta - \zeta_4) f(\zeta) 
>     = \frac{\left ( \zeta_4^2 - 1 \right )^2}{\zeta_4 \cdot (z \zeta_3 / \sigma^{2}) \cdot \sigma^2 \sqrt{y} \left (\zeta_4 - \zeta_3 \right)} \\
>     & = \frac{\zeta_4 - \zeta_3}{\sqrt{y} z} = - \frac{\sqrt{\sigma^{4}(1-y)^{2}-2 \sigma^{2}(1+y) z+z^{2}}}{\sigma^{2} yz}.
>     \end{align*}
>     $$
>
> 对于 $\zeta_3$ 与 $\zeta_4$，考察判定式
> $$
> \Delta = \sigma^{4}(1-y)^{2}-2 \sigma^{2}(1+y) z+z^{2}.
> $$
> 首先 $\Im \sqrt{\Delta}$与 $\Im [ - \sigma^{2}(1+y) + z ] = v$ 都为非负的。另一方面，由于
> $$
> \Re \sqrt{\Delta} = \frac{\Im \Delta}{\sqrt{2 \left ( |\Delta| - \Re \Delta \right )}} 
> = \frac{2v \left [ u - \sigma^{2}(1+y) \right ]}{\sqrt{2 \left ( |\Delta| - \Re \Delta \right )}} 
> = \frac{2v \cdot \Re [ - \sigma^{2}(1+y) + z ]}{\sqrt{2 \left ( |\Delta| - \Re \Delta \right )}},
> $$
> 因此 $\Re \sqrt{\Delta}$ 也与 $\Re [ - \sigma^{2}(1+y) + z ]$ 符号一致。由于 $|\zeta_3| \cdot |\zeta_4| = 1$，这意味着 $|\zeta_3| > 1$ 而 $| \zeta_4 | < 1$。
>
> 对于 $y \in (0,1)$ 的情形，注意到 $|\zeta_1| < 1$ 而 $|\zeta_2| > 1$。因此
> $$
> \begin{align*} 
> s(z)
> & = - \frac{1}{4 \pi \mathrm{i}} \int_{| \zeta | = 1} f(\zeta) \mathrm{d} \zeta = - \frac{1}{2} \left ( \operatorname{Res}_{\zeta_0} f + \operatorname{Res}_{\zeta_1} f + \operatorname{Res}_{\zeta_4} f \right ) \\
> & = \frac{\sigma^2(1-y) - z +  \sqrt{\sigma^{4}(1-y)^{2}-2 \sigma^{2}(1+y) z+z^{2}}}{2 \sigma^{2} yz}.
> \end{align*}
> $$
> 至于 $y \in (1, \infty)$ 的情形，此时 $|\zeta_1| > 1$ 而 $|\zeta_2| < 1$，因此仍旧有
> $$
> \begin{align*} 
> s(z)
> & = - \frac{1}{4 \pi \mathrm{i}} \int_{| \zeta | = 1} f(\zeta) \mathrm{d} \zeta - \frac{1}{z} \left( 1 - \frac{1}{y} \right) = - \frac{1}{2} \left ( \operatorname{Res}_{\zeta_0} f + \operatorname{Res}_{\zeta_2} f + \operatorname{Res}_{\zeta_4} f \right ) - \frac{y - 1}{yz} \\
> & = \frac{\sigma^2(1-y) - z +  \sqrt{\sigma^{4}(1-y)^{2}-2 \sigma^{2}(1+y) z+z^{2}}}{2 \sigma^{2} yz}.
> \end{align*}
> $$
>
> 最后，对于 $y = 1$，由 $s(z)$ 关于 $y$ 的连续性可得：这是由于 $f$ 关于 $y \in (0, \infty)$ 是连续的，并且
> $$
> s(z) = - \frac{1}{4 \pi \mathrm{i}} \int_{| \zeta | = 1} f(\zeta) \mathrm{d} \zeta - \frac{1}{z} \left( 1 - \frac{1}{y} \right)^+.
> $$
