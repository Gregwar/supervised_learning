---
marp: true
title: "Optimization"
theme: uncover
paginate: true
header: "Optimization"
footer: "Grégoire Passault"
style: :root { font-size: 1.5em; }
---

<style>
@import 'bootstrap/css/bootstrap.min.css';
@import 'style.css';
</style>

# Optimization - Netwon's method
### Grégoire Passault

---

<!-- header: "Newton's method" -->
# Newton's method

---

## Newton's method

Previously, we see how to solve linear systems of equations (exactly, or approximately).

**Problem**: How to solve $f(x) = 0$, for any function $f$?

---

## Newton's method

<center>
<img src="imgs/newton_0.svg" width="600" />
</center>

Here is an example of a non-linear function $f(x)$.

---

## Newton's method

<center>
<img src="imgs/newton_1.svg" width="600" />
</center>

First, we select an initial guess $x_0$.

---

## Newton's method

<center>
<img src="imgs/newton_2.svg" width="600" />
</center>

We compute $y_0$ = $f(x_0)$.

---

## Newton's method

<center>
<img src="imgs/newton_3.svg" width="600" />
</center>

We can then approximate $f(x)$ by its tangent at $x_0$.

---

## Newton's method

<center>
<img src="imgs/newton_4.svg" width="600" />
</center>

We can then solve for the approximation.

---

## Newton's method

<center>
<img src="imgs/newton_5.svg" width="600" />
</center>

And start again with the new initial guess.

---

## Newton's method

<center>
<img src="imgs/newton_6.svg" width="600" />
</center>

And start again with the new initial guess.

---

## Newton's method

<center>
<img src="imgs/newton_7.svg" width="600" />
</center>

And start again with the new initial guess.

---

## Newton's method: algorithm

The algorithm can then be summarized as follows:

1. Select an initial guess $x_0$.
2. Compute $y_0 = f(x_0)$.
3. Compute the tangent at $x_0$.
4. Solve for the approximation $x_1 = x_0 - f'(x_0) y_0$.
5. Start again with the new initial guess $x_1$, until convergence.

---

## A simple example

Let's consider the function $f(x) = x^2 + x - 2$.

<div class="alert alert-primary mt-2">

⚙️ Apply 5 steps of Newton's method to find a root of $f(x)$.
Try different initial guesses $x_0 = -5$ and $x_0 = 5$.

</div>

---

## A simple example

Here are the intermediate expected steps, using $x_0 = -5$:

<center>
<img src="imgs/newton_1.gif" width="600" />
</center>

---

## A simple example

Here are the intermediate expected steps, using $x_0 = 5$:

<center>
<img src="imgs/newton_2.gif" width="600" />
</center>

---

<!-- header: "Multi dimensional case" -->
# Multi dimensional case

---

## Gradient

Suppose we have a function $f: \mathbb{R}^n \to \mathbb{R}$.

Let's take for example a function of two variables $x = \begin{bmatrix} x^{(1)} \\ x^{(2)} \end{bmatrix}$.

In that case, the linear approximation becomes:

$$
f(x)
\approx
f(x_0)
+
\frac{df}{dx^{(1)}} \Delta x^{(1)}
+
\frac{df}{dy^{(2)}} \Delta x^{(2)}
$$

---

## Gradient

In matrix form:

$$
f(x)
\approx
f(x_0)
+
\underbrace{
\begin{bmatrix}
\frac{df}{dx^{(1)}} &&
\frac{df}{dy^{(2)}}
\end{bmatrix}
}_{\nabla f^T}
\begin{bmatrix}
\Delta x^{(1)} \\
\Delta y^{(2)}
\end{bmatrix}
$$

We call $\nabla f$ the **gradient** of $f$.

---

## Jacobian

If we now have $f: \mathbb{R}^n \to \mathbb{R}^m$, the exact same approximation will
apply for every rows of $f$.

For example, for $f: \mathbb{R}^2 \to \mathbb{R}^2$, we have:

$$
f(x)
\approx
f(x_0)
+
\underbrace{
\begin{bmatrix}
\frac{df^{(1)}}{dx^{(1)}} && \frac{df^{(1)}}{dy^{(2)}} \\
\frac{df^{(2)}}{dx^{(1)}} && \frac{df^{(2)}}{dy^{(2)}}
\end{bmatrix}
}_J
\begin{bmatrix}
\Delta x^{(1)} \\
\Delta y^{(2)}
\end{bmatrix}
$$

$J$ is called the **Jacobian** of $f$. We can also write $J = \frac{\partial f}{\partial x}$.

---

<!-- header: "Application on the RR robot" -->
# Application on the RR robot

---

## RR robot

Remember the RR robot model:

<center>
<img src="imgs/rr_simple.svg" width="600" />
</center>