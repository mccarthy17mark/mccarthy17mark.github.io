---
title: Technology
layout: page_no_title
pageId: tech
parentId: tutorialHome
---

{% for page in site.pages %}
{% if page.title == "Tutorials" %}
{% assign tutorial = page %}
{% endif %}
{% endfor %}

#### Return to [{{ tutorial.title }}]({{tutorial.url}})

<!--
{% for tutorial in site.tutorials %}
{% if tutorial.pageId == page.parentId %}
### Return to [{{ tutorial.title }}]({{tutorial.url}})
{% endif %}
{% endfor %}
-->

## The following technologies and tools have tutorials:

{% for tutorial in site.tutorials %}
{% if page.pageId == tutorial.parentId %}
### [{{ tutorial.title }}]({{tutorial.url}})
{% endif %}
{% endfor %}

