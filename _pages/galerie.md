---
title: Galerie photo
permalink: photo.html
layout: page
---

{% for image in site.static_files %}
  {% if image.path contains 'public/galery' %}
    <img src="{{ image.path }}" alt="">
  {% endif %}
{% endfor %}
