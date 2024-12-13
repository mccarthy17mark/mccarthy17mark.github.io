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
