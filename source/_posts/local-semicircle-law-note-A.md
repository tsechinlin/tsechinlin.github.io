---
title: Note A - Stochastic Domination
date: 2021-06-30 16:44:28
tags: 
  - Stochastic Domination
categories: Random Matrix
mathjax: true
---

[Notes] Benaych-Georges, Florent, and Antti Knowles. "Lectures on the local semicircle law for Wigner matrices." arXiv preprint arXiv:1601.04055 (2016).

<!--more-->

## Definitions and Notations

Consider two families of nonnegative random variables
$$
\begin{equation*}
X = \big \{ X^{(N)}(u) : N \in \mathbb{N}, u \in U^{(N)} \big \}
\quad \text{ and } \quad
Y = \big \{ Y^{(N)}(u) : N \in \mathbb{N}, u \in U^{(N)} \big \},
\end{equation*}
$$
where $U^{(N)}$ is a possibly $N$-dependent parameter set.

### Definition A.1 (stochastic domination)

We say that $X$ is **stochastically dominated** by $Y$, uniformly in $u$, if for any (small) $\varepsilon > 0$ and (large) $D > 0$ we have
$$
\begin{equation}
\mathbb{P} \big ( X^{(N)}(u)>N^{\varepsilon} Y^{(N)}(u) \big ) \leq N^{-D}
\end{equation}
$$
for all large enough $N \geq N_0 (\varepsilon, D)$ and $u \in U^{(N)}$.

If $X$ is stochastically dominated by $Y$, uniformly in $u$, we use the notation $X \prec Y$.

Moreover, if for some family of complex variables $X$ we have $|X| \prec Y$, we also write $X = O_\prec(Y)$.

### Definition A.2 (boundedness up to a constant factor)

In this note, we will also use the notation $X \lesssim Y$, which means that there exists some universal constant $C > 0$ such that
$$
\begin{equation}
X^{(N)}(u) \leq C Y^{(N)}(u)
\end{equation}
$$
for all (large) $N \in \mathbb{N}$ and $u \in U^{(N)}$.

When we have both $X \lesssim Y$ and $X \gtrsim Y$, we use the notation $X \sim Y$.

### Definition A.3 (high probability events)

Finally, we say that an event $\Xi = \Xi^{(N)}$ **holds with high probability** if $1 - \mathbb{I} (\Xi) \prec 0$, i.e. if for any $D > 0$, there exists $N_0 = N_0 (D)$ such that
$$
\begin{equation}
\mathbb{P} \big ( \Xi^{(N)} \big ) \geq 1 - N^{-D}.
\end{equation}
$$

## Properties

### Lemma A.1 (constant factors) <a name="lemma-A-1"></a>

Suppose that $X(u) \lesssim Y(u)$. Then $X(u) \prec Y(u)$.

> By assumption there exists some constant $C > 0$ such that $X(u) \leq C Y(u)$ for all $N$ and $u \in U$.
>
> Fix $\varepsilon > 0$. Then, for all $N \geq C^{1/\varepsilon}$ and $u \in U$, we have
> $$
> \begin{equation*}
> \mathbb{P} \big ( X(u) > N^\varepsilon Y(u) \big )
> \leq \mathbb{P} \big ( X(u) > C Y(u) \big )
> = 0.
> \end{equation*}
> $$

### Lemma A.2 (addition and multiplication) <a name="lemma-A-2"></a>

Suppose that $X_1 (u) \prec Y_1 (u)$ and $X_2 (u) \prec Y_2 (u)$. Then

+ $X_1 (u) + X_2 (u) \prec Y_1 (u) + Y_2(u)$.
+ $X_1 (u) X_2 (u) \prec Y_1 (u) Y_2(u)$.

> By assumption, for any $\varepsilon > 0$ and $D > 0$ we have
> $$
> \begin{equation*}
> \mathbb{P} \big ( X_1(u) > N^{\varepsilon} Y_1(u) \big ) \leq N^{-D}
> \quad \text{ and } \quad
> \mathbb{P} \big ( X_2(u) > N^{\varepsilon} Y_2(u) \big ) \leq N^{-D}
> \end{equation*}
> $$
> for all large enough $N \geq N_0 (\varepsilon, D)$ and $u \in U$.
>
> As a result, when $N \geq N_0(\varepsilon, D + 1)$, for any $u \in U$ we have
> $$
> \begin{align*}
> & \ \mathbb{P} \big ( X_1(u) + X_2 (u) > N^{\varepsilon} Y_1(u) + N^{\varepsilon} Y_2(u) \big ) \\
> \leq & \ \mathbb{P} \big ( X_1(u) > N^{\varepsilon} Y_1(u) \big ) + \mathbb{P} \big ( X_2(u) > N^{\varepsilon} Y_2(u) \big )
> \leq 2 N^{-(D + 1)} \leq N^{-D}.
> \end{align*}
> $$
> Similarly, when $N \geq N_0(\varepsilon / 2, D + 1)$, for any $u \in U$ we have
> $$
> \begin{align*}
> & \ \mathbb{P} \big ( X_1(u) X_2(u) > N^{\varepsilon} Y_1(u) Y_2(u) \big ) \\
> \leq & \ \mathbb{P} \big ( X_1(u)>N^{\varepsilon / 2} Y_1(u) \big ) + \mathbb{P} \big ( X_2(u) > N^{\varepsilon/2} Y_2(u) \big )
> \leq 2 N^{-(D + 1)} \leq N^{-D}.
> \end{align*}
> $$

### Lemma A.3 ($p$-th power) <a name="lemma-A-3"></a>

Suppose that $X (u) \prec Y (u)$. Then

+ $X (u)^p \prec Y (u)^p$ for any fixed $p \in (0, \infty)$.
+ $X (u)^p \succ Y (u)^p$ for any fixed $p \in (-\infty, 0)$.

> Fix $p \in (0, \infty)$. When $N \geq N_0 (\varepsilon / p, D)$, for any $u \in U$ we have
> $$
> \begin{equation*}
> \mathbb{P} \big ( X(u)^p > N^\varepsilon Y(u)^p \big )
> = \mathbb{P} \big ( X(u) > N^{\varepsilon / p} Y(u) \big )
> \leq N^{-D}.
> \end{equation*}
> $$
> The second statement follows directly from the first one since
> $$
> \begin{equation*}
> X (u) \prec Y (u) \quad \iff \quad \frac{1}{X (u)} \succ \frac{1}{Y (u)}.
> \end{equation*}
> $$

### Lemma A.4 (transitivity) <a name="lemma-A-4"></a>

Suppose that $X (u) \prec Y (u)$ and $Y (u) \prec Z (u)$. Then $X (u) \prec Z (u)$.

> Note that
> $$
> \begin{equation*}
> X (u) \prec Y (u) \iff \frac{X(u)}{Y(u)} \prec 1
> \quad \text{ and } \quad
> Y (u) \prec Z (u) \iff \frac{Y(u)}{Z(u)} \prec 1.
> \end{equation*}
> $$
> Therefore, by [Lemma A.2](#lemma-A-2) we have
> $$
> \begin{equation*}
> \frac{Z(u)}{X(u)} 
> = \frac{Z(u)}{Y(u)} \frac{Y(u)}{X(u)}
> \prec 1,
> \end{equation*}
> $$
> which means precisely $X (u) \prec Z (u)$.

### Lemma A.5 (summation) <a name="lemma-A-5"></a>

Suppose that $X (u, v) \prec Y (u, v)$ uniformly in $u \in U$ and $v \in V$. If $|V| \leq N^C$ for some constant $C$, then
$$
\begin{equation}
\sum_{v \in V} X (u, v) \prec \sum_{v \in V} Y (u, v)
\end{equation}
$$
uniformly in $u \in U$.

> Fix $\varepsilon > 0$ and $D > 0$. Then, for any $N \geq N_0 (\varepsilon, D + C)$ and $u \in U$,
> $$
> \begin{equation*}
> \mathbb{P} \left ( \sum_{v \in V} X (u, v) > N^\varepsilon \sum_{v \in V} Y (u, v) \right )
> \leq \sum_{v \in V} \mathbb{P} \big ( X(u, v)>N^{\varepsilon} Y(u, v) \big )
> \leq |V| N^{-(D + C)} \leq N^{-D}.
> \end{equation*}
> $$

### Lemma A.6 (subtraction) <a name="lemma-A-6"></a>

Suppose that $X(u)$ and $Y(u)$ are two families of complex variables satisfying
$$
\begin{equation}
| X (u) | \prec N^{-c} | Y (u) |,
\end{equation}
$$
where $c > 0$ is constant. Then, we have
$$
\begin{equation}
\big | Y (u) - X (u) \big | \succ | Y (u) |.
\end{equation}
$$

> By assumption, for any $\varepsilon > 0$ and $D > 0$ we have
> $$
> \begin{equation*}
> \mathbb{P} \big ( |X(u)| > N^{\varepsilon - c} | Y(u) | \big ) \leq N^{-D}
> \end{equation*}
> $$
> for all large enough $N \geq N_0 (\varepsilon, D)$ and $u \in U$.
>
> Fix $\varepsilon \in (0, c/2)$ and $D > 0$. Then, for $N$ large enough with $N \geq N_0 (\varepsilon, D) \vee 2^{1/\varepsilon}$, we have
> $$
> \begin{align*}
> & \ \mathbb{P} \big ( |Y(u)| > N^{\varepsilon} | Y(u) - X(u) | \big ) \\
> \leq & \ \mathbb{P} \big ( |Y(u)| > N^{\varepsilon} | Y(u) | - N^{\varepsilon} | X(u) | \big )
> = \mathbb{P} \big ( | X(u) | > (1 - N^{-\varepsilon}) | Y(u) | \big )
> \leq N^{-D}.
> \end{align*}
> $$
> for any $u \in U$, where in the last step we used $1 - N^{-\varepsilon} \geq N^{-\varepsilon} \geq N^{\varepsilon - c}$.

### Lemma A.7 (expectation and conditional expectation) <a name="lemma-A-7"></a>

Suppose that 

+ there exists some constant $C > 0$ such that, for all (large) $N \in \mathbb{N}$, the deterministic control parameter $\Phi (u)$ satisfies
    $$
    \begin{equation}
    \Phi(u) \geq N^{−C}
    \label{asm-7-1}
    \end{equation}
    $$

+ for all $p \in \mathbb{N}$ there is a constant $C_p > 0$ such that, for all (large) $N \in \mathbb{N}$ and $u \in U$, the nonnegative random variable $X(u)$ satisfies
    $$
    \begin{equation}
    \mathbb{E} X(u)^p \leq N^{C_p}.
    \label{asm-7-2}
    \end{equation}
    $$

#### Part I (expectation)

We have the equivalence
$$
\begin{equation}
X(u) \prec \Phi(u)
\quad \iff \quad
\mathbb{E} X(u)^p \prec \Phi(u)^p \text{ for any fixed } p \in \mathbb{N}.
\label{eq-7-1}
\end{equation}
$$

> **Proof for ($\Leftarrow$)**: Fix $\varepsilon > 0$ and $D > 0$. Now choose $p \equiv p(\varepsilon, D)$ large enough such that $p \geq D/\varepsilon + 1$.
>
> Then, by $\mathbb{E} X(u)^p \prec \Phi(u)^p$ we have
> $$
> \begin{equation*}
> \mathbb{E} X(u)^p \leq N^\varepsilon \Phi(u)^p
> \end{equation*}
> $$
> for all large enough $N \geq N_0 (\varepsilon, D)$ and $u \in U$. Hence, by Markov’s inequality, we have
> $$
> \begin{equation*}
> \mathbb{P} \big ( X(u) \geq N^{\varepsilon} \Phi(u) \big )
> \leq \frac{\mathbb{E} X(u)^p}{N^{\varepsilon p} \Phi(u)^p} 
> \leq N^{- \varepsilon (p -1)}
> \leq N^{-D}.
> \end{equation*}
> $$
> **Proof for ($\Rightarrow$)**: Note that by [Lemma A.3](#lemma-A-3), we have
> $$
> \begin{equation*}
> X(u) \prec \Phi(u)
> \quad \Longrightarrow \quad
> X(u)^q \prec \Phi(u)^q \text{ for any fixed } q \in \mathbb{N}.
> \end{equation*}
> $$
> Moreover, the two assumptions $\eqref{asm-7-1}$ and $\eqref{asm-7-2}$ are still fulfilled when $X(u)$ and $\Phi(u)$ are replaced by $X(u)^q$ and $\Phi(u)^q$.
>
> Therefore, it suffices to show that
> $$
> \begin{equation*}
> X(u) \prec \Phi(u)
> \quad \Longrightarrow \quad
> \mathbb{E} X(u) \prec \Phi(u).
> \end{equation*}
> $$
> Fix any $\varepsilon > 0$, and let $D \geq C_{2} + 2 C$. Then, by $X(u) \prec \Phi(u)$ we have
> $$
> \begin{equation*}
> \mathbb{P} \big ( X(u) > N^{\varepsilon} \Phi(u) \big ) \leq N^{-D}
> \end{equation*}
> $$
> for all large enough $N \geq N_0 (\varepsilon, D)$ and $u \in U$. Then, by Cauchy–Schwarz inequality, it follows that
> $$
> \begin{align*}
> \mathbb{E} X(u)
> & = \mathbb{E} \big [ X(u) \cdot \mathbb{I} \big ( X(u) > N^{\varepsilon} \Phi(u) \big ) \big ] + \mathbb{E} \big [ X(u) \cdot \mathbb{I} \big ( X(u) \leq N^{\varepsilon} \Phi(u) \big ) \big ] \\
> & \leq \big [ \mathbb{E} X(u)^{2} \big ]^{1/2} \cdot \mathbb{P} \big ( X(u) > N^{\varepsilon} \Phi(u) \big )^{1/2} + N^{\varepsilon} \Phi(u) \\
> & \leq N^{C_{2} / 2 - D/2} + N^{\varepsilon} \Phi(u) \\
> & \leq N^{- C} + N^{\varepsilon} \Phi(u)
> \leq 2 N^{\varepsilon} \Phi(u),
> \end{align*}
> $$
> where in the last step we used the assumption $\Phi(u) \geq N^{−C}$.

#### Part II (conditional expectation) 

We further assume the family $X(u)$ is defined on the space $(\Omega, \mathcal{F}, \mathbb{P})$, and $\{ \mathcal{F}_{v} \}_{v \in V}$ is a collection of sub-$\sigma$-fields, i.e., $\mathcal{F}_v \subset \mathcal{F}$ for each $v \in V$.

For any $\mathcal{F}$-measurable variable $Z$, define
$$
\begin{equation}
\mathcal{P}_v Z := \mathbb{E} (Z | \mathcal{F}_v) 
\quad \text{ and } \quad
\mathcal{Q}_v Z := Z - \mathcal{P}_v Z.
\end{equation}
$$
Then, we have
$$
\begin{equation}
X(u) \prec \Phi(u)
\quad \Longrightarrow \quad
\begin{cases}
\mathcal{P}_v \big ( X(u)^p \big ) = O_\prec \big ( \Phi(u)^p \big ) \\
\mathcal{Q}_v \big ( X(u)^p \big ) = O_\prec \big ( \Phi(u)^p \big ) 
\end{cases}
\text{ for any fixed } p \in \mathbb{N}.
\label{eq-7-2}
\end{equation}
$$

> Again, by [Lemma A.3](#lemma-A-3), it suffices to show that
> $$
> \begin{equation*}
> X(u) \prec \Phi(u)
> \quad \Longrightarrow \quad
> \begin{cases}
> \mathcal{P}_v X(u) = O_\prec \big ( \Phi(u) \big ), \\
> \mathcal{Q}_v X(u) = O_\prec \big ( \Phi(u) \big ) .
> \end{cases}
> \end{equation*}
> $$
> Note that by Jensen’s inequality for conditional expectations, we have
> $$
> \begin{equation*}
> \mathbb{E} | \mathcal{P}_v Z |^q \leq \mathbb{E} \big ( \mathcal{P}_v | Z |^q \big ) = \mathbb{E} | Z |^q
> \end{equation*}
> $$
> for any variable $Z \in \mathcal{F}$ and $q \in \mathbb{N}$.
>
> Now, for any $\varepsilon > 0$ and $D > 0$, we choose $q \equiv q(\varepsilon, D)$ large enough such that $q \geq D/\varepsilon + 1$. Then, by part I,
> $$
> \begin{equation*}
> X(u) \prec \Phi(u) 
> \quad \Longrightarrow \quad
> \mathbb{E} X(u)^{q} \prec \Phi(u)^{q}.
> \end{equation*}
> $$
> This means that for all large enough $N \geq N_0 (\varepsilon, D)$ and $u \in U$,
> $$
> \begin{equation*}
> \mathbb{E} X(u)^{q} \leq N^\varepsilon \Phi(u)^{q}
> \end{equation*}
> $$
> Consequently, when $N \geq N_0 (\varepsilon, D)$, for any $u \in U$ and $v \in V$ we have
> $$
> \begin{equation*}
> \mathbb{P} \big ( \mathcal{P}_v X(u) \geq N^{\varepsilon} \Phi (u) \big )
> \leq \frac{\mathbb{E} \big | \mathcal{P}_v X(u) \big |^q}{N^{\varepsilon q} \Phi (u) ^{q}}
> \leq \frac{\mathbb{E} X(u)^{q}}{N^{\varepsilon q} \Phi (u) ^{q}}
> \leq N^{- \varepsilon (q - 1)}
> \leq N^{-D}.
> \end{equation*}
> $$
> Now we have proved that $\mathcal{P}_v X(u) \prec \Phi(u)$. Finally, by definition of $\mathcal{Q}_v$ and [Lemma A.2](#lemma-A-2), we have
> $$
> \begin{equation*}
> \big | \mathcal{Q}_v X(u) \big |
> = \big | X(u) - \mathcal{P}_v X(u) \big |
> \leq X(u) + \mathcal{P}_v X(u)
> \prec \Phi
> \end{equation*}
> $$
> uniformly in $u \in U$ and $v \in V$.
