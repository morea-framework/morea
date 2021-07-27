---
layout: default
title: Modules
---
{% include breadcrumb-2.html %}

<div class="container">
  <h1>Modules</h1>
  
  {% if site.morea_overview_modules %}
    {{ site.morea_overview_modules.content | markdownify }}
  {% endif %}
  
  <div class="row">
     {% for module in site.morea_module_pages %}
        <div class="col-md-6 col-lg-4" style="padding-bottom: 20px">
          <div class="card h-100">
            <div class="text-center">
              <img alt="{{module.title}}" src="{{ site.baseurl }}{{ module.morea_icon_url }}" class="card-img-top rounded-circle" style="max-width: 100px; padding-top: 2px">
            </div>
            <div class="card-body">
              <h3 class="card-title">{{ forloop.index }}. {{ module.title }}</h3>
              {{ module.morea_summary | markdownify }}
              <p>
              {% for label in module.morea_labels %}
                <span class="badge">{{ label }}</span>
              {% endfor %}
              </p>
            </div>
            {% if module.morea_coming_soon %}
              <div class="card-footer text-center">
                <span class="btn btn-primary disabled">Coming soon...</span>
              </div>
            {% else %}
                <a href="{{ module.morea_id }}" class="stretched-link"></a>
            {% endif %}
          </div>
        </div>
     {% endfor %}
  </div>
</div>


