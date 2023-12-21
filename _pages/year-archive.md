---
title: "Pages"
permalink: /year-archive/
layout: posts
author_profile: true
---

{% for page in site.pages %}
  {% unless page.hidden %}
    {% include archive-single.html %}
  {% endunless %}
{% endfor %}

Good page
[Kenny Yip Coding](https://www.kennyyipcoding.com/)