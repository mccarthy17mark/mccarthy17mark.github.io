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

In a pseudo-mathematical sense, we're trying to understand the following relation:

$$ x \in S \leftrightarrow x' \in S' $$

### The Two Assumptions of Special Relativity

To arrive at the Lorentz transformation, we have to make two assumptions:

* Physics works the same in every inertial reference frame. This means looking in different directions, translating to distant locations, and moving at a constant velocity in a new direction should not change anything about how objects behave. In fancier words, we say the laws of physics has both homogeniety and isotropy.
* The speed of light, $c$, is constant regardless of reference frame.

The first is a fairly obvious, but ultimately philosophical assumption. The idea is that there's a spatial and temporal symmetry about the universe. Why would any one time or place be special? Since there's nothing to break this symmetry then everywhere and everytime must have the same laws of physics.

The second assumption is a much more modern idea. Maxwell's equations provide us with a speed of light, but implies that all reference frames see that same speed of light *no matter what*. This led to all sorts of notions about a *luminiferous ether*, which was largely another way of saying that there was one special reference frame, but this notion was disproven.

Turns out these assumptions cause no trouble, so long as you lose the assumption that there is a universal time across all reference frames. If you're okay with different observers experiencing time at different rates, and disagreeing over the order in which events happen, then you can have these two assumptions simultaneously.

One final note: you might be curious why such basic assumptions lead to the Lorentz Transformation and special relativity, and not to the more accurate general relativity. The issue is that we've restricted ourselves to inertial reference frames only, no accelerating or rotating frames allowed. There is another implicit assumption that our reference frames do not depend on the content they're describing. The problem is that all mass-energy causes gravity, which is indistinguishable from a form of acceleration, and therefore any reference frame with *stuff* in it becomes a non-inertial reference frame. The special relativity model really only begins breaking down when masses become incredibly large however. For particles in an accelerator, or rockets in space, the main two regions where we expect speeds close to that of light, the effects of gravity and the flaws in our model are negligible.

### Simplification

Starting from nothing, this is currently a very general transformation. We can't say much about it without making assumptions. It should be clear from the start that this transformation is a function (each coordinate in $S$ transforms to only one value in $S'$). This function obviously ought to depend on what we're transforming, but also on $v$, and on the particulars of our coordinate systems $S$ and $S'$. 

$$ \boldsymbol{x'} = f(\boldsymbol{x}, v, S, S') $$

We can simplify this further. When $v=0$ then we're now dealing with more simple transformations: rotations, translations, and technically reflections (but why would anyone want a reflection?). We already know how to do those, so without any loss of generality we can specify our frames somewhat.

Let us say $S'$ is moving at speed $v$ along the $+x$ direction relative to $S$, that all the unit vectors are aligned if $v=0$, and that at $t=0$ the origins of the frames are on top of one another. This way we can perform our Lorentz transformation and handle any rotations and translations later between co-moving frames. With these specifications, we can simplify our function:

$$ \boldsymbol{x'} = f(\boldsymbol{x}, v) $$

We also expect our transformation to be invertible with a speed of $v_{S,S'} = -v_{S',S} = -v$, making this a one-to-one relation:

$$ \boldsymbol{x} = f(\boldsymbol{x'}, -v) $$

### The Transformation is Linear

The next steps are to play with the setup of our reference frames, and to show this is must be a linear transformation.

Firstly, the units we use to measure our system shouldn't affect the physics observed. Changing units is mathematically equivalent to multiplication by a constant; eg. changing from seconds to minutes is a multiplication of all time values by $1/60$. Our assumption is that changing units then changing reference frames should be the same as changing reference frames and then changing units. Mathematically it looks like this:

$$ f(c\boldsymbol{x}) = cf(\boldsymbol{x}) , c \in \mathbb{R}$$

Next, we argue that the origin of our reference frame should be independent of the physics we describe. Note that since we're dealing with four dimensions, the origin is both spatial and temporal. So if we transform to a moving reference frame then say "I wonder how this looks like to someone long, long ago in a galaxy far, far away", we should arrive at the same result as if someone long, long ago in a galaxy far, far away actually wanted to transform this in a new, moving reference frame. In math:

$$ f(\boldsymbol{x}+\boldsymbol{x_{0}}) = f(\boldsymbol{x}) + f(\boldsymbol{x_{0}}), x_{0} \in \mathbb{R}^4 $$

These two equations are the conditions for our transformation $f$ to be linear. This means we can now describe our transformation as a matrix:

$$ \boldsymbol{x'} = \begin{bmatrix} t' \\ x' \\ y' \\ z' \end{bmatrix} = \begin{bmatrix} a_{1,1} & a_{1,2} & a_{1,3} & a_{1,4} \\ a_{2,1} & a_{2,2} & a_{2,3} & a_{2,4} \\ a_{3,1} & a_{3,2} & a_{3,3} & a_{3,4} \\ a_{4,1} & a_{4,2} & a_{4,3} & a_{4,4} \end{bmatrix}  \begin{bmatrix} t \\ x \\ y \\ z \end{bmatrix} = \boldsymbol{A} \boldsymbol{x} $$

where every $a_{i,j}$ is potentially a function of $v$. If we can resolve these 16 elements, we're done!

### Symmetry arguments




