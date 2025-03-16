---
title: Work Introdution
layout: tutorial
pageId: workIntroductoin
parentId: physics
usemathjax: true
---

{% include toc.html %}

# The Key Idea
Work is the concept that relates forces and energy. We define it by asking what happens to an object as a force is applied to that object. In general, the following path integral is our most helpful definition:

$$ \delta W = \vec{F} \cdot d\vec{s} $$

$$ W = \int_C \vec{F} \cdot d\vec{s} $$

This simplifies neatly in the case of constant forces for motion in straight lines as:

$$ W = \vec{F}\cdot\vec{x} $$

While this might seem like an arbitrary construction, it is a very important one as this leads to the work-energy principle:

$$ \Delta E_k = \Sigma W $$

Thus work becomes the bridge between forces and energy.

# Work Energy Principle derivation

With a bit of calculus we can show that this definition of work also satisfies the work-energy principle.

$$ W = \int_C \vec{F} \cdot d\vec{s} $$

$$ = \int_{t_1}^{t_2} \vec{F}\cdot\frac{d\vec{s}}{dt}dt $$

$$ = \int_{t_1}^{t_2} \vec{F}\cdot \vec{v} dt $$

$$ = \int_{t_1}^{t_2} m\vec{a}\cdot \vec{v} dt $$

$$ = \int_{t_1}^{t_2} m\frac{d\vec{v}}{dt}\cdot \vec{v} dt $$

$$ = \int_{t_1}^{t_2} \frac{m}{2}\left(\frac{d\vec{v}}{dt}\cdot \vec{v}+\vec{v}\cdot\frac{d\vec{v}}{dt}\right)dt $$

By making use of the product rule, we can create the following:

$$ = \int_{t_1}^{t_2} \frac{m}{2}\frac{d(\vec{v}\cdot\vec{v})}{dt}dt $$

$$ = \int_{t_1}^{t_2} \frac{m}{2}\frac{dv^2}{dt}dt $$

By the fundamental theorem of calculus, we obtain:

$$ = \frac{1}{2}mv^2 \Big|_{t_1}^{t_2} $$

$$ = \Delta E_k $$

# Intuition for Work as a Physics Concept
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
