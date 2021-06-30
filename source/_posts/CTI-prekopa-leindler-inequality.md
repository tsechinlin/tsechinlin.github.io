---
title: Prekopa-Leindler Inequality
date: 2021-04-30 15:06:05
tags: 
  - Convex Functions
categories: Concentration Inequalities
mathjax: true
---

Prekopa-Leindler Inequality

<!--more-->

## Brunn-Minkowski Ineuqality (One-dimensional)

Let $A, B, C$ be nonempty measurable sets in $\mathbb{R}$ with $A + B \subset C$. Then
$$
\mu_1 (C) \geq \mu_1 (A) + \mu_1 (B).
$$

> **[Part 1]** When $\mu_1 (A) = \infty$ or $\mu_1 (B) = \infty$, the inequality holds trivially with $\mu_1 (C) = \infty$.
>
> For example, consider the case where $\mu_1 (A) = \infty$.
>
> Since $B$ is nonempty, we can let $b \in B$. It follows that $A + b \subset A + B \subset C$ and
> $$
> \mu_1 (C) \geq \mu_1 (A + b) = \mu_1 (A) = \infty.
> $$
> **[Part 2]** Now assume that $\mu_1 (A) < \infty$ and $\mu_1 (B) < \infty$.
>
> For any $\varepsilon > 0$, by inner regularity of $\mu_1$, there exist compact sets $A^\prime \subset A$ and $B^\prime \subset B$ with
> $$
> \mu_1 (A^\prime \backslash A) < \varepsilon
> \quad \text{ and } \quad
> \mu_1 (B^\prime \backslash B) < \varepsilon.
> $$
> By compactness of $A^\prime$ and $B^\prime$, we can let
> $$
> a := \sup A^\prime \in A^\prime\quad \text{ and } \quad
> b := \inf B^\prime \in B^\prime.
> $$
> In this case, we have both $A^\prime + b \subset C$ and $a + B^\prime \subset C$.
>
> On the other hand, for any $x \in A^\prime$ and $y \in B^\prime$, we have $x + b \leq a + y$, where the equality holds if and only if $x = a$ and $y = b$. In other words,
> $$
> (A^\prime + b) \cap (a + B^\prime) = \{ a + b \}.
> $$
> Therefore, we can conclude that
> $$
> \mu_1 (C) 
> \geq \mu_1 (A^\prime + b) + \mu_1 (a + B^\prime) 
> = \mu_1 (A^\prime) + \mu_1 (B^\prime)
> \geq \mu_1 (A) + \mu_1 (B) - 2 \varepsilon.
> $$
> The proof is completed by letting $\varepsilon \to 0$.

## $p$-Average

Fix $\lambda \in (0, 1)$. For each $p \in [-\infty, + \infty]$, let the function $M_p^\lambda : \mathbb{R}_+ \times \mathbb{R}_+ \to \mathbb{R}_+$ be defined as following.

+ For $x, y \in \mathbb{R}_+$ with $xy > 0$, set
    $$
    M_p^\lambda (x , y) = 
    \begin{cases}
    \left(\lambda x^{p}+(1-\lambda) y^{p}\right)^{1 / p}, & \text{ if } p \in (-\infty, 0) \cup (0, \infty), \\
    x^\lambda y^{1 - \lambda}, & \text{ if } p = 0, \\
    x \wedge y, & \text{ if } p = -\infty, \\
    x \vee y, & \text{ if } p = +\infty.
    \end{cases}
    $$

+ For $x, y \in \mathbb{R}_+$ with $xy = 0$, set
    $$
    M_p^\lambda (x , y) = 0.
    $$

**[Fact 1]** For each $p \in [-\infty, + \infty]$, the function $M_p^\lambda$ is continuous on $(0, \infty) \times (0, \infty)$.

**[Fact 2]** For each $p \in [-\infty, + \infty]$, and any $x_1, x_2, y_1, y_2 \in \mathbb{R}_+$ with $x_1 \geq x_2$ and $y_1 \geq y_2$,
$$
M_p^\lambda (x_1, y_1) \geq M_p^\lambda (x_2, y_2).
$$
**[Fact 3]** For any $x, y \in \mathbb{R}_+$,
$$
\lim_{p \to 0} M_p^\lambda (x, y) = x^\lambda y^{1 - \lambda} = M_0^\lambda (x, y).
$$

> It suffices to consider the case where $x, y$ are all positive. In this case, note that we have
> $$
> \lim_{p \to 0} \ln M_p^\lambda (x , y) 
> = \lim_{p \to 0} \frac{1}{p} \ln \left(\lambda x^{p}+(1-\lambda) y^{p}\right)
> = \lim_{p \to 0} \frac{\lambda x^{p} \ln x +(1-\lambda) y^{p} \ln y}{\lambda x^{p}+(1-\lambda) y^{p}}
> = \lambda \ln x +(1-\lambda) \ln y.
> $$

**[Fact 4]** For any $x, y \in \mathbb{R}_+$, and $p, q \in [-\infty, + \infty]$ with $p < q$, we have
$$
M_p^\lambda (x, y) \leq M_q^\lambda (x, y).
$$

> It suffices to consider the case where $x, y$ are all positive.
>
> + If $0 < p < q < +\infty$, then $\varphi(t) = t^q$ is increasing for $t > 0$. By
>     $$
>     \left [ M_p^\lambda (x, y) \right ]^p
>     = \lambda x^{p}+(1-\lambda) y^{p}
>     \leq (x \vee y)^q
>     = \left [ M_{\infty}^\lambda (x, y) \right ]^q
>     $$
>     we can obtain $M_p^\lambda (x, y) \leq M_{\infty}^\lambda (x, y)$.
>
> + If $0 < p < q < +\infty$, then $q/p > 1$. By Jensen's inequality, we have
>     $$
>     \begin{align*}
>     \left [ M_q^\lambda (x, y) \right ]^q 
>     & = \lambda x^{q}+(1-\lambda) y^{q}
>     = \lambda (x^{p})^{q/p} +(1-\lambda) (y^{p})^{q/p} \\
>     & \geq [\lambda x^{p}+(1-\lambda) y^{p}]^{q/p}
>     = \left [ M_p^\lambda (x, y) \right ]^q.
>     \end{align*}
>     $$
>     The result follows by noting that $\varphi(t) = t^q$ is increasing for $t > 0$.
>
> + If $-\infty < p < q < 0$, then $p/q > 1$. Similarly, by Jensen's inequality, we have
>     $$
>     \left [ M_p^\lambda (x, y) \right ]^p \geq \left [ M_q^\lambda (x, y) \right ]^p.
>     $$
>     The result follows by noting that $\varphi(t) = t^p$ is decreasing for $t > 0$.
>
> + If $-\infty = p < q < 0$, then $\varphi(t) = t^p$ is decreasing for $t > 0$. By
>     $$
>     \left [ M_q^\lambda (x, y) \right ]^q 
>     = \lambda x^{q}+(1-\lambda) y^{q}
>     \leq (x \wedge y)^q
>     = \left [ M_{-\infty}^\lambda (x, y) \right ]^q
>     $$
>     we can obtain $M_q^\lambda (x, y) \geq M_{-\infty}^\lambda (x, y)$.

**[Fact 5]** For any $x_1, x_2, y_1, y_2 \in \mathbb{R}_+$, and $p, q, r \in (0, \infty)$ with $1/p + 1/q = 1/r$, we have
$$
M_r^\lambda (x_1 x_2, y_1 y_2) \leq M_p^\lambda (x_1, y_1) \cdot M_q^\lambda (x_2 , y_2).
$$

> It suffices to consider the case where $x_1, x_2, y_1, y_2$ are all positive.
>
> Since $1/(p/r) + 1/(q/r) = 1$, the inequality can be deduced from Hölder's inequality,
> $$
> \begin{align*}
> \left [ M_p^\lambda (x_1, y_1) \cdot M_q^\lambda (x_2 , y_2) \right ]^r
> & = \left ( \lambda x_1^p + (1-\lambda) y_1^p \right )^{r / p} \left ( \lambda x_2^q + (1-\lambda) y_1^q \right )^{r / q} \\
> & \geq \lambda x_1^{r} x_2^{r} +(1-\lambda) y_1^{r} y_2^{r} 
> = \left [ M_r^\lambda (x_1 x_2, y_1 y_2) \right ]^r.
> \end{align*}
> $$

**[Fact 6]** For any $x_1, x_2, y_1, y_2 \in \mathbb{R}_+$, and $p \in [0, \infty)$, we have
$$
M_p^\lambda (x_1 x_2, y_1 y_2) \geq M_p^\lambda (x_1, y_1) \cdot M_{-\infty}^\lambda (x_2 , y_2).
$$

> It suffices to consider the case where $x_1, x_2, y_1, y_2$ are all positive.
>
> + If $p = 0$, then
>     $$
>     \begin{align*}
>     M_0^\lambda (x_1 x_2, y_1 y_2) 
>     & = (x_1 x_2)^\lambda (y_1 y_2)^{1 - \lambda}
>     = x_1^\lambda y_1^{1 - \lambda} \cdot x_2^\lambda y_2^{1 - \lambda} \\
>     & = M_0^\lambda (x_1, y_1) \cdot M_0^\lambda (x_2, y_2)
>     \geq M_0^\lambda (x_1, y_1) \cdot M_{-\infty}^\lambda (x_2, y_2).
>     \end{align*}
>     $$
>
> + If $p \in (0, \infty)$, then
>     $$
>     \begin{align*}
>     M_p^\lambda (x_1 x_2, y_1 y_2) 
>     & = \left ( \lambda (x_1 x_2)^p + (1 - \lambda) (y_1 y_2)^p \right )^{1/p} \\
>     & \geq \left ( \lambda x_1^p (x_2 \wedge y_2)^p + (1 - \lambda) y_1^p (x_2 \wedge y_2)^p \right )^{1/p} \\
>     & = \left ( \lambda x_1^p + (1 - \lambda) y_1^p \right )^{1/p} \cdot (x_2 \wedge y_2)
>     = M_p^\lambda (x_1, y_1) \cdot M_{-\infty}^\lambda (x_2, y_2).
>     \end{align*}
>     $$

## Prékopa-Leindler Inequality (One-dimensional)

Fix $\lambda \in (0, 1)$, and let $f, g : \mathbb{R} \to \mathbb{R}_+$ and $h: \mathbb{R} \to [0, \infty]$ be nonnegative measurable functions with $f, g \in L^{1} (\mathbb{R})$.

### Prékopa-Leindler Inequality for $p = -\infty$

Let $p = -\infty$. Assume that $\| f \|_{\infty} = \| g \|_{\infty} = 1$, and for every $x, y \in \mathbb{R}$,
$$
h(\lambda x + (1-\lambda) y) \geq M_{-\infty}^{\lambda}(f(x), g(y)) = f(x) \wedge g(y) .
$$
Then,
$$
\| h \|_1 \geq M_{1}^{\lambda}(\| f \|_1, \| g \|_1) = \lambda \| f \|_1 + (1 - \lambda) \| g \|_1.
$$

> For each $t > 0$, denote
> $$
> A_t := \{ f > t \}, \quad
> B_t := \{ g > t \} \quad \text{ and } \quad
> D_t := \{ h > t \}.
> $$
> Note that all the sets $A_t, B_t$ and $D_t$ are measurable. We claim that
> $$
> \mu_1 (D_t) \geq \lambda \mu_1 (A_t) + (1 -\lambda) \mu_1 (B_t),
> \quad \text{ for all } t > 0.
> $$
>
> + If $t \in (0,1)$, then both $A_t$ and $B_t$ are nonempty.
>
>     Note that for $x \in A_t$ and $y \in B_t$, we have
>     $$
>     h(\lambda x + (1-\lambda) y) 
>     \geq f(x) \wedge g(y)
>     > t.
>     $$
>     In other words, $\lambda A_t + (1 - \lambda) B_t \subset D_t$. 
>
>     Hence, the inequality can be deduced from Brunn-Minkowski inequality.
>
> + If $t \in [1, \infty)$, then $\mu_1 (A_t) = \mu_1 (B_t) = 0$, and the inequality holds trivially.
>
> Now, the result follows from
> $$
> \begin{align*}
> \| h \|_1 
> & = \int_{0}^{\infty} \mu_1 (D_t) \mathrm{d} t 
> \geq \int_{0}^{\infty}  [ \lambda \mu_1 (A_t) + (1 -\lambda) \mu_1 (B_t)  ] \mathrm{d} t \\
> & \geq \lambda \int_{0}^{\infty} \mu_1 (A_t) \mathrm{d} t + (1 -\lambda) \int_{0}^{\infty} \mu_1 (B_t) \mathrm{d} t
> = \lambda \| f \|_1 + (1 - \lambda) \| g \|_1.
> \end{align*}
> $$

### Prékopa-Leindler Inequality for $p \in [0, \infty)$

Let $p \in [0, \infty)$. Assume that for every $x, y \in \mathbb{R}$,
$$
h(\lambda x + (1-\lambda) y) \geq M_{p}^{\lambda}(f(x), g(y)).
$$
Then,
$$
\| h \|_1 \geq M_{p / (p + 1)}^{\lambda}(\| f \|_1, \| g \|_1).
$$

> **[Part 1]** Firstly consider the case where $f, g \in L^{\infty} (\mathbb{R})$. In this case, we can assume that $\| f \|_{\infty} > 0$ and $\| g \|_{\infty} > 0$.
>
> Let $F := f / \| f \|_{\infty}$ and $G := g / \| g \|_{\infty}$. Then for any $x, y \in \mathbb{R}$, we have
> $$
> \begin{align*}
> h(\lambda x + (1-\lambda) y) 
> & \geq M_{p}^{\lambda}(f(x), g(y))
> = M_{p}^{\lambda}  ( \| f \|_{\infty} F(x), \| g \|_{\infty} G(y)  ) \\
> & \geq M_{p}^{\lambda}  ( \| f \|_{\infty}, \| g \|_{\infty}  ) \cdot M_{-\infty}^{\lambda} ( F(x), G(y) ).
> \end{align*}
> $$
>
> In other words, if we let $H := h / M_{p}^{\lambda}  ( \| f \|_{\infty}, \| g \|_{\infty}  )$, then
> $$
> H(\lambda x + (1-\lambda) y) \geq M_{-\infty}^{\lambda} ( F(x), G(y) ),
> \quad \text{ for all } x, y \in \mathbb{R}.
> $$
> Applying Prékopa-Leindler inequality for $p = -\infty$, we can obtain
> $$
> \| h \|_1 
> = M_{p}^{\lambda} ( \| f \|_{\infty}, \| g \|_{\infty} ) \cdot \| H \|_1
> \geq M_{p}^{\lambda} ( \| f \|_{\infty}, \| g \|_{\infty} ) \cdot M_{1}^{\lambda} ( \| F \|_1, \| G \|_1 ) \\
> \geq M_{p/(1+p)}^{\lambda} ( \| f \|_{\infty} \| F \|_1, \| g \|_{\infty} \| G \|_1 )
> = M_{p/(1+p)}^{\lambda}  ( \| f \|_1, \| g \|_{1} ).
> $$
>
> **[Part 2]** For general $f, g \in L^{1} (\mathbb{R})$, define $f_N := f \wedge N$ and $g_N := g \wedge N$ for $N \geq 1$.
>
> Now, $f_N, g_N \in L^{\infty} (\mathbb{R})$. On the other hand, since $f \geq f_N, g \geq g_N$, we have
> $$
> h(\lambda x + (1-\lambda) y)
> \geq M_{p}^{\lambda}(f(x), g(y))
> \geq M_{p}^{\lambda}(f_N (x), g_N (y)),
> \quad \text{ for any } x, y \in \mathbb{R}.
> $$
> Applying the result of part 1, we obtain
> $$
> \| h \|_1 \geq M_{p/(1+p)}^{\lambda}(\| f_N \|_1, \| g_N \|_1),
> \quad \text{ for all } N \geq 1.
> $$
> Letting $N \to \infty$, by $\| f_N \|_1 \uparrow \| f \|_1$ and $\| g_N \|_1 \uparrow \| g \|_1$ we can conclude that
>
> $$
> \| h \|_1 \geq \lim_{N \to \infty} M_{p/(1+p)}^{\lambda}(\| f_N \|_1, \| g_N \|_1) 
> = M_{p/(1+p)}^{\lambda}(\| f \|_1, \| g \|_1).
> $$

## Prékopa-Leindler inequality (Multi-dimensional)

Fix $\lambda \in (0, 1)$, and let $f, g: \mathbb{R}^n \to \mathbb{R}_+$ and $h: \mathbb{R}^n \to [0, \infty]$ be nonnegative measurable functions with $f, g \in L^{1} (\mathbb{R}^n)$.

### Prékopa-Leindler Inequality for $p \in [0, \infty)$

Let $p \in [0, \infty)$. Assume that for any $\mathbf{x}, \mathbf{y} \in \mathbb{R}^n$,
$$
h(\lambda \mathbf{x} + (1-\lambda) \mathbf{y}) \geq M_{p}^{\lambda}(f(\mathbf{x}), g(\mathbf{y})).
$$
Then,
$$
\| h \|_1 \geq M_{p / (np + 1)}^{\lambda}(\| f \|_1, \| g \|_1).
$$

> Assume that $n \geq 2$ and the assertion of the theorem has been proved in all dimensions $k = 1, \cdots, n-1$.
>
> For every $s \in \mathbb{R}$ we define $h_s : \mathbb{R}^{n-1} \to \mathbb{R}_+$ by setting $h_s( \mathbf{w} )= h(\mathbf{w}, s)$, and $f_s, g_s: \mathbb{R}^{n-1} \to \mathbb{R}_+$ in an analogous way.
>
> Note that for fixed $s \in \mathbb{R}$, all the functions $f_s, g_s$ and $h_s$ are measurable. Besides, by
> $$
> \| f \|_1 = \int_{\mathbb{R}} \mathrm{d} s \int_{\mathbb{R}^{n-1}} f_s(\mathbf{u}) \mathrm{d} \mathbf{u} = \int_{\mathbb{R}} \| f_s \|_1 \mathrm{d} s < \infty,
> $$
> we know that $f_s \in L^{1} (\mathbb{R}^{n-1})$ a.e. for $s \in \mathbb{R}$. Similarly, $g_s \in L^{1} (\mathbb{R}^{n-1})$ a.e. for $s \in \mathbb{R}$.
>
> Now for fixed $s, t \in \mathbb{R}$, we have
> $$
> h_{\lambda s + (1 - \lambda) t}( \lambda \mathbf{u} + (1 - \lambda) \mathbf{v} )
> \geq M_{p}^{\lambda}(f_s(\mathbf{u}), g_t(\mathbf{v})),
> \quad \text{ for any } \mathbf{u}, \mathbf{v} \in \mathbb{R}^{n-1}.
> $$
> Therefore, for $s, t$ with $f_s, g_t \in L^{1} (\mathbb{R}^{n-1})$, by the inductive hypothesis we have
> $$
> \| h_{\lambda s + (1 - \lambda) t} \|_1 \geq M_{p / ((n-1)p + 1)}^{\lambda}(\| f_s \|_1, \| g_t \|_1).
> $$
> Now let $F, G: \mathbb{R}^n \to \mathbb{R}_+$ and $H: \mathbb{R}^n \to [0, \infty]$ be nonnegative measurable functions such that $H(s) = \| h_s \|_1$,
> $$
> F(s) = 
> \begin{cases}
> \| f_s \|_1, & \text{ if } f_s \in L^{1} (\mathbb{R}^{n-1}), \\
> 0, & \text{ otherwise, }
> \end{cases}
> \quad \text{ and } \quad
> G(s) = 
> \begin{cases}
> \| g_s \|_1, & \text{ if } g_s \in L^{1} (\mathbb{R}^{n-1}), \\
> 0, & \text{ otherwise. }
> \end{cases}
> $$
> Then, $F, G$ and $H$ are measurable with 
> $$
> H(\lambda s + (1 - \lambda) t) \geq M_{p / ((n-1)p + 1)}^{\lambda}(F(s), G(t)),
> \quad \text{ for all } s, t \in \mathbb{R}.
> $$
> Therefore, by the inductive hypothesis again, we get
> $$
> \| h \|_1 = \| H \|_1 \geq M_{q}^{\lambda}(\| F \|_1, \| G \|_1) 
> = M_{q}^{\lambda}(\| f \|_1, \| g \|_1),
> $$
> where
> $$
> q = \frac{p / ((n-1)p + 1)}{p/((n-1)p + 1) + 1} 
> = \frac{p}{p + (n-1)p + 1} = \frac{p}{np + 1}.
> $$

