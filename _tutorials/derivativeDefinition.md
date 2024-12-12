---
title: Introduction to Derivatives
layout: tutorial
pageId: derivativeDefinition
parentId: math
usemathjax: true

published: false
---

{% include toc.html %}

# Derivatives - The Core Idea

The derivative is a tool that tells you how much one thing changes when a second thing changes. There are many different ways to interpret the derivative, each with its own strengths in certain situations.

The derivative refers to sensitivity, one variable is sensitive to another when its derivative is positive. The derivative refers to rates of change, when the second thing is time. The derivative refers to a slope on a graph if you were to plot the two variables against each other. This is a very common and useful concept.

It is also common to see derivatives referred to as the slope of a tangent line at a point. This is true, but I find this is only rarely a helpful fact to know. Usually it's taught because some educator wants to use a graphical derivation for the derivative, but I feel like this misses the key idea. It's not about some coincidental property involving tangent lines, it's about finding out how different quantities are linked.

# Motivation & Core Idea

The most straight-forward way to think about understanding how different variables affect one another might be to think about a ratio between them. For example, the ratio of dimes in my possession to the amount of money in my possession is a pretty important relationship to know:

$$ 1 \ \text{dime} : \$0.10 $$

One way to look at that ratio is that if I *increase* my dimes by 1, then my money *increases* by $0.10. This ratio of changes is the fundamental idea of the derivative. For our dime example, we would write this idea mathematically as:

$$ \frac{d(\text{money})}{d(\text{dimes})} = 0.10 \frac{\$}{\text{dimes}} $$

Technically derivatives for discretized variables like dimes and money ought to be handled with more nuance, but this is the key idea.

**As one quantity changes, how much does another quantity change?**

# Definition

Let's treat this more mathematically. For this relationship between two quantities to make any sense, one must be a function of the other. In mathematical terms, we use $\Delta$ to describe a change in a variable. The ratio of these variables chaning looks like:

$$ \frac{\Delta f(x)}{\Delta x} = \frac{f(x_2)-f(x_1)}{x_2-x_1} $$

This ratio, this dependency of the change of variable upon the change of another is important regardless of how big the change. The most useful way to look at this is to bring $x_2 \to x_1$ and look at an infinitesimal point rather than a finite range. We use $\text{d}$ to describe an infinitesimal change, replacing the $\Delta$'s. 

$$ \frac{df(x)}{dx} = \lim_{x_2 \to x_1} \frac{f(x_2)-f(x_1)}{x_2-x_1} $$

If we reparameterize this, we obtain the most common form of this equation, and the useful. The reparameterization:

$$ x = x_1 \qquad h = x_2-x_1 $$

The original variables in terms of the new ones:

$$ x_1 = x \qquad x_2 = x + h $$

And the final form of our derivative definition

$$ \frac{df(x)}{dx} = \lim_{h \to 0} \frac{f(x+h)-f(x)}{h} $$

<details class="exampleBox">
<summary>
A mostly pointless aside about why this limit is not one-sided
</summary>
<hr>
The keen-eyed might have noticed that we've perhaps assumed $x_2 > x_1$ but we never wrote it down. This is because we don't actually want to assume this, but it's a little more complicated when we think about the general case.

There's an idea that if I want to know about the rate of change at $x=x_1$, and I spend all this time deriving a rate of change involving $h \to 0^+$ then I'm somewhat creating a "right-ward bias" toward a definition of something broad. By allowing $h \to 0^-$ as well, then I'm removing this bias. Our definitions can remain the same, any negative signs created in our infinitesimals should be cancelled by the negative sign created in the opposite inifinitesimal.

This idea that $h \to 0$ is a two-sided limit is important when discussing when a derivative is well-defined, as we'll see in the next section.
</details>

The notation with the d's is called Leibniz notation, and it is very helpful in a lot of ways. There is a popular alternate notation, which I find is mainly only useful because it requires fewer pen-strokes, called the Newtonian notation:

$$ \frac{df(x)}{dx} = f'(x) $$

The new notation is handy when there are many derivatives occuring and we're too lazy to write it all down, but it suffers from not being clear about what we are differentiating with respect to... we have to rely on context.

At this point, most calculus courses will have spent much time talking about secant lines and tangent lines, but I think this is a distraction from the main idea. Most people reading this would have seen tangent line arguments already, and while it has its uses, I feel like it misses the core idea about why derivatives are so important.

# When is a Derivative Defined?

A derivative is defined at a point **whenever the definition is valid at that point**. That is to say, if we can evaluate the definition and get a number out the other end, then no further thinking is required:

$$ \frac{df(x)}{dx} = \lim_{h \to 0} \frac{f(x+h)-f(x)}{h} $$

There are a lot of situations in math where things aren't this straight-forward, so it's a bit surprising when it's such a clean rule.

It's worth discussing what it looks like for a function to be differentiable and to meet this definition. Ideally you'd be able to quickly check these things, in order, and by doing find >99% of non-differentiable functions.

1. $f(x)$ needs to be defined at $x$, but also in the *neighbourhood* around $x$. We want to talk about lines and curves, not points or sets. Endpoints, asymptotes, holes, etc are all easy to see are not differentiable.

1. $f(x)$ needs to be *continuous* at $x$. Jumps and the like are clearly not going to work. Continuity can be verified with the following condition:

$$ \lim_{x \to c^-} f(x) = f(x) = \lim_{x \to c^+} f(x) $$

<ol start="3">
<li> $f(x)$ needs to be *smooth*. No sharp corners, no kinks. In mathematical terms, this means that the derivative must be continuous. It's odd to talk about needing continuity for the derivative while determining the derivative, but let's look again at how the condition for continuity works, except with derivatives instead:

$$ \lim_{x \to c^-} f'(x) = f'(x) = \lim_{x \to c^+} f'(x) $$

The middle expression is the one we're trying to determine if it's possible to calculate, but we can only do so when the left limit is equal to the right limit. A quick glance at a plot of the function can usually tell you whether or not this is likely to work out.

Technically speaking, there are differentiable functions that do not have continuous derivatives, but these functions are pretty wacky and not likely to be seen describing any physical reality. If you need to determine the differentiability of a crazy function like the following, then you are either a mathematician or you have bigger problems:

$$ f(x) = \begin{cases} x^2 \sin(\frac{1}{x}) & x \neq 0 \\ 0 & x=0 \end{cases} $$

</li>
</ol>

# Properties of Derivatives



# !! Everything below should probably move to another Tutorial !!

# Linearity

# Power Rule

# Product Rule

# Quotient Rule

# Chain Rule

# Derivatives of Inverse Functions

# Derivatives of Popular Functions

# Implicit Differentiation

# Logarithmic Differentiation

# Derivatives of Parametric Functions

