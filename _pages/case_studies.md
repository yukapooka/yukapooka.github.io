---
layout: page
title: case studies
permalink: /case_studies/
description: 
nav: true
nav_order: 3
display_categories: [systems_and_platforms, decision_environments, risk_and_execution]
horizontal: true
---

<!-- pages/[case_studies].md -->
<div class="case_studies">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized case_studies -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_case_studies = site.case_studies | where: "category", category %}
  {% assign sorted_case_studies = categorized_case_studies | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_case_studies %}
      {% include case_studies_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_case_studies %}
      {% include case_studies.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display case_studies without categories -->

{% assign sorted_case_studies = site.case_studies | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_case_studies %}
      {% include case_studies_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_case_studies %}
      {% include case_studies.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
