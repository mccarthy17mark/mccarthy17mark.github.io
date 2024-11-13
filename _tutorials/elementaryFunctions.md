---
title: Elementary Functions
layout: page_no_title
pageId: elementaryFunctions
parentId: math
usemathjax: true
---

{% for tutorial in site.tutorials %}
{% if tutorial.pageId == page.parentId %}
### Return to [{{ tutorial.title }}]({{tutorial.url}})
{% endif %}
{% endfor %}

# {{page.title}}

The point of these tutorials is to go over all the most basic and most common functions that you see in future math and to demonstrate some identities along with passing along some intuition that we should hold onto forever, along with linking to some complex ideas involving these simple functions.

{% for tutorial in site.tutorials %}
{% if page.pageId == tutorial.parentId %}
### [{{ tutorial.title }}]({{tutorial.url}})
{% endif %}
{% endfor %}

---

I should delete the below stuff: 

[Polynomials](#polynomials)

[Non-integer powers](#nonIntegerPowers)

[Trigonometric functions](#trig)

[Exponentials and logarithms](#exponents)

[Piece-wise](#piece-wise)

[Absolute value](#abs)

<br>



