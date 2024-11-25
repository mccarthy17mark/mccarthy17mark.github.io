---
title: Integration by Parts
layout: tutorial
pageId: integrationByParts
parentId: math
usemathjax: true
---

{% include toc.html %}

### Derivation

Integration by parts is a way to rewrite some integrals in terms of a way which often makes them simpler to resolve. It's an extension of the product rule:

$$ f(x) = u(x)v(x) = uv $$

$$ \frac{df(x)}{dx} = u\frac{dv}{dx} + v\frac{du}{dx} $$

$$ \int \frac{df(x)}{dx} dx= \int \left[u\frac{dv}{dx} + v\frac{du}{dx}\right] dx $$

$$ f(x) = \int u\frac{dv}{dx} dx + \int v\frac{du}{dx} dx $$

$$ uv = \int udv + \int vdu $$

$$ \int udv = uv - \int vdu $$

The formula extends in a very reasonable way for definite integrals, where $a$ and $b$ are the limits in terms of $x$ specifically:

$$ \int_{a}^{b} udv =  uv \bigg\rvert_{a}^{b} - \int_{a}^{b} vdu $$

<br>

### Typical usage

What's the point of this formula? As with most integration tools, it's a technique which is only useful in certain situations, and identifying those situations has more to do with pattern recognition than anything else. Since it doesn't directly reduce the number of integrals we need to solve, we usually reach for this tool when integration by substitution will not suffice. Typically integration by parts comes in handy when there is an integrand with an easily differentiatable portion multiplied by an easily integrable portion. We let $u$ represent something that gets simpler with differentiation, and $dv$ be something that doesn't get more complicated.

Some examples are below:

<details class="exampleBox">
<summary>
$$ \int xe^{x} dx $$
</summary>
<hr>
This integrand is unable to be solved by substitution, so we look to integration by parts. We see that there is a polynomial portion $x$ that will become simpler with differentiation, and an exponential portion $e^{x}$ that does not become more complicated with integration. This lets us easily choose our $u$ and $dv$:

$$ u = x \hspace{1cm} dv = e^{x}dx $$

$$ du = dx \hspace{1cm} v = e^{x} $$

Note that even though we did an indefinite integral to acquire $v$ from $dv$, it's not worth bothering with an integration constant since our final formula still contains an indefinite integral.

Now we can just plug into our formula and simplify, introducing an integration constant when all the indefinite integrals have been resolved:

$$ \int xe^{x} dx = xe^{x} - \int e^{x} dx $$

$$ = xe^{x} - e^{x} + C $$ 

$$ = (x-1)e^{x} + C $$

</details>

<details class="exampleBox">
<summary>
$$ \int x^{2}\cos(x) dx $$
</summary>
<hr>
Our choice of $u$ and $dv$ should be pretty straight-forward, except for one reservation: the polynomial portion becomes simpler with differentiation but does not disappear. Often integration by parts forces us to repeatedly use it to get a polynomial to give up and differentiate itself away.

$$ u = x^{2} \hspace{1cm} dv = \cos(x)dx $$

$$ du = 2xdx \hspace{1cm} v = \sin(x) $$

$$ \int x^{2}\cos(x) dx = x^{2}\sin(x) - \int 2x\sin(x)dx $$

$$ u = x \hspace{1cm} dv = \sin(x)dx $$

$$ du = dx \hspace{1cm} v = -\cos(x) $$

$$ \int x^{2}\cos(x) dx = x^{2}\sin(x) - 2\left[-x\cos(x) - \int -\cos(x)dx\right] $$

$$ = x^{2}\sin(x) + 2x\cos(x) - 2\sin(x) + C $$

</details>

Sometimes the choice of $u$ and $v$ are less obvious. It often requires a bit of foresight about how the substitutions will affect the new integrand. Sometimes there isn't even a pair of functions being multiplied and we have to rely on good guess-work (or memory of similar problems).

<details class="exampleBox">
<summary>
$$ \int ln(x) dx $$
</summary>
<hr>
This feels like it should be something elementary, like it was forgotten from our standard formulae, but it's actually quite a strange integral. Noticing that integration by parts is the best method is especially difficult here unless you've seen it done before.

$$ u = ln(x) \hspace{1cm} dv = dx $$

$$ du = frac{1}{x} dx \hspace{1cm} v = x $$

$$ \int ln(x) dx = xln(x) - \int x \frac{1}{x} dx $$

$$ = xln(x) - \int dx $$

$$ = xln(x) - x + C $$

$$ = x(ln(x) - 1) + C $$

</details>

There is another way to resolve an integral for integration by parts which comes up fairly rarely. It happens when the new integral winds up identical to the old integral. Then treating the integral like a variable allows us to isolate it and find its solution.

<details class="exampleBox">
<summary>
$$ \int \sin(x)e^{x} dx $$
</summary>
<hr>
This integral actually allows us to pick either the trigonometric factor or the exponential factor for both $u$ and $dv$. The result is ultimately the same.

$$ u = \sin(x) \hspace{1cm} dv = e^{x} dx $$

$$ du = \cos(x) dx \hspace{1cm} v = e^{x} $$

$$ \int \sin(x)e^{x} dx = \sin(x)e^{x} - \int e^{x}\cos(x)dx $$

$$ u = \cos(x) \hspace{1cm} dv = e^{x} dx $$

$$ du = -\sin(x) dx \hspace{1cm} v = e^{x} $$

$$ \int \sin(x)e^{x} dx = \sin(x)e^{x} - \left[\cos(x)e^{x} - \int e^{x}(-\sin(x))dx\right] $$

$$ \int \sin(x)e^{x} dx = e^{x}(\sin(x) - \cos(x)) - \int \sin(x)e^{x}dx $$

$$ 2\int \sin(x)e^{x} dx = e^{x}(\sin(x) - \cos(x)) $$

$$ \int \sin(x)e^{x} dx = \frac{e^{x}(\sin(x) - \cos(x))}{2} $$

</details>

Integration by parts is fairly powerful as it helps us resolve a large number of integrals. It also shows up frequently in proofs and derivations of more complex theorems, especially in physics. It's can be very handy to become familiar with this technique as it keeps showing up in unexpected places for a long time.
