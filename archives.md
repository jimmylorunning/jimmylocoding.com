---
layout: page
title: Archives 
---

## Blog Posts

{% for post in site.posts %}
  {% if post.draft != true %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
  {% endif %}
{% endfor %}
