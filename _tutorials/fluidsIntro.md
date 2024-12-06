---
title: Introduction to Fluids
layout: tutorial
pageId: fluidsIntro
parentId: physics
usemathjax: true

published: false
---

{% include toc.html %}

# Fluids - the main idea

When we first learn physics, we typically deal with singular small objects moving under everyday conditions. The concepts that we learn are concepts that apply to *particles*, objects with some mass but negligible size. By restricting ourselves to rotation-free systems, assuming all objects are infinitely rigid and all forces pass through the centre of mass, then this works quite well for a large variety of common situations.

A fluid model typically assumes a fluid is an immense (but finite) number of particles, and we want to describe behaviours of the system as a whole, ignoring any individual particle. Particles are considered to be infinitely small, so they do not rotate, they do not deform, and many other complicating factors do not exist for them. We often will ask what a single particle might do if placed somewhere within the fluid, this is how we define things like the fluid's speed and path, for example. We are also concerned with bulk properties like pressure, density, viscosity, temperature, etc.

It is helpful to differentiate fluid mechanics into two smaller concepts:

1. Fluid Statics - The system does not have any direct time dependence. In other words, if you checked the system today and checked again tomorrow, you'd describe it in the same way. The fluid can still have a velocity, as this is an indirect time dependence, but how we describe that velocity cannot be a function of time. This makes our math much, much easier, but it also greatly restricts what sorts of systems we can talk about.
2. Fluid Dynamics - The system has no assumptions about how it depends on time. This is the general case. Without simplifying factors, this leads to Navier-Stokes equations and problems that can only be approximated by expensive computers.

Regarding the fluids themselves, it is helpful to split them into two main categories, as this can change much about our approach:

- Incompressible Fluids - The density of these fluids remains the same in most situations, and the volume is a simple quantity to describe. Water is the prototypical example of an incompressible fluid
- Compressible Fluids - Everything else. Air is the prototypical example.

# Continuity Equations

A very common situation is one where our fluid is neither created nor destroyed within our system, but simply flows in and out. This usually can be seen as an obvious consequence of the conservation of mass. We describe this idea of fluid conservation with continuity equations.

The most useful and simplest version of this would be for water flowing through a pipe. Let's say this pipe has an entrance and an exit, with cross-sectional areas $A_{in}$ and $A_{out}, and uniform fluid velocities at the entrance and exit as $v_{in}$ and $v_{out}$ respectively. In reality, viscosity and pipe friction lead to non-uniform fluid velocities, but let's ignore that for now. We begin by arguing that the total mass of the water within the system (some section of the pipe) is constant.

$$ m(t) =  m_{water in pipe} +  \frac {dm_{in}}{dt} t -  \frac {dm_{out}}{dt} t  $$

$$ \frac{d}{dt} m = 0 = \frac {dm_{in}}{dt} -  \frac {dm_{out}}{dt} $$

Note that this time derivative of mass is usually seen as a mass flow rate, or mass flux, or something of that sort.

Using the definition of density $\rho$ over a volume $V$: $\rho = \frac{m}{V} $

$$ \frac {d(\rho V_{in})}{dt} -  \frac {d(\rho V_{out})}{dt} = 0 $$

Since water is incompressible, the density $\rho$ is constant and can be divided out of the equation completely. We can imagine the volume of fluid entering during $dt$ has a cross-sectional area $A_{in}$ and a thickness of $dx_{in}$

$$ \frac { d(A_{in}x_{in})}{dt} -  \frac{d(A_{out}x_{out})}{dt} = 0 $$

$$ A_{in}\frac { dx_{in}}{dt} -  A_{out}\frac{dx_{out}}{dt} = 0 $$

$$ A_{in}v_{in} -  A_{out}v_{out} = 0 $$

There were a lot of assumptions to get us to this result, but it's so commonly useful that it's worth memorizing. We can use this equation to help us understand the fluid flow through a pipe 

With some vector calculus we can make some more general versions of the same statement, removing a lot of these assumptions, which is both good and bad.




# bouyancy & archimedes

# What is Pressure

## pressure is energy density

## surfaces have zero gauge pressure

## pascal's principle? Does anyone care about that?

# mgh ~ rho gh

# Bernoulli's principle

# viscosity = friction

# boundary layers?

# Reynold's transport theorem and everything afterward is probably the next tutorial
