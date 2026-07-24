---
layout: page
permalink: /photos/
title: photos
description: a few photos.
nav: true
nav_order: 3
---

<!-- _pages/photos.md -->
<!-- Photos and their order are defined in _data/photos.yml (sorted newest-first). -->

{% assign photos = site.data.photos | sort: "date" | reverse %}
{% for photo in photos %}
  {% assign col = forloop.index0 | modulo: 3 %}
  {% if col == 0 %}<div class="row mt-3">{% endif %}
    <div class="col-sm-4 mt-3 mt-md-0">
      {% include figure.liquid loading="eager" path=photo.image class="img-fluid rounded z-depth-1" zoomable=true caption=photo.caption max-height="350px" %}
    </div>
  {% if col == 2 or forloop.last %}</div>{% endif %}
{% endfor %}
