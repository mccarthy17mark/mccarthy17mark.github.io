---
title: Polynomials
layout: page_no_title
pageId: polynomials
parentId: elementaryFunctions
usemathjax: true
---

{% for tutorial in site.tutorials %}
{% if tutorial.pageId == page.parentId %}
### Return to [{{ tutorial.title }}]({{tutorial.url}})
{% endif %}
{% endfor %}

# {{page.title}}

{% for tutorial in site.tutorials %}
{% if page.pageId == tutorial.parentId %}
### [{{ tutorial.title }}]({{tutorial.url}})
{% endif %}
{% endfor %}

Polynomials are functions that have the following form:

$$ f(x) = \sum_{i=0}^{N} a_{i} x^{i} $$

In words, we are adding up different powers of x, weighted by various constants $a_{i}$ which are often zero, and where the powers are always positive integers or zero.

The largest $i$ for which the corresponding $a_{i}$ is not zero is called the **degree**.

<details>
<summary>Examples of polynomials</summary>
<blockquote>
Lines are polynomials of degree 1 typically written as:
$$ y = m x + b $$
for example,
$$ y = 7 x - 6 $$

Parabolas are polynomials of degree 2:
$$ f(x) = 3x^2 + 2x + 1$$

The following are all polynomials:
$$ f(x) = x^7 $$
$$ f(x) = -13x^3 + \pi x $$

Although usually a bad example, constants are also technically polynomials of degree zero:
$$ f(x) = 12 $$
</blockquote>
</details>

Quite commonly the most useful thing to do with a polynomial is to factor it. This means putting it in the form:

$$ f(x) = \prod_{i=0}^{N} (x - b_{i}) $$

This is not always possible to do while keeping the $b_{i}$ real, quite often imaginary roots are needed. It is also difficult to do this analytically in all situations for any degree larger than 2. This challenge is the reason why the quadratic formula exists. While there exists a cubic and quartic formula, these are very cumbersome, and there is no general formula beyond the 4th degree.

There is a lot to be said about polynomials, but not much has meaning without context.

See also, partial fractions, quadratic formula, polynomial long division, rational root theorem, probably others
