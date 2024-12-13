---
title: Lagrange Multipliers
layout: tutorial
pageId: lagrangeMultipliers
parentId: math
usemathjax: true
---

{% include toc.html %}

# The Core Idea

For optimization problems in general, we typically want to use the gradient (or derivative in the 1-D case) to find our extrema. The key idea is that the extrema only occur at the critical points, where the following is true:

$$ \nabla f(\vec{x}) = 0 $$

What do we do when we have some restriction on our possible $\vec{x}$ values? In general, such a restriction could be written as:

$$ g(\vec{x}) = k $$

One path we could take is to reparameterize our variables in some way that takes into account this restriction. For example, if we're constrained to find solutions that exist on some circle, it'd make sense to rewrite the problem in terms of our angle along that circle instead of our typical euclidean coordinates. In general, this can be a lot of work and can cause trouble if we're not careful.

The method of Lagrange multipliers allows us to avoid any reparameterization, and instead adds more equations to solve. 

# The Procedure

To find the maximum of $f(\vec{x})$ if given $i$ different constraining functions $g_i(\vec{x})=k_i$ where $k_i \in \mathbb{R}$, solve the system of equations:

$$ \nabla f(\vec{x}) &= \sum_i \lambda_i \nabla g_i(\vec{x}) $$

$$ g_i(\vec{x})=k_i $$

The set of solutions to this system of equations will describe the possible extrema we're looking for.

The first equation is a vector equation, so in reality we have as many equations as the rank of $\vec{x}$, plus an additional equation for each constraint. We are solving for an equal number of variables as equations: each of the elements of $\vec{x}$, along with each of the **Lagrange multipliers** $\lambda_i$. 

Typically we're not interested in the values of the Lagrange multipliers, but they can still be found exactly since they fully constrain the system of equations.

Of course, if there is no extrema, or if the functions are particularly bizarre, we should expect some nonsense in return. This method won't necessarily warn you if your functions aren't behaving as expected.

# The Understanding

Having a set of equations including our condition functions and solving seems very intuitive, but the source of our first set of equations (the ones with the gradients $\nabla$) is not clear at first.

The key idea is that at the extreme points lying on the constraints $g(\vec{x})$, the change in $f(\vec{x})$ along the path of $g(\vec{x})$ is zero. This should align well with our understanding of finding extrema in one-dimensional functions by setting the first derivative to zero.

The main difference between our 1-D case and this one, is that we imagine that if we could leave our constraint then we'd likely find even more extreme values of $f(\vec{x})$. In other words, the gradient $\nabla f(\vec{x})$ must lie perpendicular to the path of $g(\vec{x})$... if there were any parallel component then we could find more extreme values by travelling in that direction (or away from that direction in the case of minimization).

If we want to know which directions are perpendicular to $g(\vec{x})$, then we can either have memorized that this is precisely what the gradient calculates, or we can reason it out. Recall that we're defining $ g(\vec{x})=k $, the function is constant along its path. The gradient finds the direction of greatest change. This must be the perpendicular direction.

# Examples

<details class="exampleBox">
<summary>
Find the extrema of $f(x,y)=xy$ where $1=x^2+y^2$
</summary>
<hr>
Let's start with a function that we are already going to know the answer to. Here, we're constrained to the unit circle. Clearly the maxima are going to be at $(\frac{1}{\sqrt{2}}, \frac{1}{\sqrt{2}})$ and $(-\frac{1}{\sqrt{2}}, -\frac{1}{\sqrt{2}})$, whereas the minima will be the same two points in the other two quadrants. Let's see if our Lagrange multipliers will five us the same answer.

Our constraint is already in the needed form:

$$ g(x,y) = x^2+y^2 $$

First let's find our gradients:

$$ \nabla f(x,y) = \begin{bmatrix} y || x \end{bmatrix} $$

$$ \nabla g(x,y) = \begin{bmatrix} 2x || 2y \end{bmatrix} $$

Now let's write our system of equations:

$$ y = \lambda 2x $$

$$ x = \lambda 2y $$

$$ x^2+y^2 = 1 $$

To solve this, we can start by isolating $\lambda$ using the first equation:

$$ \lambda = \frac{y}{2x} $$

Plugging that into the second equation:

$$ x = \frac{y}{2x} 2y $$

and rearranging:

$$ x^2 = y^2 $$

Using the third equation, we get the expected result:

$$ 2x^2 = 1 $$

$$ x = \pm \frac{1/\sqrt{2}} $$

A similar process can be followed for $y$ to get the same result. This method gives us four points for $(x,y)$ thanks to the $\pm$ signs. We can easily evaluate them in $f(x,y)$ to check which are maxima and which are minima.
</details>

<details class="exampleBox">
<summary>
Find the extrema of $f(x,y)=x^2y$ where $4=x^2+y^2$
</summary>
<hr>
Our system of equations looks like:

$$ \nabla f(\vec{x}) = \sum_i \lambda_i \nabla g_i(\vec{x}) $$

$$ g_i(\vec{x})=k_i $$

Here there is just one constraint $g$,

$$ g(x,y) = x^2+y^2 = 4 $$

Our gradients are:

$$ \nabla f(x,y) = \begin{bmatrix} 2xy || x^2 \end{bmatrix} $$

$$ \nabla g(x,y) = \begin{bmatrix} 2x || 2y \end{bmatrix} $$

Our system of equations, rewritten for the problem, becomes:

$$ 2xy = \lambda 2x $$

$$ x^2 = \lambda 2y $$

$$ x^2+y^2 = 4 $$

We need to solve these for $x$ and $y$ (and maybe also $\lambda$). Our first equation can be rewritten as:

$$ \lambda = y $$

which then allows our second equation to be rewritten as:

$$ x^2 = (y) 2y $$

$$ x^2 = 2y^2 $$

And plugging this result into our constraint equation, we obtain:

$$ \frac{3}{2}x^2 = 4 \to x = \pm \frac{2}{3}\sqrt{6}$$

$$ 3y^2 = 4 \to y = \pm \frac{2}{3}\sqrt{3}$$

This gives us four values to check:

$$ f( \frac{2}{3}\sqrt{6}, \frac{2}{3}\sqrt{3}) = \frac{8}{3} = 2.67 $$

$$ f( -\frac{2}{3}\sqrt{6}, \frac{2}{3}\sqrt{3}) = \frac{8}{3} = 2.67 $$

$$ f( \frac{2}{3}\sqrt{6}, -\frac{2}{3}\sqrt{3}) = -\frac{8}{3} = -2.67 $$

$$ f( -\frac{2}{3}\sqrt{6}, -\frac{2}{3}\sqrt{3}) = -\frac{8}{3} = -2.67 $$

This gives us our two maxima, and two minima.
</details>
