---
title: Derivation of the Wave Equation
layout: tutorial
pageId: waveEquationDerivation
parentId: physics
usemathjax: true

published: false
---

{% include toc.html %}

# Wave Equation

The wave equation looks like this:

$$ c_1 \frac{d^2}{dx^2} f(x,t) = c_2 \frac{d^2}{dt^2} f(x,t) $$

The solutions to this equation look like this:

$$ f(x,t) = A \e^{\sqrt{c_2}x+\sqrt{c_1}t} $$

where $c_1$ and $c_2$ are complex numbers or something?

Solutions also ought to look like this:

$$ f(x,t) = A\cos(\sqrt{c_2}x+\sqrt{c_1}t)+B\sin(\sqrt{c_2}c_1x+\sqrt{c_1}t) $$

or something similar.

In higher dimensions, it looks like this:

$$ \gradient^2 f(\vec{x},t) = c^2 \frac{d^2}{dt^2} f(\vec{x},t) $$

# Wave equation in a string, rope, or cable

Let's see that this applies in non-compressible, non-elastic, flexible material, like strings etc.

insert picture here

!(like this)[/path/to/assets]

Let's get some constraints here if we can. Firstly, the motion in the direction of the rope is zero, it is non-compressible and non-elastic. All motion must be perpendicular to the rope.

