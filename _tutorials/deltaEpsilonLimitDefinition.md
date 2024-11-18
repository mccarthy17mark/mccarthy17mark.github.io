---
title: Delta-Epsilon Limit Definition
layout: tutorial
pageId: deltaEpsilonLimitDefinition
parentId: math
usemathjax: true
---

{% include toc.html %}

### Definition

The main way to rigourously define the limit is using what's called the $\delta - \epsilon$ definition. It reads as follows:

Suppose, for any $\epsilon > 0$ there exists a $\delta > 0$ such that for all the values of $x$ statisfying the following

$$ 0 < |x - c| < \delta $$ 

then the following is also satisfied

$$ 0 < |f(x) - L| < \epsilon $$

If that supposition is true we define the following:

$$ \lim_{x\to c} f(x) = L $$

There is one more restriction that's really just for the math nerds... $f(x)$ must be defined on some interval around $c$ but not necessarily including $c$ itself.

That's a bunch of quacky math lingo. In real words the idea is the following. If this limit exists in the form we know and love, then that means that as $x$ is moved arbitrarily close to $c$ from either direction, then $f(x)$ is defined and will become arbitrarily close to $L$.

So how can we use this definition to make statements about what is and is not a limit? On a typical assignment in an early university calculus course, one might be asked to show whether or not a limit is valid or not.

To achieve this, we typically follow the same steps:
1. See how $\delta$ is defined in terms of $x$ and $c$ for this problem
1. Use the restriction on $\epsilon$ to find a restriction on $\delta$ in terms of $\epsilon$
1. Use the new restriction from the previous step in our definition of $\delta$ to show that our restriction on $\epsilon$ is still valid

### Linear example

That was another confusing list of sentences, so let's show this in practice using a linear example. Show that the following is true:

$$ f(x)=mx+b $$

$$ \lim_{x->c} f(x) = mc+b $$

We begin by looking at what our definition of $\delta$ looks like for this problem:

$$ 0 < |x - c| < \delta $$

Let's recreate that in terms of our restriction on $\epsilon$:

$$ 0 < |f(x) - L| < \epsilon $$

$$ 0 < |mx+b - (mc+b)| < \epsilon $$

$$ 0 < |m (x - c)| < \epsilon $$

$$ 0 < |m| |x - c| < \epsilon $$

$$ 0 < |x - c| < \frac{\epsilon}{|m|} $$

We now have an inequality that looks very similar to our original restriction for $\delta$. We proceed to pick a suitable value for $\delta$ that is in terms of our $\epsilon$ and show that this value will work regardless of the $\epsilon$ chosen and therefore the limit is actually a limit.

$$ 0 < |x - c| < \delta = \frac{\epsilon}{|m|} $$

$$ 0 < |m| |x - c| < \epsilon $$

$$ 0 < |mx+b - (mc+b)| < \epsilon $$

$$ 0 < |f(x) - L| < \epsilon \Rightarrow \lim_{x->c} f(x) = mc+b \hspace{1cm} \blacksquare $$

### Linear Counter-Example

Sometimes it's more instructive to see how things can go wrong rather than only seeing when they work out. Let's do an example where we have provided the incorrect value for the limit and see if we can prove that it does not satisfy the $\delta - \epsilon$ definition.

$$ \lim_{x->2} 3x+4 = 1 $$ 

Begin with reminding ourselves of the form $\delta$ needs to take.

$$ 0 < |x - 2| < \delta $$

Now let's try to recreate that with $\epsilon$.

$$ 0 < |f(x) - L| < \epsilon $$

$$ 0 < |3x+4 - 1| < \epsilon $$

$$ 0 < 3|x+1| < \epsilon $$

$$ -\epsilon < 3(x+1) < \epsilon $$

$$ \frac{-\epsilon}{3} - 3 < x-2 < \frac{\epsilon}{3} - 3 $$

Now look closely at what is happening to the right-most side:

$$ 0 < \epsilon \leq 9 \rightarrow \frac{\epsilon}{3} - 3 \leq 0 $$

$$ \rightarrow x-2 \leq 0 $$

Now remember that we needed to find some $\delta$ that would restrict our $x$ values with a formula like this: 

$$ 0 < |x - 2| < \delta $$

and yet we're finding we need to restrict our $x$ in a way that cannot be satisfied by this equation. There is no value for $\delta$ that will make this work, and therefore we cannot say that this is the correct limit.

$$ \lim_{x->2} 3x+4 \neq 1 $$ 

### $\delta - \epsilon$ Beyond Linear Problems

Once we start dealing with more complicated functions, this proof can become much more complicated. I could go through more examples, but some earnest googling will likely do the trick as well.

The real deal is that we need to become aware of a few more techniques to deal with most functions. One common problem is that a large $\epsilon$ can cause us to pick a bad $\delta$ if we're not careful. To solve this, our $\delta$ has to be restricted to be the minimum of two values, one dependent on $\epsilon$ and one that's just some arbitrary small number. Ultimately limits really only matter *locally*, not *globally*... we only care about the behaviour of $f(x)$ arbitrarily close to $c$, not anywhere else.

A common technique which we almost always have to employ is to break up the absolute value in our inequality like so:

$$ 0 < |x| < a $$

$$ -a < x < a , \hspace{1cm} a > 0$$

### Limits Involving Infinity

The $\delta - \epsilon$ definition needs some slight tweaking when infinity is involved. There's two situations that need handling:

1. The limit evaluates to $L = \pm \infty$
1. The limit is evaluated at $x = \pm \infty$

For both of these situations our solution is to replace the offending idea with saying that it is larger than any arbitrarily large finite integer. If you give me some outrageously large value that you want my $f(x)$ to surpass (or if you want my $f(x)$ to be within some outrageously small range of the limit), then I can choose some outrageously large number that restricts $x$ (or an outrageously small range about $c$ to restrict $x$) so that your condition is satisfied for all the remaining values of $x$.

This is what this looks like in more technical language for the positive infinities:

Suppose, for any $N$ there exists a $M$ such that for all the values of $x$ statisfying the following

$$ x > M $$ 

then the following is also satisfied

$$ f(x) > N $$

If that supposition is true we define the following:

$$ \lim_{x\to \infty} f(x) = \infty $$

Using this definition at negative infinity simply requires exchanging some $>$ symbols for $<$ symbols.
