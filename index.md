---
layout: default
title: Home
---

<div class="container">
  <nav aria-label="breadcrumb">
    <ol class="breadcrumb">
      {% if site.morea_head_breadcrumb_link %}
        <li class="breadcrumb-item"><a href="{{ site.morea_head_breadcrumb_link }}">{{ site.morea_head_breadcrumb_label }}</a></li>
      {% endif %}
      <li class="breadcrumb-item active" aria-current="page">{{ page.title }}</li>
    </ol>
  </nav>
</div>

<div class="container">
  {% if site.morea_home_page %}
    {{ site.morea_home_page.content | markdownify }}
  {% else %}
    No home page content supplied.
  {% endif %}
</div>

