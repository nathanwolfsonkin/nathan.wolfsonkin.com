---
title: Blog
nav:
  order: 3
---

# Blog

{% comment %}
{% include search-box.html %}
{% include tags.html tags=site.tags %}
{% endcomment %}

{% include search-info.html %}

{% include list.html data="posts" component="post-excerpt" %}