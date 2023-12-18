---
title: "Pages"
permalink: /year-archive/
layout: posts
author_profile: true
---

{% for post in site.pages %}
  {% unless post.hidden %}
    {% include archive-single.html %}
  {% endunless %}
{% endfor %}