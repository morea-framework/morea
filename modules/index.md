---
layout: default
title: Modules
---

<div class="container">
  <nav aria-label="breadcrumb">
    <ol class="breadcrumb">
      {% if site.morea_head_breadcrumb_link %}
        <li class="breadcrumb-item"><a href="{{ site.morea_head_breadcrumb_link }}">{{ site.morea_head_breadcrumb_label }}</a></li>
      {% endif %}
      <li class="breadcrumb-item" aria-current="page"><a href="{{ site.baseurl }}/">Home</a></li>
      <li class="breadcrumb-item active" aria-current="page">{{ page.title }}</li>
    </ol>
  </nav>
</div>

<div class="container">
  <h1>Modules <small>Topics covered in this class.</small></h1>
  
  {% if site.morea_overview_modules %}
    {{ site.morea_overview_modules.content | markdownify }}
  {% endif %}
  
  <div class="row">
     {% for module in site.morea_module_pages %}
        <div class="col-sm-3">
        {% if module.morea_coming_soon %}
          <div class="card">
            <img src="{{ site.baseurl }}{{ module.morea_icon_url }}" width="100" class="card-img-top  img-circle img-responsive">
            <div class="card-body">
              <h3 class="card-title">{{ forloop.index }}. {{ module.title }}</h3>
              {{ module.morea_summary | markdownify }}
              <p>
              {% for label in module.morea_labels %}
                <span class="badge">{{ label }}</span>
              {% endfor %}
              </p>
              <p class="text-center"><b>Coming soon...</b></p>
            </div>
          </div>
        {% else %}
          <a href= "{{ module.morea_id }}" class="card h-100">
            <img src="{{ site.baseurl }}{{ module.morea_icon_url }}" width="100" class="card-img-top img-circle img-responsive">
            <div class="card-body">
              <h3 class="card-title">{{ forloop.index }}. {{ module.title }}</h3>
              {{ module.morea_summary | markdownify }}
              <p>
              {% for label in module.morea_labels %}
                <span class="badge">{{ label }}</span>
              {% endfor %}
              </p>
              
            </div>
          </a>
        {% endif %}
        </div>
         

     {% endfor %}
  </div>
</div>


