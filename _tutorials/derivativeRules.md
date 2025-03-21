---
title: Derivative Rules
layout: tutorial
pageId: derivativeRules
parentId: math
usemathjax: true

published: true
---

{% include toc.html %}

# Linearity

Linearity is a very useful property of many functions and transformations. Thankfully, derivatives being linear will save us all a lot of headaches in the many, many aspects of math that depend on them.

To be linear, a transformation has to obey the following:

$$ \left[ af(x)+bg(x) \right]' = af'(x)+bg'(x) \qquad a,b \in \mathbb{R} $$

Of course we can break this up into two smaller rules involving constants and addition:

$$ [af(x)]' = af'(x) \qquad a \in \mathbb{R} $$

$$ [f(x) + g(x)]' = f'(x)+g'(x) $$

These smaller rules are more commonly shown, but having both simultaneously is something I think very important.

<details class="exampleBox">
<summary>
Proof of linearity of the derivative
</summary>
<hr>

As always, it's good to start with the derivative definition:

$$ \frac{df(x)}{dx} = \lim_{h \to 0} \frac{f(x+h)-f(x)}{h} $$

Now let's plug in our linear set-up and hope it works out the way we'd like:

$$ f(x) = ac(x)+bd(x) $$

$$ \begin{align} \frac{df(x)}{dx} &= \lim_{h \to 0} \frac{[ac(x+h)+bd(x+h)]-[ac(x)-bd(x)]}{h} \\ &= \lim_{h \to 0} \frac{a[c(x+h)-c(x)]+b[d(x+h)-d(x)]}{h} \\ &= a \lim_{h \to 0} \frac{c(x+h)-c(x)}{h} +b\lim_{h \to 0}\frac{d(x+h)-d(x)}{h} \\ &= a c'(x) +b d'(x) \end{align} $$

</details>

# Product Rule

Having conquered addition, we need to tackle the next most important operator, multiplication:

$$ \left[ f(x)g(x) \right]' = f'(x)g(x)+f(x)g'(x) $$

Derivatives of products aren't as simple as they could be, but they are simple enough. Multiplication being as fundamental as it is, causes the product rule to be one of the most important aspects of derivatives. This rule plays an even bigger role once we enter multivariate calculus.

<details class="exampleBox">
<summary>
Proof of the product rule
</summary>
<hr>

As always, it's good to start with the derivative definition:

$$ \frac{df(x)}{dx} = \lim_{h \to 0} \frac{f(x+h)-f(x)}{h} $$

Now let's plug in our product set-up and hope it works out the way we'd like:

$$ f(x) = a(x)b(x) $$

$$ \begin{align} \frac{df(x)}{dx} &= \lim_{h \to 0} \frac{a(x+h)b(x+h)-a(x)b(x)}{h} \\ &= \lim_{h \to 0} \frac{a(x+h)b(x+h)+[a(x+h)b(x)-a(x+h)b(x)]-a(x)b(x)}{h} \\ &= \lim_{h \to 0} \frac{a(x+h)[b(x+h)-b(x)]+b(x)[a(x+h)-a(x)]}{h} \\ &= \lim_{h \to 0}a(x+h) \lim_{h \to 0}\frac{b(x+h)-b(x)}{h}+b(x)\lim_{h \to 0}\frac{a(x+h)-a(x)}{h} \\ &= a(x)b'(x)+b(x)a'(x) \end{align} $$

</details>

# Quotient Rule

I typically just see quotient rule as a special case of product rule. It doesn't come up a lot beyond a first-year calculus course, but it's good to know.

$$ \left[ \frac{f(x)}{g(x)} \right]' = \frac{f'(x)g(x)-f(x)g'(x)}{g(x)^2} $$

<details class="exampleBox">
<summary>
Proof of the quotient rule
</summary>
<hr>
We'll use the power rule, chain rule, and the product rule to help us prove the quotient rule. Don't worry, we won't need this rule to prove the power,  chain, or product rules, so we won't enter any circular definitions!

$$ f(x) = \frac{g(x)}{h(x)} = g(x)h^{-1}(x)$$

$$ \begin{align} \frac{df(x)}{dx} &= g'(x)h^{-1}(x) + (h^{-1}(x))'g(x) \\ &= g'(x)h^{-1}(x) - h^{-2}(x)h'(x)g(x) \\ &= h^{-2}(g'(x)h(x) - h'(x)g(x)) \\ &= \frac{g'(x)h(x) - h'(x)g(x)}{h^2(x)} \end{align} $$

Having the memory of a goldfish, I spent years not having this formula memorized and re-deriving it every time. Thankfully it's a really simple one to put together.
</details>

# Chain Rule

$$ \left[ f(g(x)) \right]' = f'(g(x))g'(x) $$

$$ \frac{df(x)}{dx} = \frac{df(u)}{du} \frac{du(x)}{dx} $$

<details class="exampleBox">
<summary>
Proof of the chain rule
</summary>
<hr>

As always, it's good to start with the derivative definition:

$$ \frac{df(x)}{dx} = \lim_{h \to 0} \frac{f(x+h)-f(x)}{h} $$

Now let's plug in our function. Let's first show a proof that works if and only if $g'(x) \neq 0$:

$$ f(x) = f(g(x)) $$

$$ \begin{align} \frac{df(x)}{dx} &= \lim_{h \to 0} \frac{f(g(x+h))-f(g(x))}{h} \\ &= \lim_{h \to 0} \frac{f(g(x+h))-f(g(x))}{h}\frac{g(x+h)-g(x)}{g(x+h)-g(x)} \end{align} $$

Adding this new factor only works when we don't have a division by zero. It's easy to see that requirement is fulfilled so long as the derivative $g'(x)$ is non-zero at $x$. We'll discuss the implications of this and the zero-derivative case later.

$$ \begin{align} &= \lim_{h \to 0} \frac{f(g(x+h))-f(g(x))}{g(x+h)-g(x)}\lim_{h \to 0}\frac{g(x+h)-g(x)}{h} \\ &= \lim_{h \to 0} \frac{f(g(x+h))-f(g(x))}{g(x+h)-g(x)}\lim_{h \to 0}\frac{g(x+h)-g(x)}{h} \\ &= \lim_{h \to 0} \frac{f(g(x+h))-f(g(x))}{g(x+h)-g(x)} \frac{dg(x)}{dx} \end{align} $$

Now our first factor looks close to what we want, but the current form makes the connection a bit obscured. Let's make some substitutions to better show the proof:

$$ g_1 = g(x) \qquad g_2 = g(x+h) $$

$$ h \to 0 \Rightarrow g_2 \to g_1 $$

$$ \lim_{h \to 0} \frac{f(g(x+h))-f(g(x))}{g(x+h)-g(x)} = \lim_{g2 \to g1} \frac{f(g_2)-f(g_1)}{g_2-g_1} $$

This should look pretty familiar, it's a step from when we first derived the derivative! Recall that we made the following reparameterization and arrived with our familiar derivative, except we should probably use a different letter than $h$ since we've already used it in this proof:

$$ g = g_1 \qquad H = g_2-g_1 $$

$$ \begin{align} \lim_{g2 \to g1} \frac{f(g_2)-f(g_1)}{g_2-g_1} &= \lim_{H \to 0} \frac{f(g+H)-f(g)}{H} \\ &= \frac{df(g)}{dg} \end{align}$$

Putting it together, we obtain the proof we're looking for:

$$ \begin{align} \frac{df(g(x))}{dx} &=\lim_{h \to 0} \frac{f(g(x+h))-f(g(x))}{g(x+h)-g(x)} g'(x) \\ &= \frac{df(g)}{dg} \frac{dg(x)}{dx} \end{align} $$

Great! Now we just need to deal with the case that $g(x+h)=g(x)$. This is pretty straight forward to do unthinkingly, but it helps a lot to see that $g(x)$ is essentially a constant function, at least locally. It should be easy to see that $\frac{dg}{dx}=0$ as well.

$$ \begin{align} \frac{df(x)}{dx} &= \lim_{h \to 0} \frac{f(g(x+h))-f(g(x))}{h} \\ &= \lim_{h \to 0} \frac{0}{h} \\ &= 0 \\ &= \frac{df(g)}{dg} \frac{dg(x)}{dx} \end{align} $$

Now we've shown all cases lead to the same result!

</details>

# Derivatives of Inverse Functions

This next rule is a lot less commonly used since it mainly applies to derivations creating derivatives of particular functions, and not to applications that involve derivatives. Regardless, it's still handy to know of its existence.

$$ (f^{-1}(x))' = \frac{1}{f'(f^{-1}(x))} $$

We'll use this later to find the derivatives of the inverse trigonometric functions.

<details class="exampleBox">
<summary>
Derivation of inverse derivative formula
</summary>
<hr>
We won't need to go back to the definition of the derivative for this one, instead we mainly need chain rule. The proof is very straight forward, write $x$ in terms of $y$ to remove the inverse function, differentiate, and solve for $y'$.

$$ y = f^{-1}(x) $$

$$ x = f(y) $$

$$ \frac{d}{dx} x = \frac{d}{dx} f(y) $$

$$ 1 = f'(y)y' $$

$$ y' = \frac{1}{f'(y)} $$

$$ (f^{-1}(x))' = \frac{1}{f'(f^{-1}(x))} $$

This derivation is simple enough that the derivation might be easier to remember than the formula!

</details>

# Derivatives of Popular Functions

## Derivative of a Constant

Constants, (functions which do not depend on the value of $x$) are delightfully simple to differentiate. This should be obvious, no matter how you conceptualize the derivative, but it doesn't hurt to write it explicitly for completeness.

$$ c' = 0 $$

<details class="exampleBox">
<summary>
Proof of $ c' = 0 $ using the definition of the derivative
</summary>
<hr>

The definition of the derivative looks like the following:

$$ \frac{df(x)}{dx} = \lim_{h \to 0} \frac{f(x+h)-f(x)}{h} $$

In this case, the function $f(x)$ is simple:

$$ f(x) = c $$

Now let's continue the proof:

$$ \begin{align} \frac{dc}{dx} &= \lim_{h \to 0} \frac{c-c}{h} \\ &= \lim_{h \to 0} \frac{0}{h} \end{align} $$

This is an interesting limit. At $h=0$, we obtain the $\frac{0}{0}$ indeterminate form, and there is no clear way to simplify this. However, let's think about what is happening in the neighbourhood of $h=0$. Clearly, this function evaluates to zero all throughout the region, with the only exception being at $h=0$. If we remember our $\delta-\epsilon$ definition of the limit, or even just the general properties of limits, we recall that the behaviour in the neighbourhood around $h=0$ is all that matters, and therefore we can confidently state the following:

$$ \begin{align} \frac{dc}{dx} &= \lim_{h \to 0} \frac{0}{h} \\ &= 0 \end{align} $$

</details>

## Power rule

The power rule essentially allows us to take derivatives of all polynomials, along with all sorts of functions with negative exponents, non-integer exponents, or both.

$$ \left[ x^a \right]' = ax^{a-1} \qquad \text{if} a\neq 0, a \in \mathbb{R} $$

Note there are a lot of extremely common functions, all of which are just special cases of power rule:

$$ x' = 1(x^(1-1)) = 1 $$

$$ \left[\frac{1}{x}\right]' = [x^{-1}]' = -x^{-2} = -\frac{1}{x^2} $$

$$ \left[\sqrt{x}\right]' = \left[x^{\frac{1}{2}}\right]' = \frac{1}{2} x^{-\frac{1}{2}} = \frac{1}{2\sqrt{x}} $$

## Other functions

The following derivatives are worth memorizing, as they are all important elementary functions, and their derivatives are not straight-forward to prove:

$$ [e^x]' = e^x $$

$$ [\ln(x)]' = \frac{1}{x} $$

$$ [\sin(x)]' = \cos(x) $$

$$ [\cos(x)]' = \sin(x) $$

There are some more complicated functions that are still very common whose derivatives are worth mentioning:

$$ [\tan(x)]' = \sec^2(x) = \frac{1}{\cos^2(x)} $$

$$ [\sin^{-1}(x)]' = \frac{1}{\sqrt{1-x^2}} $$

$$ [\cos^{-1}(x)]' = -\frac{1}{\sqrt{1-x^2}} $$

$$ [\tan^{-1}(x)]' = \frac{1}{1+x^2} $$

$$ [\sinh(x)]' = \cosh(x) $$

$$ [\cosh(x)]' = \sinh(x) $$

There is a class of function that rarely appears, whose derivative is not worth memorizing, but is worth knowing how to derive. The most important idea is that both power rule and treating these functions like exponentials are incorrect approaches. These functions need logarithmic differentiation:

$$ \left[f(x)^{g(x)}\right]' = f(x)^{g(x)} \left[g'(x)\ln(f(x)) + \frac{g(x)f'(x)}{f(x)}\right] $$

<details class="exampleBox">
<summary>
Proof
</summary>
<hr>

$$ \begin{align} y &= f(x)^{g(x)} \\ \ln(y) &= g(x)\ln(f(x)) \\ [\ln(y)]' &= [g(x)\ln(f(x))]' \\ \frac{y'}{y} &= g'(x)\ln(f(x)) + \frac{g(x)f'(x)}{f(x)} \\ y' &= f(x)^{g(x)} \left[g'(x)\ln(f(x)) + \frac{g(x)f'(x)}{f(x)}\right] \end{align} $$

</details>

