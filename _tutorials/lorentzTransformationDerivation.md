---
title: Derivation of the Lorentz Transformation
layout: tutorial
pageId: lorentzTransformationDerivation
parentId: physics
usemathjax: true

published: false
---

{% include toc.html %}

### Problem Statement

The Lorentz transformation is an essential pillar of special relativity. The transformation is meant to take events $\boldsymbol{x}$ in reference frames $S$ and describe them in reference frame $S'$ as the event $\boldsymbol{x'}$ where $S'$ is moving at a speed $v$ relative to $S$. Events are represented by a vector with four elements $\boldsymbol{x}=<t,x,y,z>$, although later we'll find it more useful to use a scaled version $\boldsymbol{x}=<ct,x,y,z>$ instead.

### Simplification

Starting from nothing, this is currently a very general transformation. We can't say much about it without making assumptions. It should be clear from the start that this transformation is a function (each coordinate in $S$ transforms to only one value in $S'$). This function obviously ought to depend on what we're transforming, but also on $v$, and on the particulars of our coordinate systems $S$ and $S'$. 

$$ \boldsymbol{x'} = f(\boldsymbol{x}, v, S, S') $$

We can simplify this further. When $v=0$ then we're now dealing with more simple transformations: rotations, translations, and technically reflections (but why would anyone want a reflection?). We already know how to do those, so without any loss of generality we can specify our frames somewhat.

Let us say $S'$ is moving at speed $v$ along the $+x$ direction relative to $S$, that all the unit vectors are aligned if $v=0$, and that at $t=0$ the origins of the frames are on top of one another. This way we can perform our Lorentz transformation and handle any rotations and translations later between co-moving frames. With these specifications, we can simplify our function:

$$ \boldsymbol{x'} = f(\boldsymbol{x}, v) $$

We also expect our transformation to be invertible with a speed of $-v$:




