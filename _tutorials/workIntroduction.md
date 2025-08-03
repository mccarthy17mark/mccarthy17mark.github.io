---
title: Work Introdution
layout: tutorial
pageId: workIntroductoin
parentId: physics
usemathjax: true
---

{% include toc.html %}

# The key idea

Work is the concept that relates forces and energy. We define it by asking what happens to an object as a force is applied to that object. In general, the following path integral is our most helpful definition:

$$ \delta W = \vec{F} \cdot d\vec{s} $$
$$ W = \int_C \vec{F} \cdot d\vec{s} $$
This simplifies neatly in the case of constant forces for motion in straight lines as:

$$ W = \vec{F}\cdot\vec{x} $$

While this might seem like an arbitrary construction, it is a very important one as this leads to the work-energy principle:

$$ \Delta E_k = \Sigma W $$

Thus work becomes the bridge between forces and energy.

# Work Energy Principle derivation

$$ W = \int_C \vec{F} \cdot d\vec{s} $$

$$ = \int_{t_1}^{t_2} \vec{F}\cdot\frac{d\vec{s}}{dt}dt $$

$$ = \int_{t_1}^{t_2} \vec{F}\cdot \vec{v} dt $$

$$ = \int_{t_1}^{t_2} m\vec{a}\cdot \vec{v} dt $$

$$ = \int_{t_1}^{t_2} m\frac{d\vec{v}}{dt}\cdot \vec{v} dt $$

$$ = \int_{t_1}^{t_2} \frac{m}{2}\left(\frac{d\vec{v}}{dt}\cdot \vec{v}+\vec{v}\cdot\frac{d\vec{v}}{dt}\right)dt $$

$$ = \int_{t_1}^{t_2} \frac{m}{2}\frac{d(\vec{v}\cdot\vec{v})}{dt}dt $$

$$ = \int_{t_1}^{t_2} \frac{m}{2}\frac{dv^2}{dt}dt $$

$$ = \frac{1}{2}mv^2 \Big|_{t_1}^{t_2} $$

$$ = \Delta E_k $$

Here we get the all important work-energy principle:

$$ W = \Delta{E_k} $$

But also an important alternative formulation for work:

$$ W=\int_{t_1}^{t_2} \vec{F}\cdot \vec{v} dt $$

Which is handy when discussing power:

$$ P=\frac{dW}{dt}=\vec{F}\cdot\vec{v} $$

# Work intuition

The physics definition of work does not correlate well with the everyday definition of work, much to the frustration of every early physics student. The dot product is a significant reason for that.

Take the following situations for example

- Lifting a heavy object means applying a positive amount of work to that object. 
- Carrying that object around without changing elevation does no work. 
- Lowering the heavy object does negative work. 
- Applying a large amount of force for a long time on an object that does not move also does no work. 

Of these situations, only the first corresponds with our everyday notion of work, and negative work feels especially counterintuitive.

To be explicit about it:

- The everyday defintion of work is along the lines of actions that make you more tired
- The physics definition of work is about how much a force on an object is collinear with the object’s motion.

It’s important to remember that these are two different things

# Constraint Forces do no work

The main idea here is that if there exists some force that constrains the motion of an object to some *static* region in space, then such a force cannot do any work.

The normal force is a common example of this. In the frame of reference of the earth, the normal forces which keep objects from falling into the ground are all incapable of doing work.

The reason for this is that for movement perpendicular to these forces, no work is done by definition, and the movement in a parallel direction is either stopped by such a force or the force vanishes to zero. Ie: an object cannot enter the ground as the opposing normal force rises as needed to prevent movement, and when the object is lifted and no longer contacts the ground, the normal force disappears.

We find similar situations for objects sliding to a wire, sliding along a surface, encountering a barrier, etc.

For non-static regions with constraint forces, we do not find this result… something like the normal force of an elevator floor can still do work as the elevator moves up or down.
