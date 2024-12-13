---
title: Essential Kinematics
layout: tutorial
pageId: essentialKinematics
parentId: physics
usemathjax: true

published: false
---

{% include toc.html %}

# The level of this overview

This tutorial should cover everything you'd see in a first year undergrad course. As one dives deeper into physics, we see alternative methods of calculating and understanding kinematics, but this approach is usually how we begin. The assumption is that the basics of calculus is known.

# Galilean Relativity

# Time

There is a lot to be said about how physicists like to handle time. 

# Position

We denote position with a variety of terms. It's important to note that position is a vector quantity, so three variables are needed to fully describe it. I've seen $(x, y, z)$, $\vec{d}$, $\vec{r}$, and a few others. The most common and sensible option, and the one I'll use is the following:

$$ \vec{x} = \begin{bmatrix}x_{0} \\\ x_{1} \\\ x_{2} \end{bmatrix} = x_{0}\hat{i} + x_{1}\hat{j} + x_{2}\hat{k}$$

Of course this is a representation for a cartesian coordinate system; it looks different with other systems, but that discussion belongs elsewhere.

Position alone doesn't mean much, we need to build up our vocabulary of concepts to start making interesting conclusions.

# Displacement & Distance

These two concepts are differing ways that we use to compare two different positions. These positions could represent anything. For example: the position of two different objects, the positions of either end of the same object, or the position of the same object at different moments in time.

**Displacement** refers to the difference between those positions. This remains a vector quantity, and is trivially easy to calculate:

$$ \vec{x_{A/B}} = \vec{x_{A}} - \vec{x_{B}} $$

$$ = (x_{A0} - x_{B0})\hat{i} + (x_{A1} - x_{B1})\hat{j} + (x_{A2} - x_{B2})\hat{k}$$

We would refer to this as the displacement of $A$ relative to $B$. It's worth pointing out that even our position vector $\vec{x}$ is actually a form of displacement... it's relative to the origin point $O = \vec{0}$. In fact, every time we write a vector without saying what it is relative to, we're implying that it's relative to the origin of the reference frame. A tutorial on relativity would be a good place to go into a lot more detail on this idea.

**Distance** refers to the magnitude of the displacement vector, and therefore it is a positive (or zero) scalar quantity. To be explicit, the magnitude is implied to be the 2-norm of the vector, reminiscent of Pythagoras' Theorem:

$$ |\vec{x_{A/B}}| = ||\vec{x_{A}} - \vec{x_{B}}|| $$

$$ = \sqrt{(x_{A0} - x_{B0})^{2} + (x_{A1} - x_{B1})^{2} + (x_{A2} - x_{B2})^{2}}$$

In one dimension, this simplifies to only being an absolute value.

# Velocity and Speed

