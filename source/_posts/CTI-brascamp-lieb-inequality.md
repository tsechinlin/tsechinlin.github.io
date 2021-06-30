---
title: Brascamp–Lieb Inequality
date: 2021-04-30 15:00:34
tags: 
  - Convex Functions
  - Subguassian Density
categories: Concentration Inequalities
mathjax: true
---

Brascamp–Lieb Inequality

<!--more-->

Consider a probability measure $\mu$ on $\mathbb{R}^n$ with density $\exp(-\varphi(\mathbf{z}))$ w.r.t. Lebesgue measure, where $\varphi \in C^2(\mathbb{R}^n)$ is strictly convex.

Then, for every $f \in C_1(\mathbb{R}^n)$ with $\mathbb{E}_\mu (f^2) < \infty$, it holds that
$$
\operatorname{Var}_{\mu} (f) 
\leq \mathbb{E}_\mu \left \langle \nabla f, \mathbf{H}_\varphi^{-1} \nabla f \right \rangle,
$$
where $\mathbf{H}_\varphi = \operatorname{Hess} \varphi$ is the Hessian matrix of $\varphi$.

---

**[Assumption 1]** Assume that $f$ is nonnegative with $f \in C_c^\infty(\mathbb{R}^n)$, i.e. $f$ vanishes outside some compact set $K \subset \mathbb{R}^n$.

**[Assumption 2]** Assume that $\mathbf{H}_\varphi \geq \rho \mathbf{I}_n$ for some $\rho > 0$.

By assumption 1, there exists some $M > 0$ such that for any $\mathbf{z} \in \mathbb{R}^n$,
$$
\left | f(\mathbf{z}) \right | \leq M, 
\quad
\left \| \nabla f(\mathbf{z}) \right \|_2 \leq M,
\quad \text{ and } \quad
\left \| \mathbf{H}_f(\mathbf{z}) \right \|_{\mathrm{op}} \leq M.
$$

---

For each $\delta \in (0, 1)$ and $\mathbf{z} \in \mathbb{R}^n$, let
$$
f_{\delta} (\mathbf{z}) = \sup_{\mathbf{h} \in \mathbb{R}^n} \psi_{\delta} (\mathbf{z}, \mathbf{h}) :=
\sup_{\mathbf{h} \in \mathbb{R}^n} \left [ \delta f(\mathbf{z} + \mathbf{h}) - \frac{1}{2} \varphi(\mathbf{z} + \mathbf{h}) - \frac{1}{2} \varphi(\mathbf{z} - \mathbf{h}) + \varphi(\mathbf{z}) \right ].
$$


Let $\delta \in (0, 1)$ and $\mathbf{z} \in \mathbb{R}^n$ be fixed. Then, by convexity of $\varphi$, for any $\mathbf{h} \in \mathbb{R}^n$ we have
$$
\psi_{\delta} (\mathbf{z}, \mathbf{h}) \leq \delta f(\mathbf{z} + \mathbf{h}) \leq \delta M.
$$
This implies that $f_{\delta} (\mathbf{z})$ is finite. In addition, by nonnegativity of $f$ we have
$$
f_{\delta} (\mathbf{z}) \geq \psi_{\delta} (\mathbf{z}, \mathbf{0}) = \delta f(\mathbf{z}) \geq 0.
$$

That is to say, $f_{\delta} (\mathbf{z}) \in [0, \infty)$. 

---

Moreover, we claim that there exists some $\mathbf{h}_{\delta} \in \mathbb{R}^n$, depending on $\delta$ and $\mathbf{z}$, such that $f_{\delta} (\mathbf{z}) = \psi_{\delta} (\mathbf{z}, \mathbf{h}_{\delta})$.

+ If $f_{\delta} (\mathbf{z}) = 0$, then
    $$
    0 = f_{\delta} (\mathbf{z}) \geq \psi_{\delta} (\mathbf{z}, \mathbf{0}) = \delta f(\mathbf{z}) \geq 0.
    $$
    In other words, we have $f(\mathbf{z}) = 0$. Hence, we can simply let $\mathbf{h}_{\delta} = \mathbf{0}$.

+ If $f_{\delta} (\mathbf{z}) > 0$, then there exists a sequence $\{ \mathbf{h}^{(k)} \} \subset \mathbb{R}^n$ such that $\psi_{\delta} (\mathbf{z}, \mathbf{h}^{(k)}) \to f_{\delta} (\mathbf{z})$.

    For sufficiently large $n$, we have $\psi_{\delta} (\mathbf{z}, \mathbf{h}^{(k)}) > 0$, which implies
    $$
    \delta f(\mathbf{z} + \mathbf{h}^{(k)}) \geq \psi_{\delta} (\mathbf{z}, \mathbf{h}^{(k)}) > 0.
    $$
    Since $f$ vanishes outside $K$, we have $\{ \mathbf{z} + \mathbf{h}^{(k)} \} \subset K$.

    By compactness of $K$ and continuity of $\psi_{\delta}$, there exists some $\mathbf{h}_{\delta} \in K - \mathbf{z}$ such that $\psi_{\delta} (\mathbf{z}, \mathbf{h}_\delta) = f_{\delta} (\mathbf{z})$.

---

Now, by optimality of $\mathbf{h}_\delta$, we have
$$
2 \delta \nabla f(\mathbf{z} + \mathbf{h}_{\delta}) = \nabla \varphi(\mathbf{z} + \mathbf{h}_{\delta}) - \nabla \varphi(\mathbf{z} - \mathbf{h}_{\delta}).
$$

+ For the LHS,
    $$
    \big \langle 2 \delta \nabla f(\mathbf{z} + \mathbf{h}_{\delta}),  \mathbf{h}_{\delta} \big \rangle 
    \leq 2 \delta \| \nabla f(\mathbf{z} + \mathbf{h}_{\delta}) \|_2 \| \mathbf{h}_{\delta} \|_2 
    \leq 2 M \delta \| \mathbf{h}_{\delta} \|_2.
    $$

+ For the RHS, by the mean value theorem and assumption 2 we have
    $$
    \big \langle \nabla \varphi(\mathbf{z} + \mathbf{h}_{\delta}) - \nabla \varphi(\mathbf{z} - \mathbf{h}_{\delta}),  \mathbf{h}_{\delta} \big \rangle  
    = \big \langle 2 \mathbf{H}_\varphi(\mathbf{z} + t_{\delta} \mathbf{h}_{\delta}) \mathbf{h}_{\delta}, \mathbf{h}_{\delta} \big \rangle  
    \geq 2 \rho \| \mathbf{h}_{\delta} \|_2^2,
    $$
    where $t_{\delta} \in (-1, 1)$ depends on both $\delta$ and $\mathbf{z}$.

Therefore, we have $\| \mathbf{h}_{\delta} \|_2 \leq M \delta / \rho$.

---

Let $K^\prime \subset \mathbb{R}^n$ be the compact set given by
$$
K^\prime := \{ \mathbf{z} \in \mathbb{R}^n : d (\mathbf{z}, K) \leq 2 M / \rho \}.
$$
Note that $\mathbf{H}_\varphi$ is uniformly continuous on $K^\prime$. Hence, for $\delta \in (0, 1)$ we can let
$$
c(\delta) := \sup \left \{ \big \| \mathbf{H}_\varphi (\mathbf{z}_1) - \mathbf{H}_\varphi (\mathbf{z}_2) \big \|_{\mathrm{op}} : \mathbf{z}_1, \mathbf{z}_2 \in K^\prime \text{ and } \| \mathbf{z}_1 - \mathbf{z}_2 \|_2 \leq \delta \right \}.
$$
It follows that $c(\delta) \downarrow 0$ as $\delta \downarrow 0$.

---

Consider again the both sides of optimality condition (&&&&). 

If $d (\mathbf{z}, K) > M / \rho$, then for any $\delta \in (0, 1)$ we have $\mathbf{z} + \mathbf{h}_{\delta} \notin K$. It follows that
$$
2 \mathbf{H}_\varphi(\mathbf{z} + t_{\delta} \mathbf{h}_{\delta}) \mathbf{h}_{\delta}
= \nabla \varphi(\mathbf{z} + \mathbf{h}_{\delta}) - \nabla \varphi(\mathbf{z} - \mathbf{h}_{\delta})
= 2 \delta \nabla f(\mathbf{z} + \mathbf{h}_{\delta}) = \mathbf{0}.
$$
Since $\mathbf{H}_\varphi \geq \rho \mathbf{I}_n$, we must have $\mathbf{h}_{\delta} = \mathbf{0}$. In this case, it holds trivially that
$$
\delta \nabla f(\mathbf{z}) = \mathbf{H}_\varphi(\mathbf{z}) \mathbf{h}_{\delta}.
$$
Now assume that $d (\mathbf{z}, K) \leq M / \rho$.

+ For the LHS, by the mean value theorem again, there exists some $s_\delta \in (0,1)$, depending on $\delta$ and $\mathbf{z}$, such that
    $$
    2 \delta \nabla f(\mathbf{z} + \mathbf{h}_{\delta})
    = 2 \delta \nabla f(\mathbf{z}) + 2 \delta \mathbf{H}_f(\mathbf{z} + s_\delta \mathbf{h}_{\delta}) \mathbf{h}_{\delta}.
    $$
    Here
    $$
    \big \| \delta \mathbf{H}_f(\mathbf{z} + s_\delta \mathbf{h}_{\delta}) \mathbf{h}_{\delta} \big \|_2 
    \leq \delta \big \| \mathbf{H}_f(\mathbf{z} + s_\delta \mathbf{h}_{\delta}) \big \|_{\mathrm{op}} \left \| \mathbf{h}_{\delta} \right \|_2
    \leq M^2 \delta^2 / \rho.
    $$

+ For the RHS, write
    $$
    \nabla \varphi(\mathbf{z} + \mathbf{h}_{\delta}) - \nabla \varphi(\mathbf{z} - \mathbf{h}_{\delta}) 
    = 2 \mathbf{H}_\varphi(\mathbf{z} + t_{\delta} \mathbf{h}_{\delta}) \mathbf{h}_{\delta}
    = 2 \mathbf{H}_\varphi(\mathbf{z}) \mathbf{h}_{\delta} + 2 \big [ \mathbf{H}_\varphi(\mathbf{z} + t_{\delta} \mathbf{h}_{\delta}) \mathbf{h}_{\delta} - \mathbf{H}_\varphi (\mathbf{z}) \mathbf{h}_{\delta} \big ].
    $$
    Note that we have assume $d (\mathbf{z}, K) \leq M / \rho$. 

    In this case, for any $\delta \in (0, 1)$ we have $\mathbf{z}, \mathbf{z} + t_{\delta} \mathbf{h}_{\delta} \in K^\prime$ and thus
    $$
    \big \| \mathbf{H}_\varphi(\mathbf{z} + t_{\delta} \mathbf{h}_{\delta}) \mathbf{h}_{\delta} - \mathbf{H}_\varphi (\mathbf{z}) \mathbf{h}_{\delta} \big \|_2
    \leq \big \| \mathbf{H}_\varphi(\mathbf{z} + t_{\delta} \mathbf{h}_{\delta}) - \mathbf{H}_\varphi (\mathbf{z}) \big \|_{\mathrm{op}} \left \| \mathbf{h}_{\delta} \right \|_2
    \leq (M \delta / \rho) \cdot c (M \delta / \rho).
    $$

Combining the both parts, we get
$$
\big \| \delta \nabla f(\mathbf{z}) - \mathbf{H}_\varphi(\mathbf{z}) \mathbf{h}_{\delta}\big \|_2 \leq M^2 \delta^2 / \rho + (M \delta / \rho) \cdot c (M \delta / \rho).
$$
Note that this inequality still holds when $d (\mathbf{z}, K) \leq M / \rho$. This means that we can write
$$
\delta \nabla f(\mathbf{z}) 
= \mathbf{H}_\varphi(\mathbf{z}) \mathbf{h}_{\delta} + \mathbf{o}(\delta),
$$
where $\mathbf{o}(\delta) / \delta$ converges to $\mathbf{0}$ in $\ell^2$ as $\delta \downarrow 0$, uniformly in $\mathbf{z} \in \mathbb{R}^n$.

Finally, by $\mathbf{H}_\varphi \geq \rho \mathbf{I}_n$, we have $\lVert \mathbf{H}_\varphi^{-1} \rVert_{\mathrm{op}} \leq 1 / \rho$ and thus
$$
\begin{equation}
\mathbf{h}_{\delta} = \delta \mathbf{H}_\varphi(\mathbf{z})^{-1} \nabla f(\mathbf{z}) + \mathbf{o}(\delta).
\end{equation}
$$

---

The argument above can be apply to $\varphi(\mathbf{z} + \mathbf{h}_\delta)$ and $\varphi(\mathbf{z} - \mathbf{h}_\delta)$.

For example, let $r_\delta \in (0, 1)$ such that
$$
\varphi(\mathbf{z} + \mathbf{h}_\delta) 
= \varphi(\mathbf{z}) + \langle \nabla \varphi(\mathbf{z}), \mathbf{h}_\delta \rangle + \frac{1}{2} \big \langle \mathbf{H}_\varphi(\mathbf{z} + r_\delta \mathbf{h}_\delta) \mathbf{h}_\delta, \mathbf{h}_\delta \big \rangle
$$
Then for all $\mathbf{z}$ with $d (\mathbf{z}, K) \leq M / \rho$, we have $\mathbf{z} + r_\delta \mathbf{h}_\delta \in K^\prime$ and thus
$$
\big \langle \mathbf{H}_\varphi(\mathbf{z} + r_\delta \mathbf{h}_\delta) \mathbf{h}_\delta, \mathbf{h}_\delta \big \rangle - \big \langle \mathbf{H}_\varphi(\mathbf{z}) \mathbf{h}_\delta, \mathbf{h}_\delta \big \rangle
\leq  \big \| \mathbf{H}_\varphi(\mathbf{z} + r_{\delta} \mathbf{h}_{\delta}) - \mathbf{H}_\varphi (\mathbf{z}) \big \|_{\mathrm{op}} \left \| \mathbf{h}_{\delta} \right \|_2^2
\leq (M \delta / \rho)^2 \cdot c (M \delta / \rho).
$$
The inequality also holds if $d (\mathbf{z}, K) > M / \rho$, since we have $\mathbf{h}_\delta = \mathbf{0}$ in this case. 

In other words, it holds that
$$
\varphi(\mathbf{z} + \mathbf{h}_\delta) 
= \varphi(\mathbf{z}) + \langle \nabla \varphi(\mathbf{z}), \mathbf{h}_\delta \rangle + \frac{1}{2} \big \langle \mathbf{H}_\varphi(\mathbf{z}) \mathbf{h}_\delta, \mathbf{h}_\delta \big \rangle + o(\delta^2).
$$
where $o(\delta) / \delta$ converges to $\mathbf{0}$ as $\delta \downarrow 0$, uniformly in $\mathbf{z} \in \mathbb{R}^n$. Similarly,
$$
\varphi(\mathbf{z} - \mathbf{h}_\delta) 
= \varphi(\mathbf{z}) - \langle \nabla \varphi(\mathbf{z}), \mathbf{h}_\delta \rangle + \frac{1}{2} \big \langle \mathbf{H}_\varphi(\mathbf{z}) \mathbf{h}_\delta, \mathbf{h}_\delta \big \rangle + o(\delta^2).
$$
By the two equality above, we have
$$
\begin{equation}
\varphi(\mathbf{z} + \mathbf{h}_\delta) + \varphi(\mathbf{z} - \mathbf{h}_\delta)  
= 2 \varphi(\mathbf{z}) + \big \langle \mathbf{H}_\varphi(\mathbf{z}) \mathbf{h}_\delta, \mathbf{h}_\delta \big \rangle + o(\delta^2).
\end{equation}
$$

---

Now, using (&&&&), it follows that
$$
\begin{align*}
f_{\delta} (\mathbf{z}) 
& = \psi_{\delta} (\mathbf{z}, \mathbf{h}_{\delta}) = \delta f(\mathbf{z} + \mathbf{h}_\delta) - \frac{1}{2} \varphi(\mathbf{z} + \mathbf{h}_\delta) - \frac{1}{2} \varphi(\mathbf{z} - \mathbf{h}_\delta) + \varphi(\mathbf{z}) \\
& = \delta f(\mathbf{z}) + \delta \left \langle \nabla f(\mathbf{z}), \mathbf{h}_{\delta} \right \rangle - \frac{1}{2} \big \langle \mathbf{H}_\varphi(\mathbf{z}) \mathbf{h}_{\delta}, \mathbf{h}_{\delta} \big \rangle + o(\delta^2)
\end{align*}
$$

+ For the second term, using (&&&&), we get
    $$
    \begin{align*}
    \delta \big \langle \nabla f(\mathbf{z}), \mathbf{h}_{\delta} \big \rangle 
    & = \delta \left \langle \nabla f(\mathbf{z}), \delta \mathbf{H}_\varphi(\mathbf{z})^{-1} \nabla f(\mathbf{z}) + \mathbf{o}(\delta) \right \rangle \\
    & = \delta^2 \left \langle \nabla f(\mathbf{z}), \mathbf{H}_\varphi(\mathbf{z})^{-1} \nabla f(\mathbf{z}) \right \rangle  + \delta \left \langle \nabla f(\mathbf{z}), \mathbf{o}(\delta) \right \rangle \\
    & = \delta^2 \big \langle \nabla f(\mathbf{z}), \mathbf{H}_\varphi(\mathbf{z})^{-1} \nabla f(\mathbf{z}) \big \rangle + o(\delta^2)
    \end{align*}
    $$
    where the last equality follows from the fact that $\lVert \nabla f(\mathbf{z}) \rVert_2$ is uniformly bounded by $M$. 

+ As for the second term, note that we have (&&&&) and (&&&&). Hence,
    $$
    \begin{align*}
    \big \langle \mathbf{H}_\varphi(\mathbf{z}) \mathbf{h}_{\delta}, \mathbf{h}_{\delta} \big \rangle
    & = \big \langle \delta \nabla f(\mathbf{z}) + \mathbf{o}(\delta), \delta \mathbf{H}_\varphi(\mathbf{z})^{-1} \nabla f(\mathbf{z}) + \mathbf{o}(\delta) \big \rangle \\
    & = \delta^2 \big \langle \nabla f(\mathbf{z}), \mathbf{H}_\varphi(\mathbf{z})^{-1} \nabla f(\mathbf{z}) \big \rangle 
    + \delta \left \langle \nabla f(\mathbf{z}), \mathbf{o}(\delta) \right \rangle 
    + \delta \left \langle \mathbf{o}(\delta), \mathbf{H}_\varphi(\mathbf{z})^{-1} \nabla f(\mathbf{z}) \right \rangle 
    + \left \langle \mathbf{o}(\delta), \mathbf{o}(\delta) \right \rangle \\
    & = \delta^2 \big \langle \nabla f(\mathbf{z}), \mathbf{H}_\varphi(\mathbf{z})^{-1} \nabla f(\mathbf{z}) \big \rangle + {o}(\delta^2).
    \end{align*}
    $$
    Again, it relies on the fact that $\lVert \nabla f(\mathbf{z}) \rVert_2$ and $\lVert \mathbf{H}_\varphi^{-1} \rVert_{\mathrm{op}}$ are uniformly bounded.

In conclusion, we have
$$
\begin{equation}
f_{\delta} = \delta f + \frac{\delta^2}{2} \big \langle \nabla f, \mathbf{H}_\varphi^{-1} \nabla f \big \rangle + o(\delta^2).
\end{equation}
$$

---


For each $\delta > 0$, let $u_{\delta}, v_{\delta}, w_{\delta}$ be functions on $\mathbb{R}^n$ given by
$$
u_{\delta} (\mathbf{x}) = \exp \left [ \frac{\delta}{2} f (\mathbf{x}) - \varphi(\mathbf{x}) \right ],
\quad
v_{\delta} (\mathbf{y}) = \exp \big [ - \varphi(\mathbf{y}) \big ]
\quad \text{ and } \quad
w_{\delta} (\mathbf{z}) = \exp \big [ f_{\delta} (\mathbf{z}) - \varphi(\mathbf{z}) \big ].
$$
Note that both $u_{\delta}$ is integrable since $f$ is bounded by assumption.

Then, for any $\mathbf{x}, \mathbf{y} \in \mathbb{R}^n$, letting $\mathbf{z} = (\mathbf{x} + \mathbf{y}) / 2$, by definition of $f_{\delta}$ we can get
$$
f_{\delta} (\mathbf{z}) \geq \psi_{\delta} \left ( \mathbf{z}, \frac{\mathbf{x} - \mathbf{y}}{2} \right) = \delta f(\mathbf{x}) - \frac{1}{2} \varphi(\mathbf{x}) - \frac{1}{2} \varphi(\mathbf{y}) + \varphi(\mathbf{z}),
$$

which implies that
$$
\begin{align*}
w_{\delta} (\mathbf{z})
= \exp \big [ f_{\delta} (\mathbf{z}) - \varphi(\mathbf{z}) \big ]
\geq \exp \left [ \delta f(\mathbf{x}) - \frac{1}{2} \varphi(\mathbf{x}) - \frac{1}{2} \varphi(\mathbf{y}) \right ]
= u_{\delta} (\mathbf{x})^{1/2} v_{\delta} (\mathbf{y})^{1/2}.
\end{align*}
$$
Therefore, by Prékopa-Leindler inequality, we have
$$
\begin{equation}
\mathbb{E}_{\mu} \big ( \mathrm{e}^{f_\delta} \big ) =
\int w_{\delta} (\mathbf{z}) \mathrm{d} \mathbf{z} 
\geq \left ( \int u_{\delta} (\mathbf{x}) \mathrm{d} \mathbf{x} \right )^{1/2} \left ( \int v_{\delta} (\mathbf{y}) \mathrm{d} \mathbf{y} \right )^{1/2} 
= \mathbb{E}_{\mu}^{1/2} \big ( \mathrm{e}^{2 \delta f} \big ).
\end{equation}
$$

---

Again, by uniformly boundedness of $|f|$, $\lVert \nabla f \rVert_2$ and $\lVert \mathbf{H}_\varphi^{-1} \rVert_{\mathrm{op}}$, we can conclude from (&&&&) that $f_{\delta} = O(\delta)$. Hence,
$$
\mathrm{e}^{f_\delta}
= 1 + f_{\delta} + \frac{1}{2} f_{\delta}^2 + o(\delta^2)
= 1 + \delta f + \frac{\delta^2}{2} \left \langle \nabla f, \mathbf{H}_\varphi^{-1} \nabla f \right \rangle + \frac{\delta^2}{2} f^2 + o(\delta^2).
$$
It follows that
$$
\mathbb{E}_{\mu} \big ( \mathrm{e}^{f_\delta} \big )
= 1 + \delta \mathbb{E}_{\mu} ( f ) + \frac{\delta^2}{2} \mathbb{E}_\mu \left \langle \nabla f, \mathbf{H}_\varphi^{-1} \nabla f \right \rangle + \frac{\delta^2}{2} \mathbb{E}_{\mu} ( f^2 ) + o(\delta^2),
$$
and thus
$$
\begin{equation}
\mathbb{E}_{\mu}^2 \big ( \mathrm{e}^{f_\delta} \big )
= 1 + \delta^2 \mathbb{E}_{\mu}^2 ( f ) + 2 \delta \mathbb{E}_{\mu} ( f ) + \delta^2 \mathbb{E}_\mu \left \langle \nabla f, \mathbf{H}_\varphi^{-1} \nabla f \right \rangle + \delta^2 \mathbb{E}_{\mu} ( f^2 ) + o(\delta^2).
\end{equation}
$$

On the other hand, by uniformly boundedness of $|f|$, we have $2 \delta f = O(\delta)$ and thus
$$
\mathrm{e}^{2 \delta f} = 1 + 2 \delta f + 2 \delta^2 f^2 + o(\delta^2).
$$
Hence,
$$
\begin{equation}
\mathbb{E}_{\mu} \big ( \mathrm{e}^{2 \delta f} \big ) 
= 1 + 2 \delta \mathbb{E}_{\mu} (f) + 2 \delta^2 \mathbb{E}_{\mu} (f^2) + o(\delta^2)
\end{equation}
$$

Substituting (&&&&) and (&&&&) into (&&&&), we get
$$
\mathbb{E}_\mu \left \langle \nabla f, \mathbf{H}_\varphi^{-1} \nabla f \right \rangle 
\geq \mathbb{E}_{\mu} (f^2) - \mathbb{E}_{\mu}^2 ( f ) + o(\delta^2)
= \operatorname{Var}_{\mu} (f) + o(1),
$$
from which the Brascamp–Lieb inequality easily follows as $\delta \downarrow 0$.



