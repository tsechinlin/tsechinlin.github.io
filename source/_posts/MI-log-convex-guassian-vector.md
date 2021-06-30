---
title: Moment Inequalities for Log-convex Transformation of Gaussian Vectors
date: 2021-05-03 19:08:18
tags: 
  - Log-convex Functions
  - Guassian Distribution
categories: Moment Inequalities
mathjax: true
---

[Reference] Brascamp, Herm Jan, and Elliott H. Lieb. **On extensions of the Brunn-Minkowski and Prékopa-Leindler theorems, including inequalities for log concave functions, and with an application to the diffusion equation.** Inequalities. Springer, Berlin, Heidelberg, 2002. 441-464.

<!--more-->

## Preservation of Log-convexity

Let $f: \mathbb{R}^{n} \to [0, \infty)$ be a nonnegative function.

$f$ is said to be **logarithmically convex** (or **log-convex**) if for any $\mathbf{x}_1, \mathbf{x}_2 \in \mathbb{R}^{n}$ and $\lambda \in (0, 1)$,
$$
\begin{equation}
f( \lambda \mathbf{x}_1 + (1 - \lambda) \mathbf{x}_2) 
\leq f(\mathbf{x}_1)^{\lambda} f(\mathbf{x}_2)^{1 - \lambda}.
\end{equation}
$$

### Affine Transformation

Let $f: \mathbb{R}^{n} \to [0, \infty)$ be log-convex. For any $\mathbf{A} \in \mathbb{R}^{n \times k}$ and $\mathbf{b} \in \mathbb{R}^{k}$, define $g: \mathbb{R}^{k} \to [0, \infty)$ by
$$
g(\mathbf{y}) = f(\mathbf{A} \mathbf{y} + \mathbf{b}).
$$
Then $g$ is log-convex.

### Multiplication

Let $f,g : \mathbb{R}^{n} \to [0, \infty)$ be log-convex. Then $fg$ is log-convex.

### Addition

Let $f,g : \mathbb{R}^{n} \to [0, \infty)$ be log-convex. Then $f + g$ is log-convex.

> Fix $\lambda \in (0, 1)$. For any $u_1, u_2 > 0$, by concavity of logarithm, we have
> $$
> \ln (\lambda u_1 + (1 - \lambda) u_2) 
> \geq \lambda \ln u_1 + (1 - \lambda) \ln u_2 
> = \ln \left ( u_1^\lambda u_2^{1 - \lambda} \right ).
> $$
> In other words, $u_1^\lambda u_2^{1 - \lambda} \leq \lambda u_1 + (1 - \lambda) u_2$.
>
> Therefore, if $u_1, u_2, v_1, v_2 > 0$ are positive numbers, then
> $$
> \begin{align*}
> \left ( \frac{u_1}{u_1 + v_1} \right )^\lambda \left ( \frac{u_2}{u_2 + v_2} \right )^{1 - \lambda} & \leq \lambda \frac{u_1}{u_1 + v_1} + (1 - \lambda) \frac{u_2}{u_2 + v_2}, \\
> \left ( \frac{v_1}{u_1 + v_1} \right )^\lambda \left ( \frac{v_2}{u_2 + v_2} \right )^{1 - \lambda} & \leq \lambda \frac{v_1}{u_1 + v_1} + (1 - \lambda) \frac{v_2}{u_2 + v_2}.
> \end{align*}
> $$
> It follows that
> $$
> \begin{equation}
> u_1^\lambda u_2^{1 - \lambda} + v_1^\lambda v_2^{1 - \lambda} 
> \leq (u_1 + v_1)^\lambda (u_2 + v_2)^{1 - \lambda}.
> \end{equation}
> $$
> Note that (2) is still true when any of $u_1, u_2, v_1, v_2$ becomes $0$.
>
> Hence, for any $\mathbf{x}_1, \mathbf{x}_2 \in \mathbb{R}^{n}$,
> $$
> \begin{align*}
> (f + g)( \lambda \mathbf{x}_1 + (1 - \lambda) \mathbf{x}_2) 
> & = f( \lambda \mathbf{x}_1 + (1 - \lambda) \mathbf{x}_2)  + g( \lambda \mathbf{x}_1 + (1 - \lambda) \mathbf{x}_2) \\
> & \leq f(\mathbf{x}_1)^{\lambda} f(\mathbf{x}_2)^{1 - \lambda} + g(\mathbf{x}_1)^{\lambda} g(\mathbf{x}_2)^{1 - \lambda} \\
> & \leq \big [ f(\mathbf{x}_1) + g(\mathbf{x}_1) \big ]^\lambda \big [ f(\mathbf{x}_2) + g(\mathbf{x}_2) \big ]^{1 - \lambda}
> = (f + g)(\mathbf{x}_1)^\lambda \cdot (f + g)(\mathbf{x}_2)^{1 - \lambda},
> \end{align*}
> $$
> from which we can conclude the log-convexity of $f + g$.

### Marginalization

Let $f: \mathbb{R}^{n+k} \to [0, \infty)$ be nonnegative with $f \in L^{1} (\mathbb{R}^{n+k})$. For each $\mathbf{x} \in \mathbb{R}^{n}$, let
$$
g(\mathbf{x}) := \int_{\mathbb{R}^k} f(\mathbf{x}, \mathbf{y}) \mathrm{d} \mathbf{y}.
$$
If $f(\mathbf{x}, \mathbf{y})$ is log-convex on $\mathbb{R}^{n}$ for each fixed $\mathbf{y} \in \mathbb{R}^k$, then $g$ is log-convex.

> Let $D = \{ \mathbf{x} \in \mathbb{R}^{n}: g(\mathbf{x}) < \infty \}$.
>
> For any $\mathbf{x}_1, \mathbf{x}_2 \in \mathbb{R}^{n}$ and $\lambda \in (0, 1)$, by Hölder's inequality, we have
> $$
> \begin{align*}
> g( \lambda \mathbf{x}_1 + (1 - \lambda) \mathbf{x}_2) 
> & = \int_{\mathbb{R}^k} f (\lambda \mathbf{x}_1 + (1 - \lambda) \mathbf{x}_2, \mathbf{y}) \mathrm{d} \mathbf{y}
> \leq \int_{\mathbb{R}^k} f (\mathbf{x}_1, \mathbf{y})^{\lambda} f(\mathbf{x}_2, \mathbf{y})^{1 - \lambda} \mathrm{d} \mathbf{y} \\
> & \leq \left [ \int_{\mathbb{R}^k} f (\mathbf{x}_1, \mathbf{y}) \mathrm{d} \mathbf{y} \right ]^{\lambda} \left [ \int_{\mathbb{R}^m} f (\mathbf{x}_2, \mathbf{y}) \mathrm{d} \mathbf{y} \right ]^{1 - \lambda} = g(\mathbf{x}_1)^{\lambda} g(\mathbf{x}_2)^{1 - \lambda}.
> \end{align*}
> $$
> Hence, to conclude the log-convex of $g$, it remains to show that $D = \mathbb{R}^{n}$.
>
> But this is trivial since $D$ is convex by the inequality above and $\mathbb{R}^{n} \backslash D$ is a null set by $f \in L^{1} (\mathbb{R}^{n+k})$.

## Log-convex Transformation of Gaussian Vectors

### Log-convexity of Conditional Expectation

Assume that $(\mathbf{X}, \mathbf{Y}) \sim \mathrm{N} (\mathbf{m}, \boldsymbol{\Sigma})$ is a $(n+k)$-dimensional gaussian random vector, with $\boldsymbol{\Sigma}$ positive definite.

Let $f: \mathbb{R}^{n+k} \to [0, \infty)$ be log-convex with $\mathbb{E} f(\mathbf{X}, \mathbf{Y}) < \infty$. Define $g: \mathbb{R}^{n} \to [0, \infty)$ by
$$
g(\mathbf{x}) := \mathbb{E} ( f(\mathbf{X}, \mathbf{Y}) | \mathbf{X} = \mathbf{x} ).
$$

Then, $g$ is log-convex.

> Write
> $$
> \mathbf{m} = \begin{bmatrix}
> \mathbf{m}_{\mathbf{X}} \\
> \mathbf{m}_{\mathbf{Y}}
> \end{bmatrix}
> \quad \text{ and } \quad 
> \boldsymbol{\Sigma} 
> = \begin{bmatrix}
> \boldsymbol{\Sigma}_{\mathbf{X} \mathbf{X}} & \boldsymbol{\Sigma}_{\mathbf{X} \mathbf{Y}} \\
> \boldsymbol{\Sigma}_{\mathbf{Y} \mathbf{X}} & \boldsymbol{\Sigma}_{\mathbf{Y} \mathbf{Y}}
> \end{bmatrix}.
> $$
> It is well known that $( \mathbf{Y} \big| \mathbf{X} = \mathbf{x} ) \sim \mathrm{N} ( \boldsymbol{\mu}_{\mathbf{Y} |\mathbf{X} = \mathbf{x}} , \boldsymbol{\Sigma}_{\mathbf{Y} \mathbf{Y} | \mathbf{X}}  )$, with
> $$
> \mathbf{m}_{\mathbf{Y} |\mathbf{X} = \mathbf{x}} :=
> \mathbf{m}_{\mathbf{Y}} + \boldsymbol{\Sigma}_{\mathbf{Y} \mathbf{X}} \boldsymbol{\Sigma}_{\mathbf{X} \mathbf{X}}^{-1} (\mathbf{x} - \mathbf{m}_{\mathbf{X}})
> \quad \text{ and } \quad 
> \boldsymbol{\Sigma}_{\mathbf{Y} \mathbf{Y} | \mathbf{X}} := \boldsymbol{\Sigma}_{\mathbf{Y} \mathbf{Y}} - \boldsymbol{\Sigma}_{\mathbf{Y} \mathbf{X}} \boldsymbol{\Sigma}_{\mathbf{X} \mathbf{X}}^{-1} \boldsymbol{\Sigma}_{\mathbf{X} \mathbf{Y}}.
> $$
> Therefore, we can write
> $$
> g(\mathbf{x}) 
> = \mathbb{E} ( f(\mathbf{X}, \mathbf{Y}) | \mathbf{X} = \mathbf{x} ) 
> = C \int_{\mathbb{R}^k} f ( \mathbf{x}, \mathbf{y} + \mathbf{m}_{\mathbf{Y} |\mathbf{X} = \mathbf{x}} ) \exp \big ( - \langle \boldsymbol{\Sigma}_{\mathbf{Y} \mathbf{Y} | \mathbf{X}}^{-1} \mathbf{y}, \mathbf{y} \rangle /2 \big ) \mathrm{d} \mathbf{y}
> \triangleq \int_{\mathbb{R}^m} F (\mathbf{x}, \mathbf{y}) \mathrm{d} \mathbf{y}
> $$
> where $C = {(2\pi)^{-k/2} | \boldsymbol{\Sigma}_{\mathbf{Y} \mathbf{Y} | \mathbf{X}} |^{-1/2}}$.
>
> Note that the transformation $(\mathbf{x}, \mathbf{y}) \mapsto ( \mathbf{x}, \mathbf{y} + \mathbf{m}_{\mathbf{Y} |\mathbf{X} = \mathbf{x}} )$ is affine. 
>
> Hence, for each fixed $\mathbf{y} \in \mathbb{R}^k$, the function $F (\mathbf{x}, \mathbf{y})$ is log-convex on $\mathbb{R}^{n}$, from which we can conclude the log-convexity of $g$.

### Moment Inequalities (One-dimensional)

Assume that $X \sim \mathrm{N} (0, \sigma^2)$ is a normal random variable, where $\sigma^2 > 0$.

Let $f: \mathbb{R}^{n} \to [0, \infty)$ be log-convex and assume that
$$
\mathbb{E} f(X) = \int_{-\infty}^{\infty} f (x) \phi (x) \mathrm{d} x = 1,
\quad \text{ where }
\phi(x) = \frac{1}{\sqrt{2\pi}} \exp \left ( - {x^2} / 2 \right ).
$$
Let $\mu$ denote the probability measure on $\mathbb{R}$ with density function $f(x) \phi(x)$. 

Then, for arbitrary $p > 0$ and $a \in \mathbb{R}$,
$$
\begin{equation}
\mathbb{E}_{\mu} | X - a |^p \geq \mathbb{E} | X |^p.
\end{equation}
$$

> Without loss of generality, we can assume that $\sigma = 1$.
>
> By transforming the variables, we get
>
> $$
> \begin{align*}
> \mathbb{E}_{\mu} | X - a |^p 
> & = \mathbb{E} \big [ | X - a |^p \cdot f(X) \big ]
> = \int_{-\infty}^{\infty} | x - a |^p f(x) \phi(x) \mathrm{d} x \\
> & = \int_{-\infty}^{\infty} | x |^p f(x + a) \exp ( -ax - a^2/2 ) \phi(x) \mathrm{d} x
> \triangleq \mathbb{E} \big [ | X |^p \cdot g(X) \big ],
> \end{align*}
> $$
> where
> $$
> g(x) := f(x + a) \exp ( -ax - a^2/2 ).
> $$
> Note that we also have
> $$
> 1 = \mathbb{E} f(X) = \int_{-\infty}^{\infty} f (x) \phi (x) \mathrm{d} x
> = \int_{-\infty}^{\infty} f(x + a) \exp ( -ax - a^2/2 ) \phi(x) \mathrm{d} x
> = \mathbb{E} g(X).
> $$
> Since $-X$ has the same distribution as $X$,
> $$
> \mathbb{E} \big [ | X |^p \cdot g(X) \big ] = \mathbb{E} \big [ | X |^p \cdot g(-X) \big ]
> \quad \text{ and } \quad
> \mathbb{E} g(X) = \mathbb{E} g(-X).
> $$
> Letting $h(x) := g(x) /2 + g(-x) /2$ for $x \in \mathbb{R}$, it follows that
> $$
> \mathbb{E}_{\mu} | X - a |^p = \mathbb{E} \big [ | X |^p \cdot h(X) \big ]
> \quad \text{ and } \quad
> \mathbb{E} h(X) = 1.
> $$
>
> By log-convexity of $f$ and $\exp ( -ax - a^2/2 )$, we know that $g$ and $h$ are log-convex. 
>
> Moreover, $h$ is even. Thus we can write
>
> $$
> \begin{align*}
> \mathbb{E}_{\mu} | X - a |^p 
> & = \mathbb{E} \big [ | X |^p \cdot h(X) \big ]
> = 4 \int_{0}^{\infty} x^p h(x) \phi(x) \mathrm{d} x \int_{0}^{\infty} \phi(y) \mathrm{d} y \\
> & = 2 \int_{0}^{\infty} \int_{0}^{\infty} \big [ x^p h(x) + y^p h(y) \big ] \phi(x) \phi(y) \mathrm{d} x \mathrm{d} y
> \end{align*}
> $$
>
> and
> $$
> \begin{align*}
> \mathbb{E} | X |^p 
> & = \mathbb{E} | X |^p \cdot \mathbb{E} h(X)
> = 4 \int_{0}^{\infty} x^p \phi(x) \mathrm{d} x \int_{0}^{\infty} h(y) \phi(y) \mathrm{d} y \\
> & = 2 \int_{0}^{\infty} \int_{0}^{\infty} \big [ x^p h(y) + y^p h(x) \big ] \phi(x) \phi(y) \mathrm{d} x \mathrm{d} y.
> \end{align*}
> $$
> In other words,
> $$
> \mathbb{E}_{\mu} | X - a |^p - \mathbb{E} | X |^p 
> = \int_{0}^{\infty} \int_{0}^{\infty} ( x^p - y^p ) \big [ h(x) - h(y) \big ] \phi(x) \phi(y) \mathrm{d} x \mathrm{d} y
> $$
>
> Therefore, (3) follows by noting that $x^p$ and $h(x)$ are both non-decreasing on $[0, \infty)$.
>
> Here, $h(x)$ is non-decreasing on $[0, \infty)$ since it is even and log-convex.

### Moment Inequalities (Multi-dimensional)

Assume that $\mathbf{X} \sim \mathrm{N} (\mathbf{0}, \boldsymbol{\Sigma})$ is a $n$-dimensional gaussian random vector, where $\boldsymbol{\Sigma} \succ \mathbf{0}$.

Let $f: \mathbb{R}^{n} \to [0, \infty)$ be log-convex and assume that
$$
\mathbb{E} f(\mathbf{X}) = \int_{-\infty}^{\infty} f (\mathbf{x}) \phi (\mathbf{x}) \mathrm{d} \mathbf{x} = 1,
\quad \text{ where }
\phi(\mathbf{x}) = {(2\pi)^{-n/2} | \boldsymbol{\Sigma} |^{-1/2}} \exp \big ( - \langle \boldsymbol{\Sigma}^{-1} \mathbf{x}, \mathbf{x} \rangle / 2 \big ).
$$
Let $\mu$ denote the probability measure on $\mathbb{R}^n$ with density function $f(\mathbf{x}) \phi(\mathbf{x})$. 

Then, for arbitrary $p > 0$, $a \in \mathbb{R}$ and $\boldsymbol{\alpha} \in \mathbb{R}^n$,
$$
\mathbb{E}_{\mu} | \langle \boldsymbol{\alpha}, \mathbf{X} \rangle - a |^p
\geq \mathbb{E} | \langle \boldsymbol{\alpha}, \mathbf{X} \rangle |^p.
$$
In particular, if we let
$$
\boldsymbol{\Sigma}_{\mu} := \operatorname{Cov}_{\mu} (\mathbf{X}, \mathbf{X})
= \mathbb{E}_{\mu} (\mathbf{X} \mathbf{X}^\top) - \mathbf{m}_{\mu}\mathbf{m}_{\mu}^\top
\quad \text{ where }
\mathbf{m}_{\mu} :=  \mathbb{E}_{\mu}\mathbf{X},
$$
Then $\boldsymbol{\Sigma}_{\mu} \succeq \boldsymbol{\Sigma}$.

> **[Part 1]** Without loss of generality, assume that $\| \boldsymbol{\alpha} \|_2 = 1$.
>
> Let $\mathbf{A} \in \mathbb{R}^{n \times n}$ be the orthogonal matrix with $\mathbf{A}^\top = [\boldsymbol{\alpha}_1, \cdots, \boldsymbol{\alpha}_n]$ and $\boldsymbol{\alpha}_1 = \boldsymbol{\alpha}$.
>
> Let $\mathbf{Y} = \mathbf{A} \mathbf{X}$. Then $\mathbf{Y} \sim \mathrm{N} (\mathbf{0}, \mathbf{A} \boldsymbol{\Sigma} \mathbf{A}^*)$ and $Y_1 = \langle \boldsymbol{\alpha}, \mathbf{X} \rangle$. Therefore, we can write
>
> $$
> \mathbb{E}_{\mu} | \langle \boldsymbol{\alpha}, \mathbf{X} \rangle - a |^p
> = \mathbb{E} \big [ | \langle \boldsymbol{\alpha}, \mathbf{X} \rangle - a |^p \cdot f(\mathbf{X}) \big ] 
> = \mathbb{E} \big [ | Y_1 - a |^p \cdot f(\mathbf{A}^\top \mathbf{Y}) \big ]
> = \mathbb{E} \big [ | Y_1 - a |^p \cdot g(Y_1) \big ],
> $$
> where for $y_1 \in \mathbb{R}$,
> $$
> g(y_1) := \mathbb{E} ( f(\mathbf{A}^\top \mathbf{Y}) | Y_1 = y_1 ).
> $$
>
> Since $\mathbb{E} f(\mathbf{A}^\top \mathbf{Y}) = \mathbb{E} f(\mathbf{X}) < \infty$, by normality of $\mathbf{Y}$ and log-convexity of $f \circ \mathbf{A}^\top$ we know that $g$ is log-convex.
>
> Therefore, by (3) we can conclude that
> $$
> \mathbb{E}_{\mu} | \langle \boldsymbol{\alpha}, \mathbf{X} \rangle - a |^p
> = \mathbb{E} \big [ | Y_1 - a |^p \cdot g(Y_1) \big ]
> \geq \mathbb{E} | Y_1 |^p =  \mathbb{E} | \langle \boldsymbol{\alpha}, \mathbf{X} \rangle |^p.
> $$
> **[Part 2]** For any $\boldsymbol{\alpha} \in \mathbb{R}^n$, by part 1 we have
> $$
> \begin{align*}
> \langle \boldsymbol{\Sigma}_{\mu} \boldsymbol{\alpha}, \boldsymbol{\alpha} \rangle
> = \operatorname{Var}_{\mu} (\langle \boldsymbol{\alpha}, \mathbf{X} \rangle)
> & = \mathbb{E}_{\mu} | \langle \boldsymbol{\alpha}, \mathbf{X} \rangle - \langle \boldsymbol{\alpha}, \mathbf{m}_{\mu} \rangle |^2 \\
> &\geq \mathbb{E} | \langle \boldsymbol{\alpha}, \mathbf{X} \rangle |^2
> = \operatorname{Var} (\langle \boldsymbol{\alpha}, \mathbf{X} \rangle)
> = \langle \boldsymbol{\Sigma} \boldsymbol{\alpha}, \boldsymbol{\alpha} \rangle.
> \end{align*}
> $$
