---
layout: default
title: Readings
---
<div class="breadcrumb-bar">
  <div class="container">
    <ol class="breadcrumb">
        {% if site.morea_head_breadcrumb_link %}
          <li><a href="{{ site.morea_head_breadcrumb_link }}">{{ site.morea_head_breadcrumb_label }}</a></li>
          {% endif %}
      <li><a href="{{ site.baseurl }}/">Home</a></li>
      <li class="active">{{ page.title }}</li>
    </ol>
  </div>
</div>

<div class="container">
  <h1>Readings and other resources <small>in module order</small></h1>
</div>

{% if site.morea_overview_readings %}
<div class="container">
  {{ site.morea_overview_readings.content | markdownify }}
</div>
{% endif %}

{% for module in site.morea_module_pages %}
{% if module.morea_coming_soon != true and module.morea_readings.size > 0 %}
<div class="{% cycle 'section-background-1', 'section-background-2' %}">
  <div class="container">
    <h2><small>Module:</small> <a href="{{ site.baseurl }}{{ module.module_page.url }}">{{ module.title }}</a></h2>

    <div class="row">
    {% for page_id in module.morea_readings %}
      {% assign reading = site.morea_page_table[page_id] %}
       <div class="col-md-6 col-lg-3">
         <div class="card h-100">
           <div class="card-body">
             <a href="{{ reading.morea_url }}" class="card-link"><h4 class="card-title">{{ reading.title }}</h4></a>
             {{ reading.morea_summary | markdownify }}
           </div>
           <div style="border-top-color: transparent" class="card-footer bg-body">
             {% for label in reading.morea_labels %}
               <span class="badge bg-primary">{{ label }}</span>
             {% endfor %}
           </div>
         </div>
       </div>
        {% if forloop.index == 4 %}
          </div><div class="row">
        {% endif %}
        {% if forloop.index == 8 %}
          </div><div class="row">
        {% endif %}
       {% if forloop.index == 12 %}
          </div><div class="row">
        {% endif %}
        {% if forloop.index == 16 %}
          </div><div class="row">
        {% endif %}
    {% endfor %}
    </div>
  </div>
</div>
{% endif %}
{% endfor %}
