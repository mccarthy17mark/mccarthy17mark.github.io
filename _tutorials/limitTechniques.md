---
title: Limit Techniques
layout: tutorial
pageId: limitTechniques
parentId: math
usemathjax: true
---

{% include toc.html %}

### Vibe Check

The first step to any math problem ought to be a vibe check. Is there anything weird about the function? Is the problem well-defined? Does this problem give off any "vibes" which remind us of anything in particular?

When limits are concerned, we particularly want to be careful near the "interesting regions" of a function. Things like divisions by zero, or transitions between definitions of a piece-wise function, or asymptotes of a tangent function, or logarithms of values at or below zero, or square roots of negative numbers, or... All of these kinds of situations should give us signals that the problem we want to solve might require more thought than a simple algorithmic response.

### Substitution

The vast majority of the time, the following is true:

$$ \lim_{x \to c} f(x) = f(c) $$

This is actually a definition of continuity, which is a property most useful functions possess. If your "vibe check" rings no alarms and this substitution provides a reasonable answer, then perhaps the limit truly is this easy to evaluate.

The real danger is in **not** performing this check. Quite often we search for more complicated tools when simple tools will suffice!

<details class="exampleBox">
<summary>

$$ \lim_{x \to \pi} \frac{\sin{x}}{x} $$

</summary>
<hr>
This function gives off some stinky vibes near zero, but not at $x=\pi$! Since the function ought to be continuous in this region, let's just try substituting our value directly

$$ \lim_{x \to \pi} \frac{\sin{x}}{x} = \frac{\sin{\pi}}{\pi} $$

$$ = \frac{0}{\pi} $$

$$ = 0 $$

Sometimes it really is that easy. Aren't you happy we didn't jump straight to doing a Taylor expansion?

</details>

### Indeterminate Forms

When dealing with limits we often encounter one of the seven indeterminate forms. These are mathematical constructions that often were derived from something reasonable but have no meaning. Whenever we encounter one of these, it means we must try another technique to get the answer.

The indeterminate forms are as follows:

$$ \frac{0}{0},\  \frac{\infty}{\infty},\  \infty - \infty,\  0^{0},\  0^{\infty},\  \infty^{0},\  1^{\infty}$$

although typically we encounter the first three. There are methods to convert each type of indeterminate form into all the others, which will be helpful when we introducte l'H&#244;pital's Rule later.

### Cancellation

A very frequent problem is when we have to take a limit of the following:

$$ \lim_{x \to c} \frac{f(x)}{g(x)},\quad f(c)=g(c)=0 $$

Direct substitution results in $\frac{0}{0}$ which is one of our indeterminate forms. Although $f$ and $g$ could be any function, let's focus on the case where they are both polynomials first.

If a polynomial $f(c)=0$, then we call $c$ a *root* and we know that $(x-c)$ is a factor of that polynomial. Since this factor is common to both $f$ and $g$, then we can guarantee that a cancellation is possible. Factoring a polynomial is a long reviled practice by many high school students and there are many ways to do it, but since we already know the values of the root, we can definitively say that polynomial long division **always** works!

<details class="exampleBox">
<summary>

$$ \lim_{x \to 1} \frac{x^{2} - 1}{x^{2}+3x-4} $$

</summary>
<hr>
We first attempt simple subsititution, because it's almost always a good idea to check:

$$ \lim_{x \to 1} \frac{x^{2} - 1}{x^{2}+3x-1} = \frac{1^{2} - 1}{1^2+3-4}$$

$$ = \frac{0}{0} $$

As you might expect from the discussion, this leads to our indeterminate form. However, now we know that $x-1$ is a factor in both numerator and denominator and can be cancelled.

$$ = \lim_{x \to 1} \frac{(x+1)(x-1)}{(x+4)(x-1)} $$

$$ = \lim_{x \to 1} \frac{x+1}{x+4} $$

Once the cancellation is complete, we are often (but not always) safe to try subsitution again:

$$ = \frac{1+1}{1+4} $$

$$ = \frac{2}{5} $$

</details>

#### Rationalization

One common type of problem, though I'm not certain why it is stressed so much, involves a technique known as rationalization. We have the same setup as before, except either $f$ or $g$ or both look something like the following:

$$ f(x) = a_{L}\sqrt{f_{L}(x)} \pm a_{R}\sqrt{f_{R}(x)} $$

where the $a$'s are just constants and the $f_{i}$'s are polynomials. This function is still equal to zero, so we can follow the same factoring and cancellation technique as before, except that the procedure to follow is much less obvious now that square roots are involved.

Returning to a polynomial is actually pretty simple. We take advantage ofthe following identity:

$$ a^2 - b^2 = (a+b)(a-b) $$

and multiply $f$ (or $g$ or both) by what we call the *conjugate*:

$$ f^{*}(x) = a_{L}\sqrt{f_{L}(x)} \mp a_{R}\sqrt{f_{R}(x)} $$

$$ ff^{*} =  a_{L}^{2}f_{L}(x) - a_{R}^{2}f_{R}(x) $$

This is the sort of thing that is usually simpler when seen performed in an example.

<details class="exampleBox">
<summary>

$$ \lim_{x \to 1} \frac{\sqrt{x^2+3} - 2\sqrt{x}}{4-2\sqrt{3x^2+1}} $$

</summary>
<hr>

As always, don't forget to try a simple substitution first:

$$ \lim_{x \to 1} \frac{\sqrt{x^2+3} - 2\sqrt{x}}{4-2\sqrt{3x^2+1}} = \frac{\sqrt{1^2+3} - 2\sqrt{1}}{4-2\sqrt{3(1)^2+1}}$$

$$ = \frac{\sqrt{4} - 2}{4-2\sqrt{4}} $$

$$ = \frac{0}{0} $$

Of course that was unlikely to work, but it takes os little effort to check! Now let's try multiplying (and dividing, to not change the value of the function) by the conjugates of both the numerator and denominator.

$$ = \lim_{x \to 1} \frac{\sqrt{x^2+3} - 2\sqrt{x}}{4-2\sqrt{3x^2+1}}\left(\frac{\sqrt{x^2+3} + 2\sqrt{x}}{\sqrt{x^2+3} + 2\sqrt{x}}\right)\left(\frac{4+2\sqrt{3x^2+1}}{4+2\sqrt{3x^2+1}}\right) $$

$$ = \lim_{x \to 1} \frac{x^2+3 - 4x}{16-4(3x^2+1)}\left(\frac{1}{\sqrt{x^2+3} + 2\sqrt{x}}\right)\left(\frac{4+2\sqrt{3x^2+1}}{1}\right) $$

$$ = \lim_{x \to 1} \frac{x^2 - 4x+3}{-12x^2+12}\left(\frac{4+2\sqrt{3x^2+1}}{\sqrt{x^2+3} + 2\sqrt{x}}\right) $$

With some factoring of the newly rationalized factors, our cancellation appears:

$$ = \lim_{x \to 1} \frac{(x-3)(x-1)}{-12(x+1)(x-1)}\left(\frac{4+2\sqrt{3x^2+1}}{\sqrt{x^2+3} + 2\sqrt{x}}\right) $$

$$ = -\frac{1}{12} \lim_{x \to 1} \frac{x-3}{x+1}\left(\frac{4+2\sqrt{3x^2+1}}{\sqrt{x^2+3} + 2\sqrt{x}}\right) $$

And now we substitute to find better fortunes than before:

$$ = -\frac{1}{12} \frac{(1-3)}{(1+1)}\frac{(4+2\sqrt{3(1)^2+1})}{(\sqrt{1^2+3} + 2\sqrt{1})} $$

$$ = -\frac{1}{12} \frac{(-2)}{(2)}\frac{(4+4)}{(2 + 2)} $$

$$ = -\frac{1}{12} (-1)(2) $$

$$ = \frac{1}{6} $$

</details>

This rationalization technique is not limited to square roots, as cube roots have a similar formula. There are other tricks which can extend the lifetime of this technique, but it is ultimately limited in usefulness.

There is a more powerful technique known as l'H&#244;pital's Rule which has fewer restrictions that can also deal with these problems. However l'H&#244;pital's Rule requires the usage of the derivative, and the derivative's definition requires us to resolve limits involving $\frac{0}{0}$, so at least while defining the derivative we ought to use techniques like this.

### Ratios at Infinity

Another common source of indeterminate forms lies at $x=\pm\infty$. We frequently arrive at, or can create, a ratio of two functions and the question becomes which function accelerates towards infinity the fastest. The key insight is typically that the highest degree of $x$ will go to infinity the fastest.

For example, let's assume we have the ratio of two polynomials $f(x)$ and $g(x)$ which have degrees $d_f$ and $d_g$ and leading coefficients $a_f$ and $a_g$ respectively. We can make the following conclusions:

$$ \lim_{x \to \infty} \frac{f(x)}{g(x)} = \text{sgn}\left(\frac{a_f}{a_g}\right)\infty \quad \text{if} \  d_f>d_g $$

$$ \lim_{x \to \infty} \frac{f(x)}{g(x)} = 0 \quad \text{if}\  d_f<d_g $$

$$ \lim_{x \to \infty} \frac{f(x)}{g(x)} = \frac{a_f}{a_g} \quad\text{if} \ d_f=d_g $$

The way I usually like to prove this is by multiplying the limit by:

$$ \frac{\frac{1}{x^d}}{\frac{1}{x^d}} \quad \text{where}\  d=\text{max}(d_f,d_g) $$

<details class="exampleBox">
<summary>

$$ \lim_{x \to \infty}\frac{a_1x^2+b_1x+c_1}{b_2x+c_2} $$

</summary>
<hr>

$$ = \lim_{x \to \infty}\frac{a_1x^2+b_1x+c_1}{b_2x+c_2} \frac{(\frac{1}{x^2})}{(\frac{1}{x^2})} $$

$$ = \lim_{x \to \infty}\frac{a_1+\frac{b_1}{x}+\frac{c_1}{x^2}}{\frac{b_2}{x}+\frac{c_2}{x^2}} $$

$$ = \frac{a_1+0+0}{0+0} $$

At this point it's clear we're approaching a division by zero so it's important to note the signs of the numerator and denominator. Since the leading terms dominate the others, their signs are the only ones that matter.

$$ = \text{sgn}\left(\frac{a_1}{b_2}\right)\infty$$

</details>

<details class="exampleBox">
<summary>

$$ \lim_{x \to \infty}\frac{b_1x+c_1}{a_2x^2+b_2x+c_2} $$

</summary>
<hr>

$$ = \lim_{x \to \infty}\frac{b_1x+c_1}{a_2x^2+b_2x+c_2} \frac{(\frac{1}{x^2})}{(\frac{1}{x^2})} $$

$$ = \lim_{x \to \infty}\frac{\frac{b_1}{x}+\frac{c_1}{x^2}}{a_2+\frac{b_2}{x}+\frac{c_2}{x^2}} $$

$$ = \frac{0+0}{a_2+0+0} $$

$$ = 0 $$

Since the sign of zero means very little, we don't have to bother with keeping track of the signs of the leading coefficients.

</details>

<details class="exampleBox">
<summary>

$$ \lim_{x \to \infty}\frac{a_1x^2+b_1x+c_1}{a_2x^2+b_2x+c_2} $$

</summary>
<hr>

$$ = \lim_{x \to \infty}\frac{a_1x^2+b_1x+c_1}{a_2x^2+b_2x+c_2} \frac{(\frac{1}{x^2})}{(\frac{1}{x^2})} $$

$$ = \lim_{x \to \infty}\frac{a_1+\frac{b_1}{x}+\frac{c_1}{x^2}}{a_2+\frac{b_2}{x}+\frac{c_2}{x^2}} $$

$$ = \frac{a_1+0+0}{a_2+0+0} $$

$$ = \frac{a_1}{a_2} $$

</details>


### L'H&#244;pital's Rule

### Taylor Series Expansions

### Squeeze Theorem

Congratulations, you have stumbled upon one of the gems of interestingly named concepts in math! It's not quite as good as the Hairy Ball Theorem, but we take what we can get.

The main idea behind squeeze theorem is that if a limit is difficult to evaluate, we can occasionally find two other enveloping functions that are simpler to evaluate and provide some constraints. This is especially useful when the two enveloping functions meet and we can deduce the value of the limit without ever tackling it directly.

In mathier terms, let's introduce a function $f(x)$, and two enveloping functions $f_-(x)$ and $f_+(x)$. These functions don't need to envelope over all $x \in \mathbb{R}$, just merely some interval $I$ that contains our limit $x=c$. The squeeze theorem looks like this:

$$ \text{Let} \quad f_-(x)\leq f(x) \leq f_+(x) \quad \forall x \in I $$

$$ \text{If} \quad \lim_{x \to c} f_-(x) = \lim_{x \to c} f_+(x) = L, \ c \in I $$

$$ \text{Then} \quad \lim_{x \to c} f(x) = L $$

The reasoning behind this should be obvious, but despite the simplicity of the idea, there are some limits where this theorem is indispensable.

Very frequently this theorem is used for the trigonometric functions, taking advantage of some version of the following:

$$ -1 \leq \sin(x) \leq 1 $$

$$ -1 \leq \cos(x) \leq 1 $$

<details class="exampleBox">
<summary>

$$ \lim_{x \to \infty} \sin(x)e^{-x} $$

</summary>
<hr>

As always let's try substitution

$$  = \lim_{x \to \infty} \sin(\infty)e^{-\infty} $$

We have two factors to contend with, and the $\sin(\infty)$ factor is poorly defined. It's unclear how we should treat this. A Taylor series expansion of $\sin(\infty)$ will give us the $\infty-\infty$ indeterminate form, and there doesn't appear to be any solution that l'H&#244;pital's rule can provide either.

Still, we might guess at the result based on the following:

$$ -1 \leq \sin(x) \leq 1, \quad \forall x \in \mathbb{R} $$

$$ \lim_{x \to \infty} e^{-\infty} = 0 $$

which implies that we have something between -1 and 1 multiplied by zero, giving us a reasonable guess that the answer is zero.

We can prove this definitively using squeeze theorem. Let's create two enveloping functions:

$$ f(x) = \sin(x)e^{-x} $$

$$ f_-(x) = -e^{-x} $$

$$ f_+(x) = e^{-x} $$

$$ f_-(x)\leq f(x) \leq f_+(x) \quad \forall x \in \mathbb{R} $$

And now we can apply squeeze theorem:

$$ \lim_{x \to \infty} f_-(x) = \lim_{x \to \infty} f_+(x) = 0 $$

$$ \implies \lim_{x \to \infty} f(x) = 0 $$ 

</details>
