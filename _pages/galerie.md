---
title: Galerie photo
permalink: photo.html
layout: page
---

## Galerie photo

{% assign image_files = site.static_files | where: "image", true %}
{% for myimage in image_files %}
  <img src="{{ site.baseurl }}{{ myimage.path }}">
{% endfor %}




{% for image in site.static_files %}
  {% if image.path contains 'assets/images/gallery-1' %}
    <img src="{{ image.path }}" alt="">
  {% endif %}
{% endfor %}
