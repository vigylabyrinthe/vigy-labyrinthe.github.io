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
