---
title: Conditional Expectation
date: 2020-11-30 21:15:27
tags: 
  - Conditional Expectation
categories: Probability and Measure
mathjax: true
---

[Notes] <u>Probability: Theory and Examples</u> by Rick Durrett.

<!--more-->

## Definitions

Given a probability space $(\Omega, \mathcal{F}_0, \mathbb{P})$, a $\sigma$-field $\mathcal{F} \subset \mathcal{F}_0$, and a random variable $X \in \mathcal{F}_0$ with $\mathbb{E}|X| < \infty$, define the **conditional expectation** of $X$ given $\mathcal{F}$, $\mathbb{E}(X|\mathcal{F})$, to be any random variable $Y$ that has

+ $Y \in \mathcal{F}$, that is, $Y$ is $\mathcal{F}$-measurable.
+ For all $A \in \mathcal{F}$,
    $$
    \int_A X \mathrm{d} \mathbb{P} = \int_A Y \mathrm{d} \mathbb{P}.
    $$

Any $Y$ satisfying the two conditions above is said to be a version of $\mathbb{E}(X|\mathcal{F})$.

### Integrability

If $Y$ is a version of $\mathbb{E}(X|\mathcal{F})$, then it is integrable with $\mathbb{E}|Y| \leq \mathbb{E}|X| < \infty$.

### Uniqueness

If $Y$ and $Y^\prime$ are two versions of $\mathbb{E}(X|\mathcal{F})$, then $Y = Y^\prime$, a.s.

> Since $Y$ and $Y^\prime$ are versions of $\mathbb{E}(X|\mathcal{F})$, we have
> $$
> \int_A Y \mathrm{d} \mathbb{P} = \int_A X \mathrm{d} \mathbb{P} = \int_A Y^\prime \mathrm{d} \mathbb{P}, \quad \forall A \in \mathcal{F}.
> $$
> For any $\varepsilon > 0$, let $A = \{ Y - Y^\prime \geq \varepsilon \} \in \mathcal{F}$. Then we have
> $$
> 0 = \int_A Y \mathrm{d} \mathbb{P} - \int_A Y^{\prime} \mathrm{d} \mathbb{P} = \int_A (Y - Y^\prime) \mathrm{d} \mathbb{P} \geq \varepsilon \mathbb{P}(A),
> $$
> so $\mathbb{P}(A) = 0$. Since this holds for all $\varepsilon > 0$, we have $Y \leq Y^\prime$, a.s. Interchanging the roles of $Y$ and $Y^\prime$, we can conclude that $Y = Y^\prime$, a.s.

If $X = X^\prime$ on $B \in \mathcal{F}$, then $\mathbb{E}(X|\mathcal{F}) = \mathbb{E}(X^\prime|\mathcal{F})$ a.s. on $B$.

> Write $Y = \mathbb{E}(X|\mathcal{F})$ and $Y^\prime = \mathbb{E}(X^\prime|\mathcal{F})$. Then, for any $A \in \mathcal{F}$ with $A \subset B$, we have
> $$
> \int_A Y \mathrm{d} \mathbb{P} = \int_A X \mathrm{d} \mathbb{P}
> = \int_A X^\prime \mathrm{d} \mathbb{P} =\int_A Y^\prime \mathrm{d} \mathbb{P}.
> $$
> For any $\varepsilon > 0$, let $A = B \bigcap \{  Y - Y^\prime \geq \varepsilon \} \in \mathcal{F}$. Then we have
> $$
> 0 = \int_A Y \mathrm{d} \mathbb{P} - \int_A Y^{\prime} \mathrm{d} \mathbb{P} = \int_A (Y - Y^\prime) \mathrm{d} \mathbb{P} \geq \varepsilon \mathbb{P}(A),
> $$
> so $\mathbb{P}(A) = 0$. Since this holds for all $\varepsilon > 0$, we have $Y \leq Y^\prime$ on $B$, a.s. Interchanging the roles of $Y$ and $Y^\prime$, we can conclude that $Y = Y^\prime$ on $B$, a.s.

### Existence

The conditional expectation of $X$ given $\mathcal{F}$ exists.

> **Non-negative Case**
>
> Suppose first that $X \geq 0$. Let $\mu = \mathbb{P}$ and
> $$
> \nu (A) = \int_A X \mathrm{d} \mu = \int_A X \mathrm{d} \mathbb{P}, \quad \forall A \in \mathcal{F}.
> $$
> Then $\nu$ is a finite measure on $\mathcal{F}$ since
>
> + $\nu(A) \geq 0$ for any $A \in \mathcal{F}$.
> + $\nu(\varnothing) = 0$.
> + $\nu(\Omega) = \mathbb{E} X < \infty$.
> + If $\{ A_n \}_{n=1}^{\infty} \subset \mathcal{F}$ are pairwise disjoint and $A = \bigcup_{n=1}^\infty A_i$, then 
>     $$
>     \nu \left ( A \right ) = \int_{\Omega} (X \cdot \mathbb{I}_A) \mathrm{d} \mu 
>     = \int_{\Omega} \left ( X \cdot \sum_{n=1}^\infty \mathbb{I}_{A_n} \right ) \mathrm{d} \mu = \sum_{n=1}^\infty \int_{\Omega} (X \cdot \mathbb{I}_{A_n}) \mathrm{d} \mu = \sum_{n=1}^\infty \nu \left ( A_n \right ),
>     $$
>     where we use the monotone convergence theorem in the third equality.
>
> Now for any $A \in \mathcal{F}$ with $\mu(A) = 0$, we have $\nu(A) = 0$, which means that $\nu \ll \mu$, i.e., $\nu$ is absolutely continuous with respect to $\mu$. Therefore, we have the Radon-Nikodym derivative $\mathrm{d} \nu / \mathrm{d} \mu$ which satisfies
>
> + $\mathrm{d} \nu / \mathrm{d} \mu \in \mathcal{F}$.
> + For any $A \in \mathcal{F}$,
>     $$
>     \int_A X \mathrm{d} \mathbb{P} = \nu(A) = \int_A \frac{\mathrm{d} \nu}{\mathrm{d} \mu} \mathrm{d} \mu = \int_A \frac{\mathrm{d} \nu}{\mathrm{d} \mu} \mathrm{d} \mathbb{P}.
>     $$
>
> In conclusion, $\mathrm{d} \nu / \mathrm{d} \mu$ is a version of $\mathbb{E}(X|\mathcal{F})$.
>
> **General Case**
>
> For the general case, write $X = X^+ - X^-$, and let $Y_1 = \mathbb{E}(X^+ | \mathcal{F})$ and $Y_2 = \mathbb{E}(X^- | \mathcal{F})$. Then,
>
> + $Y_1 - Y_2 \in \mathcal{F}$.
> + For any $A \in \mathcal{F}$,
>
> $$
> \begin{align*}
> \int_A X \mathrm{d} \mathbb{P} = \int_A X^+ \mathrm{d} \mathbb{P} - \int_A X^- \mathrm{d} \mathbb{P} = \int_A Y_1 \mathrm{d} \mathbb{P} - \int_A Y_2 \mathrm{d} \mathbb{P} = \int_A (Y_1 - Y_2) \mathrm{d} \mathbb{P}.
> \end{align*}
> $$

## Examples

### Perfect information

If $X \in \mathcal{F}$, then $\mathbb{E}(X | \mathcal{F}) = X$.

### No information

Suppose $X$ is independent of $\mathcal{F}$, that is, for all $B \in \mathcal{R}$ and $\mathcal{F}$,
$$
\mathbb{P} \left ( \{ X \in B \} \cap A \right ) = \mathbb{P} \left ( X \in B \right ) \mathbb{P} \left ( A \right ).
$$
In this case, we have $\mathbb{E}(X | \mathcal{F}) = \mathbb{E}X$.

> Note that
>
> + $\mathbb{E}X \in \mathcal{F}$.
> + If $A \in \mathcal{F}$, then $X$ and $\mathbb{I}_A \in \mathcal{F}$ are independent, which implies that
>     $$
>     \int_A X \mathrm{d} \mathbb{P} = \mathbb{E} (X \cdot \mathbb{I}_A) = \mathbb{E} X \cdot \mathbb{E} \mathbb{I}_A = \int_A \mathbb{E} X \mathrm{d} \mathbb{P}.
>     $$

### Conditional Probability & Bayes' Formula

For a event $A \in \mathcal{F}_0$, the conditional expectation $\mathbb{E}(\mathbb{I}_A | \mathcal{F})$ is call the **conditional probability** of $A$ given $\mathcal{F}$, denoted by $\mathbb{P}(A | \mathcal{F})$.

**Bayes' theorem** states that, for any $A \in \mathcal{F}_0$ and $B \in \mathcal{F}$, we have
$$
\mathbb{P} (B | A) = \int_B \mathbb{P}(A | \mathcal{F}) \mathrm{d} \mathbb{P} \bigg / \int_{\Omega} \mathbb{P}(A | \mathcal{F}) \mathrm{d} \mathbb{P}.
$$

> By definition of $\mathbb{P}(A | \mathcal{F})$,  we have
> $$
> \int_B \mathbb{P}(A | \mathcal{F}) \mathrm{d} \mathbb{P} 
> = \int_B \mathbb{I}_A \mathrm{d} \mathbb{P} = \mathbb{P} ( A \cap B )
> $$
> and
> $$
> \int_\Omega \mathbb{P}(A | \mathcal{F}) \mathrm{d} \mathbb{P} 
> = \int_\Omega \mathbb{I}_A \mathrm{d} \mathbb{P} = \mathbb{P} \left ( A \right ).
> $$

### Bayes' Formula for $\sigma$-field Generated by Partition

Suppose $\{ \Omega_n \} \subset \mathcal{F}_0$ is a finite or countably infinite partition of $\Omega$ into disjoint sets, each of which has positive probability. Let
$$
\mathcal{F} = \sigma ( \{ \Omega_n \} ) = \left \{ \bigcup_{k=1}^K \Omega_{n_k} :
0 \leq K \leq \infty, \ \{ n_k \}_{k=1}^K \subset \mathbb{Z}_+ \text{ is strictly increasing} \right \}
$$
be the $\sigma$-field generated by these sets. Then
$$
\mathbb{E}(X|\mathcal{F}) = \sum_{n} \frac{\mathbb{E}(X; \Omega_n)}{\mathbb{P}(\Omega_n)} \mathbb{I}_{\Omega_n}.
$$
In this situation, Bayes' formula reduces to, for any $A \in \mathcal{F}_0$,
$$
\mathbb{P} (\Omega_k | A) = \mathbb{P} (A | \Omega_k) \mathbb{P} (\Omega_k) \bigg / \sum_n \mathbb{P} (A | \Omega_n) \mathbb{P} (\Omega_n).
$$

> Note that
>
> + The random variable is constant on each $\Omega_n$, so it is measurable with respect to $\mathcal{F}$.
> + By the construction of $\mathcal{F}$, it is enough to check $\mathbb{E} (\mathbb{E}(X|\mathcal{F}); A)$ for each $A = \Omega_k$, which is trivial since
>     $$
>     \int_{\Omega_k} \left ( \sum_{n} \frac{\mathbb{E}(X; \Omega_n)}{\mathbb{P}(\Omega_n)} \mathbb{I}_{\Omega_n} \right ) \mathrm{d} \mathbb{P} 
>     = \int_{\Omega_k} \frac{\mathbb{E}(X; \Omega_k)}{\mathbb{P}(\Omega_k)} \mathrm{d} \mathbb{P} 
>     = \mathbb{E}(X; \Omega_k)
>     = \int_{\Omega_k} X \mathrm{d} \mathbb{P}.
>     $$
>
> In this situation, for any $A \in \mathcal{F}_0$, we have
> $$
> \mathbb{P}(A | \mathcal{F}) = \mathbb{E}(\mathbb{I}_A | \mathcal{F}) = \sum_{n} \frac{\mathbb{E}(\mathbb{I}_A; \Omega_n)}{\mathbb{P}(\Omega_n)} \mathbb{I}_{\Omega_n}
> = \sum_{n} \mathbb{P}(A | \Omega_n) \mathbb{I}_{\Omega_n}.
> $$
> The Bayes' formula follows.

### Conditional Expectation Given Random Variables

Let $X, Y \in \mathcal{F}_0$ be two $\mathcal{F}_0$-measurable random variables. The **conditional expectation** of $X$ given $Y$, $\mathbb{E}(X|Y)$ is defined to be $\mathbb{E}(X|\sigma(Y))$, where $\sigma(Y)$ is the $\sigma$-field generated by $Y$.

### Conditional Expectation Given Random Variables - with Known Joint Density

Suppose $X$ and $Y$ have joint density $f(x, y)$, that is,
$$
\mathbb{P}((X, Y) \in B) = \int_{B} f(x, y) \mathrm{d} x \mathrm{d} y, \quad \forall B \in \mathcal{R}^{2}.
$$
In this case, if $\mathbb{E}|g(X)| < \infty$, then $\mathbb{E}(g(X)|Y) = h(Y)$, where
$$
h(y) \int_{\mathbb{R}} f(x, y) \mathrm{d} x = \int_{\mathbb{R}} g(x) f(x, y) \mathrm{d} x.
$$
Here $h$ can be anything if $\int_{\mathbb{R}} f(x, y) \mathrm{d} x = 0$.

> Let
> $$
> h_1(y) = \int_{\mathbb{R}} g(x) f(x, y) \mathrm{d} x 
> \quad \text{ and } \quad
> h_2(y) = \int_{\mathbb{R}} f(x, y) \mathrm{d} x,
> $$
> and define $D = \left \{ y \in \mathbb{R}: h_2(y) = 0 \right \}$. 
>
> + Note that by Fubini’s theorem, $h_1$ and $h_2$ are both Borel measurable, so $h_1(Y)$ and $h_2(Y)$ are $\sigma(Y)$-measurable. In addition,
>     $$
>     \begin{align*}
>     \mathbb{P} \left ( \varphi(Y) = 0 \right ) 
>     & = \mathbb{P} (Y \in D) 
>     = \mathbb{P}((X, Y) \in \mathbb{R} \times D) \\
>     & = \int_{\mathbb{R} \times D} f(x, y) \mathrm{d} x \mathrm{d} y
>     = \int_D h_2(y) \mathrm{d} y = 0.
>     \end{align*}
>     $$
>     Therefore, we have $\varphi(Y) > 0$ a.s., and we can conclude that $h(Y) = h_1(Y) / h_2(Y)$ is $\sigma(Y)$-measurable.
> + On the other hand, for any $A \in \sigma(Y)$, there exists some $B \in \mathcal{R}$ such that 
>     $$
>     A = \{ Y \in B \} = \{ (X, Y) \in \mathbb{R} \times B \}.
>     $$
>     Using change of variables, we can conclude that
>     $$
>     \begin{align*}
>     \int_{A} h(Y) \mathrm{d} \mathbb{P}
>     & = \int_{ \{ (X, Y) \in \mathbb{R} \times B \} } h(Y) \mathrm{d} \mathbb{P} 
>     = \int_B \int_{\mathbb{R}} h(y) f(x, y) \mathrm{d} x \mathrm{d} y \\
>     & = \int_B \int_{\mathbb{R}} g(x) f(x, y) \mathrm{d} x \mathrm{d} y
>     = \int_{ \{ (X, Y) \in \mathbb{R} \times B \} } g(X) \mathrm{d} \mathbb{P} 
>     = \int_{A} g(X) \mathrm{d} \mathbb{P}.
>     \end{align*}
>     $$

### Conditional Expectation Given Random Variables - with Independence

Suppose $X$ and $Y$ are independent. Let $\varphi$ be a function with $\mathbb{E}|\varphi(X,Y)| < \infty$ and let $g(x) = \mathbb{E} \varphi(x, Y)$. Then
$$
\mathbb{E}(\varphi(X, Y)|X) = g(X).
$$

> Assume that the distribution of $X$ and $Y$ are $\mu$ and $\nu$, respectively.
>
> + Since $\mathbb{E}|\varphi(X,Y)| < \infty$, by Fubini’s theorem we know that the following map
>     $$
>     x \mapsto g(x) = \mathbb{E} \varphi(x, Y) = \int_{\Omega} \varphi(x, Y) \mathrm{d} \mathbb{P} = \int_{\mathbb{R}} \varphi(x, y) \nu (\mathrm{d} y).
>     $$
>     is Borel measurable. Thus $g(X)$ is $\sigma(X)$-measurable.
> + Let $A \in \sigma(X)$. Then there exist a Borel set $B \in \mathcal{R}$ such that $A = \{ X \in B  \}$. Using change of variables and the fact that $X$ and $Y$ are independent, we can conclude that
>     $$
>     \begin{align*}
>     \int_{A} \varphi(X, Y) \mathrm{d} \mathbb{P} 
>     & = \int_{\Omega} \varphi(X, Y) \cdot \mathbb{I}_C(X) \mathrm{d} \mathbb{P} 
>     = \int_{\mathbb{R}^2} \varphi(x, y) \cdot \mathbb{I}_C(x) \mathrm{d} (\mu \times \nu) \\
>     & = \int_{\mathbb{R}} \int_{\mathbb{R}} \varphi(x, y) \cdot \mathbb{I}_C(x) \nu(\mathrm{d} y) \mu (\mathrm{d} x)
>     = \int_{\mathbb{R}} g(x) \mathbb{I}_C(x) \mu (\mathrm{d} x) \\
>     & = \int_{\Omega} g(X) \mathbb{I}_C(X) \mathrm{d} \mathbb{P}
>     = \int_{A} g(X) \mathrm{d} \mathbb{P}.
>     \end{align*}
>     $$

## Properties

### Linearity

$$
\mathbb{E}(a X + bY | \mathcal{F}) = a \mathbb{E}(X | \mathcal{F}) + b \mathbb{E}(Y | \mathcal{F}).
$$

### Monotonicity

If $X \leq Y$, then
$$
\mathbb{E}(X | \mathcal{F}) \leq \mathbb{E}(Y | \mathcal{F}).
$$

### Monotone Converge Theorem

If $X_n \geq 0$ and $X_n \uparrow X$ with $\mathbb{E}|X| < \infty$, then
$$
\mathbb{E}(X_n | \mathcal{F}) \ \big \uparrow \ \mathbb{E}(X | \mathcal{F}).
$$

> By monotonicity of conditional expectation, we know that $\mathbb{E}(X_n | \mathcal{F})$ is increasing. Let
> $$
> Z = \sup_{n} \mathbb{E}(X_n | \mathcal{F}) \in \mathcal{F}.
> $$
> Then by the monotone convergence theorem, for any $A \in \mathcal{F}$, we have
> $$
> \int_A Z \mathrm{d} \mathbb{P}
> = \lim_{n \to \infty} \int_A \mathbb{E}(X_n | \mathcal{F}) \mathrm{d} \mathbb{P}
> = \lim_{n \to \infty} \int_A X_n \mathrm{d} \mathbb{P} 
> = \int_A X \mathrm{d} \mathbb{P} 
> = \int_A \mathbb{E}(X | \mathcal{F}) \mathrm{d} \mathbb{P}.
> $$
> Since $\mathbb{E}|X| < \infty$, the equality above gives
> $$
> \int_A \big [ Z - \mathbb{E}(X | \mathcal{F}) \big ] \mathrm{d} \mathbb{P} = 0,
> \quad \forall A \in \mathcal{F},
> $$
> which implies $Z - \mathbb{E}(X | \mathcal{F}) = 0$ a.s. since both $Z$ and $\mathbb{E}(X | \mathcal{F})$ are $\mathcal{F}$-measurable.

If $X_n \downarrow X$ with $\mathbb{E}|X|, \mathbb{E}|X_1| < \infty$, then
$$
\mathbb{E}(X_n | \mathcal{F}) \ \big \downarrow \ \mathbb{E}(X | \mathcal{F}).
$$

### Law of total probability

Assume that $\mathbb{E}|X| < \infty$, then we have
$$
\mathbb{E}(X) = \mathbb{E} (\mathbb{E}(X | \mathcal{F})).
$$

When $X = \mathbb{I}_A$ for some $A \in \mathcal{F}_0$ and $\mathcal{F}$ is generated by $\{ \Omega_n \} \subset \mathcal{F}_0$, a partition of $\Omega$, this becomes
$$
\mathbb{P} (A) = \sum_{n} \mathbb{P}(A | \Omega_n) \mathbb{P} (\Omega_n).
$$

### Order of $\sigma$-field

If $\mathcal{F} \subset \mathcal{G}$ and $\mathbb{E}(X|\mathcal{G}) \in \mathcal{F}$, then $\mathbb{E}(X|\mathcal{G}) = \mathbb{E}(X|\mathcal{F})$.

> Notice that we have $\mathbb{E}(X|\mathcal{G}) \in \mathcal{F}$ and for any $A \in \mathcal{F} \subset \mathcal{G}$,
> $$
> \int_A \mathbb{E}(X|\mathcal{G}) \mathrm{d} \mathbb{P} 
> = \int_A X \mathrm{d} \mathbb{P}.
> $$

If $\mathcal{F}_1 \subset \mathcal{F}_2$, then

+ $\mathbb{E} \big ( \mathbb{E}(X|\mathcal{F}_1) \big | \mathcal{F}_2 \big ) = \mathbb{E}(X|\mathcal{F}_1)$,
+ $\mathbb{E} \big ( \mathbb{E}(X|\mathcal{F}_2) \big | \mathcal{F}_1 \big ) = \mathbb{E}(X|\mathcal{F}_1)$.

> For the first one, we are in the same place as the example of perfect information since we have
> $$
> \mathbb{E}(X|\mathcal{F}_1) \in \mathcal{F}_1 \subset \mathcal{F}_2.
> $$
> For the second one, note that $\mathbb{E}(X|\mathcal{F}_1) \in \mathcal{F}_1$, and for any $A \in \mathcal{F}_1 \subset \mathcal{F}_2$, we have
> $$
> \int_A \mathbb{E}(X|\mathcal{F}_1) \mathrm{d} \mathbb{P} = \int_A X \mathrm{d} \mathbb{P} = \int_A \mathbb{E}(X|\mathcal{F}_2) \mathrm{d} \mathbb{P}.
> $$

If $X \in \mathcal{F}$ and $\mathbb{E} |Y|, \mathbb{E}|XY| < \infty$,then
$$
\mathbb{E}(XY | \mathcal{F}) = X \mathbb{E}(Y|\mathcal{F}).
$$


### Chebyshev’s inequality

$$
\mathbb{P} (|X| \geq a | \mathcal{F}) \leq a^{-2} \mathbb{E} \left ( X^2 | \mathcal{F} \right ).
$$

> Note that $\mathbb{I}_{|X| \geq a} \leq a^{-2} X^2$. Thus by monotonicity of conditional expectation we have
> $$
> \mathbb{P} (|X| \geq a | \mathcal{F}) 
> = \mathbb{E} (\mathbb{I}_{|X| \geq a} | \mathcal{F}) 
> \leq \mathbb{E} (a^{-2} X^2 | \mathcal{F})
> = \mathbb{E} (X^2 | \mathcal{F}).
> $$

### Cauchy-Schwarz inequality

Assume that $\mathbb{E} X^2, \mathbb{E} Y^2, \mathbb{E}|XY| < \infty$. Then 
$$
\mathbb{E}(XY|\mathcal{F})^2 \leq \mathbb{E} \left ( X^2|\mathcal{F} \right ) \mathbb{E} \left ( Y^2|\mathcal{F} \right ).
$$

> For any $\theta \in \mathbb{Q}$, we have $\mathbb{E} \left ( (X - \theta Y)^2|\mathcal{F} \right ) \geq 0$ a.s. Note that $\mathbb{Q}$ is countable. Thus
> $$
> \mathbb{E} \left ( X^2|\mathcal{F} \right ) - 2 \theta \cdot \mathbb{E}(XY|\mathcal{F}) + \theta^2 \mathbb{E} \left ( Y^2|\mathcal{F} \right ) \geq 0, 
> \quad \forall \theta \in \mathbb{Q}, 
> \quad \text{a.s.}
> $$
> This implies that,
> $$
> \mathbb{E}(XY|\mathcal{F})^2 \leq \mathbb{E} \left ( X^2|\mathcal{F} \right ) \mathbb{E} \left ( Y^2|\mathcal{F} \right ), \quad \text{a.s.}
> $$

### Jensen’s inequality

Let $\varphi$ be a convex function on $\mathbb{R}$ and suppose that $\mathbb{E}|X|, \mathbb{E}|\varphi(X)| < \infty$. Then
$$
\varphi(\mathbb{E}(X|\mathcal{F})) \leq \mathbb{E}(\varphi(X)|\mathcal{F}).
$$

> **Properties of Sub-gradient**
>
> Assume that $\varphi: \mathbb{R} \to \mathbb{R}$ is convex. Then we have the following properties for the sub-gradient of $\varphi$.
>
> + **Monotonicity**: If $x_1 < x_2$, then for any $g_1 \in \partial \varphi(x_1)$ and $g_2 \in \partial \varphi(x_2)$, we have $g_1 \leq g_2$.
> + **Continuity**: Assume that $x_n \to x$ and $g_n \in \partial \varphi(x_n)$ for each $n$. If $g_n$ converges to $g$, then $g \in \partial \varphi (x)$.
> + **Intermediate Value Theorem**: Assume that $x_1 < x_2$ and $g_1 < g_2$ with $g_i \in \partial \varphi(x_i)$, $i = 1, 2$. Then for any $g_1 < g < g_2$, there exists some $x \in [x_1, x_2]$ such that $g \in \partial \varphi(x)$.
>
> For the last statement, we can use binary search to find $x$. For each $n \geq 1$, consider $c_n = (a_n + b_n) / 2$.
>
> + If $g \in \partial \varphi(c_n)$, then searching is completed.
> + If $h > g$ for any $h \in \partial \varphi(c_n)$, then let $[a_{n+1}, b_{n+1}] = [a_n, c_n]$.
> + If $h < g$ for any $h \in \partial \varphi(c_n)$, then let $[a_{n+1}, b_{n+1}] = [c_n, b_n]$.
>
> Assume that the searching does not stop in any certain step. In this case, we have a sequence of nested intervals $\{ [a_n, b_n] \}$ whose length converges to $0$, which means that there exists a unique point $x$ with $x \in \bigcap_{n} [a_n, b_n]$. 
>
> Now, for each $n$, pick $h_n \in \partial \varphi(a_n)$ and $h_n^\prime \in \partial \varphi(b_n)$. By the construction of $a_n$ and $b_n$, we know that $h_n < g < h_n^\prime$ for each $n$. On the other hand, by the monotonicity of sub-gradients, we know that $h_n$ is non-decreasing and $h_n^\prime$ is non-increasing. Thus $\lim_{n \to \infty} h_n$ and $\lim_{n \to \infty} h_n^\prime$ exist with
> $$
> \lim_{n \to \infty} h_n \leq g \leq \lim_{n \to \infty} h_n^\prime.
> $$
> Finally, since $a_n \uparrow x$ and $b_n \downarrow x$, by the continuity of sub-gradients, we can conclude that
> $$
> g \in \left [ \lim_{n \to \infty} h_n, \lim_{n \to \infty} h_n^\prime \right ] \subset \partial \varphi (x).
> $$
> **Lower Envelope Generated by Linear Functions with Rational Coefficients**
>
> If $\bigcup_{x \in \mathbb{R}} \partial \varphi (x)$ contains more than one element, then it is a finite or infinite interval with positive length, since by the intermediate value theorem above we know that $\bigcup_{x \in } \partial \varphi (x) \subset \mathbb{R}$ is convex. In this case, the set 
> $$
> S = \left \{ (a, b) \in \mathbb{Q}^2: ax + b \leq \varphi(x) \text { for all } x \in \mathbb{R} \right \}
> $$
> is not empty. Now given any $x \in \mathbb{R}$, we claim
> $$
> \varphi(x) = \sup \{ ax + b : (a, b) \in S \}.
> $$
> This is trivial when $\partial \varphi(x) \cap \mathbb{Q} \not= \varnothing$. As for the case $\partial \varphi(x) = \{ g \}$ for some $g \in \mathbb{R} \backslash \mathbb{Q}$, assume that
> $$
> \varphi(x) - \sup \{ ax + b : (a, b) \in S \} = \varepsilon > 0.
> $$
> Since $\bigcup_{x \in \mathbb{R}} \partial \varphi (x)$ is an interval, we can find a $x_1 \in \mathbb{R}$ with $g_1 \in \partial \varphi(x_1) \cap \mathbb{Q}$. If $x_k$ and $g_k \in \partial \varphi(x_1) \cap \mathbb{Q}$ have been defined for all $1 \leq k \leq n$. Since $g_{n} \in \mathbb{Q}$ and $g \notin \mathbb{Q}$, there exists a $g_{n+1}$ such that
>
> + $g_{n+1} \in \mathbb{Q}$.
> + $|g_{n+1} - g| < 1/(n+1)$.
> + $(g_{n+1}-g)(g_{n+1}-g_n) < 0$. In other words, $g_{n+1}$ is strictly between $g$ and $g_n$.
>
> By the intermediate value theorem of sub-gradients, we can find $x_{n+1}$ with
>
> + $(x_{n+1} - x_n)(x_{n+1} - x) \leq 0$. In other words, $x_{n+1}$ is between $x$ and $x_n$.
> + $g_{n+1} \in \partial \varphi(x_{n+1})$.
>
> Now $g_n \to g$ and $\{ x_n \}$ is a monotone sequence bounded by $x_1$ and $x$. Therefore, we can define $x^\prime = \lim_{n \to \infty} x_n$. By the continuity of sub-gradients, we know that $g \in \partial \varphi (x^\prime)$, which means that $\varphi$ is linear between $x$ and $x^\prime$, i.e.
> $$
> \varphi(x^\prime) - \varphi(x) = g(x^\prime - x).
> $$
> On the other hand, there exists a sequence $r_n \uparrow 0$ such that
> $$
> b_n := \varphi(x_n) - g_n x_n + r_n \in \mathbb{Q}, \quad \forall n \in \mathbb{Z}_+.
> $$
> For each $n$, since $g_{n} \in \partial \varphi(x_{n})$ and $r_n \leq 0$, we have
> $$
> \varphi(y) - \varphi(x_n) \geq g_n (y - x_n) \geq g_n (y - x_n) + r_n, \quad \forall y \in \mathbb{R},
> $$
> which implies that $(g_n, b_n) \in S$. By the assumption at beginning, we have
> $$
> \varphi(x) - \varepsilon \geq g_n x + b_n = g_n x + [\varphi(x_n) - g_n x_n + r_n], \quad \forall n \in \mathbb{Z}_+.
> $$
> Letting $n \to \infty$, we obtain
> $$
> \varphi(x) - \varepsilon \geq \varphi(x^\prime) + g (x - x^\prime),
> $$
> which contradicts the observation that $\varphi$ is linear between $x$ and $x^\prime$.
>
> **Proof for Jensen’s inequality**
>
> If $\bigcup_{x \in \mathbb{R}} \partial \varphi (x)$ contains only one element, then $\varphi$ is linear and the result is trivial. Otherwise, for each $(a, b) \in S$, we have $\varphi(X) \geq aX + b$ and thus
> $$
> \mathbb{E}(\varphi(X)|\mathcal{F}) \geq a \mathbb{E}(X|\mathcal{F}) + b, \quad \text{a.s.}
> $$
> Since $S$ is countable, we have
> $$
> \mathbb{E}(\varphi(X)|\mathcal{F}) \geq a \mathbb{E}(X|\mathcal{F}) + b, \quad \forall (a, b) \in S, \quad \text{a.s.}
> $$
> and thus
> $$
> \mathbb{E}(\varphi(X)|\mathcal{F}) \geq \sup \big\{ a \mathbb{E}(X|\mathcal{F}) + b : (a,b) \in S \big \} = \varphi(\mathbb{E}(X|\mathcal{F})), \quad \text{a.s.}
> $$
